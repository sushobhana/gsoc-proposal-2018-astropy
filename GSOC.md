# GSOC PROPOSAL

- **ORGANISATION**     : OPEN ASTRONOMY
- **SUB-ORGANISATION** : ASTROPY

#### 1.  Student Information

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
|-----------------------------|---------------------|-----------------|-------------------|
| NIT Jalandhar               | B.Tech (CSE)        | 2020            | 7.9/10            |
| Sri Chaitanya Techno School | 12th (Intermediate) | 2016            | 95.8%            |
| De Paul School              | 10th (High School)  | 2014            | 93.8%            |

    
- Programming Experience :

I am a second year undergrad student pursuing computer science at NIT Jalandhar, India. Some of the relevant academic courses
that i have completed are : Computer programming, Object programming, Data Structures And Algorithms, Discrete Mathematics, 
Principles Of Programming Languages, Design And Analysis Of Algorithms.

I have learnt general programming skills since high school in Basic, Java. Since the last two years I have been seriously learning about advanced programming techniques
both theoretical and application based , and the technologies surrounding it. I also love taking part in competitive programming.
      
I am fluent in C, C++, python.Besides that I manage to understand Java, Javascript, bash superficially.

I am very comfortable with Ubuntu 16.04 as my primary operating system.

#### 3.  University Information
	
* University: [National Institute Of Technology, Jalandhar](http://nitj.ac.in)
* Major: Computer Science and Engineering (CSE) 
* Current year: 2nd
* Expected Graduation date: June 2020
* Degree: Bachelor of Technology
        
#### 5.  Interest In OpenAstronomy:

## PROJECT TITLE : CASA CRTF REGION FILE HANDLING

#### 5.  Project Abstract
The regions package in astropy is the successor to pyregions and photoutils package which provides data structures and functionalities to handle astronomical regions.
It aims to provide support for all commonly used region specifications and formats. DS9 region is already implemented. This project aims to add support for CASA CRTF region format. CRTF stands for Casa Region Text Format.
CASA CRTF region file has two different kind of definitions
- Regions : They will be displayed by visualisations task as well as used to create masks,etc., as appropriate.
- Annotations  : They are used by display tasks, and are used for visual reference only.

After from the regular region shapes there are special definitons such as line, vector and special symbols which are always identified as annotations and are not currently supported by regions package.

##### Few of the features that this project aims to do ,

- Implement new regions/annotations that CRTF supports.(symbols, box, etc..)
- Provide the required attributes and functionalities to the existing region/shape classes.
- Implement a parser for reading CRTF region files.
- Implement a CRTF writer.
- Implement cube region that CASA supports but currently not present in astropy-regions.
- Provide documentation to all the features added.
- Creating a test suite to ensure everything works as expected.

#### DETAILED DESCRIPTION:

1. Creating a parser : The casa CRTF format has a different syntax style than DS9 regions.It is little more complicated to parse due to larger grammar rules. The also provides a large
set of definitions which has values in a particular domain. The API needs to be made similar to that of the DS9 parser to be user friendly. The first task wiuld be to implement parser for 
the regions and annotations. The second thing would be to parse the meta data i.e the definitions. I intend to make the following main classes :
   1. `CRTFParser` : takes a region string and would contain CRTFShapeList which can be ultimately converted to region objects.It would contain several methods such as 
   `parse_line` to parse single region and `parse_meta`.There would be appropriate storing the resultant meta as well as regions.In the process of converting into 
   a CRTFShapeList there would be help of several helper classes. 
        1. `CRTFRegionParser` : this class will help turning a line containing regions in CRTF format to CRTFShape object.
        2. `CRTFShape` : this is a class which is used to represent a CRTF region so that it can be easily convertible to a regions object,kind of acts like an intermediate. 
        3. `CRTFCoordinateParser` : helper class to parse string coordinates and transform into astropy.coordinate objects (mostly `SkyCoord` objects).
   2. `CRTFShapeList` : It is a list of Shape.It would also contain `to_CRTFObject` method to convert into `CRTFObject`.
   
The first thing would be able to parse regions.Then, it should be able to parse meta data (definitions).

2. Implementing a Writer : We should be able to  convert the regions object into CRTF format strings and write them into files.
The `writeDS9` method directly converts region lists into strings thus formatting the DS9 region file difficult.
To represent CRTF region file we can create a `CRTFObject` and insert further global definitions , comments and tweak regions according to the user.
The CRTFObject may be represented as list of sentences.(A single sentence represents a single region/annotation).
The plan is to convert :
    1. region list to `CRTFShapeList`. 
    2. the `CRTFShapeList`can be converted to `CRTFObject` 
    3. the `CRTFObject` can finally be converted to region strings.

   We can add functions that wraps the first and second step.
   We can also `writeCRTF` to convert regions directly to strings. 
   The new thing (`CRTFObject`), will be heavily discussed with the community and will be implemented if seems necessary.

3. Implement 2-D regions : there are several annotations described in the CRTF region format that are not currently implemented.
    1. Vector : Probably should inherit Line shape.
    2. Text : Probably should inherit point shape with an extra text attribute.
    3. Symbols :this will also inherit point shape with an extra symbol attribute.
    
   The important thing for the above annotations is to represent them in plots by some plotting libraries such as matplotlib through `as_patch` methods.

4. Adding missing functionalities to existing region classes : 

5. Implementing 3-D regions : 
  


#### 6.  Timeline:
#### 7.  Schedule Availability:
    
    

