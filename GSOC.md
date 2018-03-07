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
        
#### 5.  Interest In OpenAstronomy

## PROJECT TITLE : CASA CRTF REGION FILE HANDLING
#### 4.  Preliminary Research

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

#### DETAILED DESCRIPTION

1. Implement new regions/annotations : The regions currently does not supports several regions such as centerbox, rotatedbox, vector, certain symbols.
Annotations are also to be handled.Initially, i will discuss with the lead maintainers about the best possible way
to design and implement the classes to make CASA regions feel as native as possible. 

2. Provide required functionalities to existing region classes: Some of the methods of the existing classes are yet to be 
implemented and many of the methods lack proper documentation.The meta and the visual attributes are not properly documented and 
may lead to confusion since the regions package would be handling both ds9 as well as CRTF. I will make sure that all the methods are implemented and
properly documented that CRTF needs. i will also make sure that these are thoroughly tested.

3.Creating a parser : The most important thing



#### 6.  Timeline
#### 7.  Schedule Availability
    
    

