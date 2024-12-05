<h1 align="center">xPort - AI Porting Software - Technical Guidelines</h1>

<p align="center">
 <img src="https://github.com/mds5793/xPort-Software-Exporting-Guidelines/blob/main/img/q_pp.png?raw=true" width=400 />
 <img src="https://github.com/mds5793/xPort-Software-Exporting-Guidelines/blob/main/img/q_sharp.png?raw=true" width=400 />
</p>

<h1 align="center">Software Description</h1>

### Purpose & Mission Statement  
1. xPort is a platform agnostic AI enhanced porting toolkit developed to ease the burden and cost of porting software to other platforms.  
2. xPort was originally intended to give indie game studios an easy avenue for porting their projects to different platforms.  
3. xPort is licensed under the MIT License. 

This README serves as a technical guideline and roadmap for the development of xPort.  

### Table of Contents  
1. [Software Description](#software-description)  
   i.[Target Platforms](#target-platforms)  
  ii.[Source Languages](#source-languages)  
 iii.[Target Languages](#target-languages)  
  iv.[Source Graphics API](#source-graphics-api)  
   v.[Target Graphics API](#target-graphics-api)  
  vi.[Source Physics API](#source-physics-api)  
 vii.[Target Physics API](#target-physics-api)  
viii.[Block Comment Tags](#block-comment-tags)

2. [CLI Tools](#cli-tools)  
   i. [General Command Structure](#general-command-structure)  
   ii. [Command Line Options](#command-line-options)  

3. [Software Distributables & Documentation](#software-distributables-and-documentation)  
   i. [GUI Application](#gui-application)  
   ii. [Documentation](#documentation)  

### Target Platforms   
##### Note: If possible the native windowing API should be used.
Windows  
macOS  
Linux - (incl. steamOS)  
swiftOS - (incl. razerOS)  
CUDA  
Android  
iOS  
Playstation   
XBOX    
Nintendo    

### Source Languages  
C/C++  
Swift  
C#  
Java   
 
### Target Languages  
##### Classical
C/C++  
Swift  
C#  
Java    
##### Quantum
Q++  
Q#  

### Source Graphics API  
DirectX  
Metal  
Vulkan  

### Target Graphics API  
DirectX  
Metal  
Vulkan  

### Source Physics API   
NVIDIA PhysX  
OpenPhysics  

### Target Physics API  
NVIDIA PhysX    
OpenPhysics  

### Block Comment Tags  
In order for xPort to function properly, use the following block comment tags as necessary.  
Using an LLM to produce the tags is recommended.  
Using an LLM to perform unit tests and ensuring the output is identical is also recommended.  
##### Note: xPort is able to generate the tags with the -g command line option, but it won't generate _```@exception```_ tags. You must add those manually.   
```
@exception - Use this tag to tell xPort to ignore the class, struct or function if it's proprietary.  
@name - Use this to provide a name for your class, struct or function.
@brief - Briefly describe the functionality or purpose of your class, struct or function.  
@param - Use this to describe all the parameters of your functions.  
@return - Use this to describe the expected result of your function and any values that are returned.
```

#### If there is no equivalent class, struct or function <ins>***_OR_***</ins> the _```@exception```_ tag is used then it should throw the following exception:  
```
Exception: No equivalent class, struct or function called @name in target API. Please provide your own implementation.
```

#### Best Practices:  
It would be helpful for porting purposes when using the _```@exception```_ tag to allow the LLM to offer a brief description.  
Such as allowing the LLM provided in xPort to read the _```@brief```_, _```@param```_, and _```@return```_ tags.  
This could be achieved by enabling the verbose (```-v```) command line flag in xPort.  
However, the LLM **<ins>_WILL NOT_</ins>** read the data or algorithms inside the class, function, or struct that is being ignored.  

[Back to top...](#table-of-contents)
<h2 align="center">CLI Tools</h2>

### General Command Structure  
```xport [options...][output_directory]```

#### If no output directory is specified, then xPort assumes the working directory.

Example Command:  
```xport -g -sys=win -lang=c|qpp -gfx=dx|v -phys=opx|npx /bin```  

#### If desired you can run xPort for the sole purpose of generating tags in your code as follows:  
```xport -g /bin```  

Where bin is the output directory. This is useful if you want to manually add _```@exception```_ tags to your code prior to translation.

##### Note: In order to see a list of the options on the command line, use the following syntax:  
```
xport --help
```

##### Note: In order to view the version number use the following command:  
```
xport --version
```

##### Note: xPort <ins>**_WILL NOT_**</ins> compile your code, you must do that yourself with the appropriate compiler.  

#### Q++ Compiler  
Bundled with this software package is an open-source compiler for q++ available under the MIT License.  

#### Example Q++ Compiler Syntax  
```
q++ -o main main.qpp lib.hqpp
```
##### Note: As shown above, the file extension for a Q++ header file is 4 letters: .hqpp  

### Command Line Options  
```
-g = GENERATE BLOCK COMMENT TAGS
-v = ENABLE VERBOSE MODE FOR EXCEPTIONS
 
-sys = [TAR_SYS]  

TAR_SYS
[win = WINDOWS]
[mac = MACOS]
[lin = LINUX]
[sft = SWIFTOS]
[ios = iOS]
[apk = ANDROID]
[psn = PLAYSTATION]
[xbx = XBOX]
[nin = NINTENDO]
[cuda=  CUDA]  

-lang = [SRC_LANG | TAR_LANG]  

SRC_LANG = [c = ANSI C][cpp = C++][csh = C#][java = JAVA][swift = SWIFT]  
TAR_LANG = [qsh = Q#][qpp = Q++][c = ANSI C][cpp = C++][csh = C#][java = JAVA][swift = SWIFT]     

-gfx=[SRC_GFX | TAR_GFX]

SRC_GFX = [dx = DIRECTX][m = METAL][v = VULKAN]  
TAR_GFX = [dx = DIRECTX][m = METAL][v = VULKAN]  

-phys=[SRC_PHYSX | TAR_PHYSX]
  
SRC_PHYSX = [npx = NVIDIA PHYSX][opx = OPEN PHYSICS]  
TAR_PHYSX = [npx = NVIDIA PHYSX][opx = OPEN PHYSICS]
```
[Back to top...](#table-of-contents)
<h1 align="center">Software Distributables and Documentation</h1>  

#### (Please Note: Documentation and executables are not currently available. The links below simply loop back to this README...)  

### GUI Application
Windows - [Download](#software-description)  
macOS - [Download](#software-description)  
Linux - [Download](#software-description)  

### Documentation
[API Documentation](#software-description)  
[Q++ Compiler Source Code & Documentation](#software-description)  

[Back to top...](#table-of-contents)
