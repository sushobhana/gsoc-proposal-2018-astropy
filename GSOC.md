# GSOC PROPOSAL

- **ORGANISATION**      : OPEN ASTRONOMY
- **SUB-ORGANISATION** : ASTROPY

### 1.  Student Information

- **NAME** : SUSHOBHANA PATRA
- **EMAIL-ID** : sushobhanapatra@gmail.com
- **TIME-ZONE** : UTC+5:30 (IST)
- **CHAT-HANDLE** : [sushobhana@gmail.com](https://hangouts.google.com/) (google hangouts)
- **GITHUB-ID** : [@sushobhana](https://github.com/sushobhana)
- **BLOG** : [@sushobhanapatra](https://medium.com/@sushobhanapatra)
- **RSS FEED** : [feed/@sushobhanapatra](https://medium.com/feed/@sushobhanapatra)
- **LINKS TO PULL REQUESTS** :
    - [ Allow Updating Of Table Using Indices ](https://github.com/astropy/astropy/pull/6831) : Enhancement (Astropy Core)
    - [ Comparing FITS File With One In a Sub-directory ](https://github.com/astropy/astropy/pull/7085) : Bug Fix (Astropy Core)
    - [ Mapped J2000 ](https://github.com/astropy/regions/pull/157) : Bug Fix (Regions)
    - [ fixed `contains` and made centre a 0D skycoord object ](https://github.com/astropy/regions/pull/159)
    - [ added_functions_annulus ](https://github.com/astropy/regions/pull/161)
    - [ docfix ](https://github.com/astropy/regions/pull/164) : a simple doc fix.

#### 2.  Education

| Institute                   | Course              | Graduation Date | Grade/ Percentage |
|:-----------------------------|:---------------------:|:-----------------:|:---------------:|
| NIT Jalandhar               | B.Tech (CSE)        | 2020            | 7.9/10            |
| Sri Chaitanya Techno School | 12th (Intermediate) | 2016            | 95.8%            |
| De Paul School              | 10th (High School)  | 2014            | 93.3%            |


- Programming Experience :

I am a second year undergrad student pursuing computer science at NIT Jalandhar, India. Some of the relevant academic courses
that i have completed are : Computer programming, Object programming, Data Structures And Algorithms, Discrete Mathematics,
Principles Of Programming Languages, Design And Analysis Of Algorithms.

I have learnt general programming skills since high school in Basic, Java. Since the last two years I have been seriously learning about advanced programming techniques
both theoretical and application based , and the technologies surrounding it. I also love taking part in competitive programming.

I am fluent in C, C++, python.Besides that I manage to understand Java, Javascript, bash superficially.I am aware of most of the high-level constructs in python that are not available in c/c++ and am learning to write pythonic code since 5 months.

I am very comfortable with Ubuntu 16.04 as my primary operating system and pycharm as my python IDE.I have already set-up developement installs for astropy core as well as regions package and are well aware of the coding and documentation guidelines.

I am also familiar with git and astropy's workflow along with sphinx-documentation and py-test.

#### 3.  University Information

* University: [National Institute Of Technology, Jalandhar](http://nitj.ac.in)
* Major: Computer Science and Engineering (CSE)
* Current year: 2nd
* Expected Graduation date: June 2020
* Degree: Bachelor of Technology

#### 5.Interest In OpenAstronomy:

While i was a child, I was very curious about how our Universe is created and the purpose of our life. Books like `The Brief History Of Time` and `The Theory Of everything` made my life interesting then and the astrophysicists were no less than superman for me. I dreamt of becoming one of them. But as time passed i became more awared of how computers are influencing every aspects of mankind by their sheer computing powers at lightening speeds, I realized the power of programming. Since, then I have fallen in love with it and decided to major in computer science. Recently, when I was looking to contribute for open source projects having real world applications, i came across the GSoC program and realised how open-source software are helping people of diverse professions. I came across this organisation from their site .The fact I could be a help to an Astronomer tempted me to start contributing in astropy. I was so interested that I learnt (still learning!) python last year just to contribute in this organisation.The community was very welcoming and patient to guide me through my first PR. Since then, I am looking forward to work for astropy under GSoC this summer.

## PROJECT TITLE : CASA CRTF REGION FILE HANDLING

#### 5.  Project Abstract
The regions package in astropy is the successor to pyregions and photoutils package which provides data structures and functionalities to handle astronomical regions.
It aims to provide support for all commonly used region specifications and formats. DS9 region is already implemented. This project aims to add support for CASA CRTF region format. CRTF stands for Casa Region Text Format.
CASA CRTF region file has two different kind of definitions :
- Regions : They will be displayed by visualisations task as well as used to create masks,etc., as appropriate.
- Annotations  : They are used by display tasks, and are used for visual reference only.

Apart from the regular region shapes there are annotations such as line, vector and special symbols  and are not currently supported by regions package.

##### Few of the features that this project aims to do ,

>- Implement new regions/annotations that CRTF supports.(symbols, box, etc..)
>- Implement a parser for reading CRTF region files.
>- Implement a CRTF writer.
>- Implement cube region that CASA supports but currently not present in astropy-regions.
>- Provide the required attributes and functionalities to the existing region/shape classes.
>- Provide documentation to all the features added.
>- Creating a test suite to ensure everything works as expected.

#### DETAILED DESCRIPTION:

#### PART 1:

#####1. Implement 2-D regions :

There are several annotations described in the CRTF region format that are not currently implemented.
    1. Vector : Probably should inherit Line shape.
    2. Text : Probably should inherit point shape with an extra text attribute.
    3. Symbols :this will also inherit point shape with an extra symbol attribute.

   The important thing for the above annotations is to represent them in plots by plotting libraries such as matplotlib through `as_patch` methods.

#####2. Adding missing features to existing region classes :

Currently all the additional parameters describing regions are stored in the `meta` and `visual` attribute.
The CRTF supports a lot of parameters and this might cause problems when stored in a single dictionary
such as there would be several name for a particular key and checking it would become difficult, the values of the keys should be in a particular domain, several file formats can store a key's value
in different way.
Particularly, the channel, frquency, velocity planes of the regions can exist independently and would be unwise to put them under `meta` attribute.
This [ issue ](https://github.com/astropy/regions/issues/162) aims to discuss the several ways to tackle the difficulties by either providing
classes or methods to check the validity of the meta attribute.
Most of the region objects does not check the validity of the attributes and are listed as `#TODOS` in comments.I would ensure that the TODOS are completed and
test cases are covered for that.


#### PART 2 :

#####1. Creating a parser :
The casa CRTF format has a different syntax style than DS9 regions. It is little more complicated to parse due to larger grammar rules than DS9. This also provides a large
set of definitions which has values in a particular domain. The API needs to be made similar to that of the DS9 parser to be user friendly.

>The first task would be to implement parser for
the regions and annotations. The second thing would be to parse the meta data i.e the definitions.

I intend to make the following main classes :
   1. `CRTFParser` : takes a region string and would contain CRTFShapeList which can be ultimately converted to region objects. It would contain several methods such as
   `parse_line` to parse single region and `parse_meta` to parse global parameters, using regular expressions .There would be appropriate attributes storing the resultant meta as well as region list.
   In the process of converting into a CRTFShapeList, there would be help of several helper classes.
        - `CRTFRegionParser` : this class will help turning a line containing regions in CRTF format to CRTFShape object.
        -  `CRTFShape` : this is a class which is used to represent a CRTF region so that it can be easily convertible to a regions object,kind of acts like an intermediate.
        - `CRTFCoordinateParser` : helper class to parse string coordinates and transform into astropy.coordinate objects (mostly `SkyCoord` objects).

   2. `CRTFShapeList` : It is a list of Shape. It would also contain `to_CRTFObject` method to convert into `CRTFObject`.

#####2. Implementing a Writer :
We should be able to convert the regions object into CRTF format strings and write them into files.
The `writeDS9` method directly converts region lists into strings thus formatting the DS9 region file difficult.
To represent CRTF region file we can create a `CRTFObject` and insert further global parameters , comments and tweak regions according to the user which is not possible in for DS9 regions.
The CRTFObject may be represented as list of sentences.(A single sentence represents a single region/annotation).
The plan is to :
    1. convert region list to `CRTFShapeList`.
    2. the `CRTFShapeList`can be converted to `CRTFObject`
    3. the `CRTFObject` can finally be converted to region strings.

   We can add functions that wraps the first and second step.

   We can also `writeCRTF` to convert regions directly to strings.

   The new thing (`CRTFObject`), will be heavily discussed with the community as well mentors and will be implemented if seems necessary.

#### PART 3:

#####1. Implementing 3-D regions :
CRTF right now supports three type of 3-D regions. They are rectangular box, center box, rotated box.
According to the specifications,
    - Rectangular box is defined by two opposite corners.
    - center box is defined by the center point and the length and width of cube.
    - rotated box is the center box with an extra rotang attributes.

All these regions can be represented by sky coordinates or pixel coordinates. it would also have `bounding_box` and `volume` attributes
and would also support `to_mask` for computing overlap masks, `to_sky`, `to_pixel` methods.
Also compound objects for 3-D regions would also be supported.


>Most of the above things are either completely new implementations or enhancements to the existing regions.Therefore each and every needs to be properly documented as well as thoroughly tested according to the
astroby documentation and testing guidelines.This will be done simultaneously while completing each sub-parts.

### Timeline

| Time-Period | Plan                                                            |
| :-----------: | :---------------------------------------------------------------|
|April 23, 2018 to May 14, 2018 (**Community-Bonding**) | <ui><li>**Reading more about CRTF format and going over the casacore codes for regions.**</li><li>**Learn more about the internal architecture of the regions package.**</li><li>Read about the regions, coordinate systems and all other things specifically used in the astronomical community.</li><li>Learn more about creating parsers and find the best way to implement it.</li><li>**Have a thorough understanding of regular expressions and about the `re` module in the python standard library**</li><li>Have a understanding of the matplotlib library.</li><li>**Collecting examples of CRTF region files which would be helpful while creating tests.**</li></ui>|
||**PART 1** |
|May 14, 2018 to May 20, 2018 (Week-1) |<ui><li>**Implement the new 2-D regions**</li><li>Write documentations and tests for it.</li></ui>|
|May 21, 2018 to May 27, 2018 (Week-2) |<ui><li>Solving the  [**issue**](https://github.com/astropy/regions/issues/162) of the way to store all the parameters specified by the CASA CRTF region format.</li></ui>|
||**PART 2**|
|May 28, 2018 to June 3, 2018 (Week-3) |<ui><li>Finalising the design of the parser system.</li><li>**Start creating `CRTFShape` , `CRTFShapeList`, `CRTFCoordinateParser`**.</li></ui>|
|June 4, 2018 to June 10, 2018 (Week-4) |<ui><li>**start writing `CRTFParser` and `CRTFRegionParser` class.**</li><li>complete the parser system to parse regions without metadata.</li></ui>|
|June 11, 2018 to June 17, 2018 (Week-5) (**Evaluation 1**)|<ui><li>Implementation of metadata reading</li><li>**Start writing test-suite for the whole parser system.**</li><li>Documenting the whole parser.</li></ui>|
|June 18, 2018 to June 24, 2018 (Week-6) |<ui><li>**Designing the writing system and start implementing it.**</li></ui>|
|June 25, 2018 to July 1, 2018 (Week-7) |<ui><li>Complete the writing system, if not finished.</li><li>**Start writing tests and make sure that everything works as expected.**</li><li>Documenting the whole writer.</li></ui>|
||**PART 3**
|July 2, 2018 to July 8, 2018 (Week-8) |<ui><li>**Implementing 3-D regions.**</li><li>Writing tests and documenting it.</li></ui>|
|July 9, 2018 to July 15, 2018 (Week-9) (**Evaluation 2**)|<ui><li>Complete the missing functionalities of 3-D regions from the previous week, if any.</li><li>**Implementing compound regions for 3-D regions with documentation and tests.**</li></ui>|
|July 16, 2018 to July 22, 2018 (Week-10) |<ui><li>Implement `as_patch` methods for all the new regions.</li></ui>|
|July 23, 2018 to July 29, 2018 (Week-11) |<ui><li>Completing the `#TODOS` in the existing region classes</li><li>**Strengthening the test suite.**</li></ui>|
|July 30, 2018 to August 5, 2018 (Week-12) |<ui><li>**Buffer Week**</li></ui>|
|August 6, 2018 to August 14, 2018 (Week-13) (**Final Evaluation**)|<ui><li>Make sure that the documentation and the whole  looks good and I achieve everything as said above. </li></ui>|

>- Will make sure that my code is simple , PEP8 compliant, clean and upto the standards that astropy tends to maintain.
>- Will write Documentation Alongside writing code and also make sure that new classes and methods are completely described by doc strings.
>- Will create issues or start discussion threads with my mentor about the work from the previous week.
>- Updating my fork with my recent work daily and creating a pull request at the end of the week.
>- Keep communicating with my mentors about my progress and asking for help when needed.
>- Will write a `blog` about the ongoings so that the comunity is informed about my progress.The posts would be weekly or bi-weekly.

#### 7.  Schedule Availability:

I am aware that GSoC program needs full time availability.Since most of my GSoC time coincides with my summer vacation, I have no problem working seven days of the week. My end-semester examination completes on May 24,2018. Therefore, I will not be able to give my complete time for the fisrt two weeks. To manage this, i will initiate some of the work during the community-bonding period and have allotted minimum work for the first two weeks. I may work extra time during the further weeks to compensate this. In case of any emergencies, i will contact the mentors and try to finish the objectives in the buffer-week.I am willing to invest upto 42hrs/week and more if required.
My primary workstation would be my laptop with i5 processor and 8GB ram.I will be having internet facilities all summer and will also arrange a PC for back-up.
