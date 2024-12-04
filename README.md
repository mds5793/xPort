<h1 align="center">xPort - AI Enhanced Porting Software</h1>

<p align="center">
 <img src="https://github.com/mds5793/xPort-Software-Exporting-Guidelines/blob/main/img/q_pp.png?raw=true" width=400 />
 <img src="https://github.com/mds5793/xPort-Software-Exporting-Guidelines/blob/main/img/q_sharp.png?raw=true" width=400 />
</p>

<h2 align="center">
 GUI Layout
</h2>

<p align="center">
 <img src="https://github.com/mds5793/xPort-Software-Exporting-Guidelines/blob/main/img/xPort-Layout.png?raw=true" width=768 />
</p>

### Target Platforms      
Windows  
macOS  
Linux - (incl. steamOS)  
swiftOS - (incl. razerOS)  
CUDA  
Android  
Playstation   
XBOX 
Nintendo - (Not Currently Supported)  
iOS - (Not Currently Supported)    

### Source Languages  
C/C++  
Swift  
C# - (Not Currently Supported)  
Java - (Not Currently Supported)  
 
### Target Languages  
##### Classical
C/C++  
Swift  
C# - (Not Currently Supported)  
Java - (Not Currently Supported)  
##### Quantum
Q++  
Q# - (Not Currently Supported)  

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

### xPort Block Comment Tags  
In order for xPort to function properly, use the following block comment tags as necessary.  
Using an LLM to produce the tags is recommended.  
Using an LLM to perform unit tests and ensuring the output is identical is also recommended.  
##### Note: xPort is able to generate the tags with the -g command line option, but it won't generate @exclude tags. You must add those manually.   
```
@exclude - Use this tag to tell xPort to ignore the class, struct or function if it's proprietary. 
@brief - Briefly describe the functionality or purpose of your function.  
@param - Use this to describe all the parameters of your functions.  
@return - Use this to describe the expected result of your function and any values that are returned.
```

#### If there is no equivalent class, struct or function OR the @exclude tag is used then it should throw the following error:  
```
Error: No equivalent class, struct, or function in target API. Please provide your own implementation.
```

#### Best Practices:  
It would be helpful for the porting team when using the @exclude tag to allow the LLM to offer a brief description.  
Such as allowing the LLM provided in xPort to read the @brief, @param, and @return descriptors.  
However, the LLM **<ins>WILL NOT</ins>** read the data or algorithms inside the class, function, or struct that is being excluded.  

<h2 align="center">
CLI Tools 
</h2>

### General Command Structure  
```xport [options...][input directory][output directory]```

#### If no output or target directory is specified, then xPort assumes the working directory.  

Example Command:  
```xport -g -sys=win -lang=c|qpp -gfx=dx|v -phys=opx|npx ../[curr_dir] ../bin/```

#### OPTIONS  
```
-g = Generate Block Comment Descriptors (w/o @exclude)
 
-sys = [TAR_SYS]  

[win = WINDOWS]  
[mac = MACOS]  
[lin = LINUX]  
[sos = SWIFTOS]
[ios = iOS]  
[apk = ANDROID]
[ps = PLAYSTATION]
[xbx = XBOX]
[nin = NINTENDO]  
[cuda = CUDA]  
TAR_SYS = [win][mac][lin][sos][ios][apk][ps][xbx][nin][cuda]  

-lang = [IN_LANG | OUT_LANG]  

[c = ANSI C]  
[cpp = C++]  
[csh = C#]  
[java = Java]  
[swift = Swift]  
IN_LANG = [c][cpp][csh][java][swift]  

[qsh = Q#]  
[qpp = Q++]  
[c = ANSI C]  
[cpp = C++]  
[csh = C#]  
[java = Java]  
[swift = Swift]  
OUT_LANG = [qsh][qpp][c][cpp][csh][java][swift]  

-gfx=[SRC_GFX | TAR_GFX]  
-phys=[SRC_PHYSX | TAR_PHYSX]  

[dx = DIRECTX]  
[m = METAL]  
[v = VULKAN]  
SRC_GFX = [dx][m][v]  
TAR_GFX = [dx][m][v]  

[npx = NVIDIA PHYSX]  
[opx = OPEN PHYSICS]  
SRC_PHYSX = [npx][opx]  
TAR_PHYSX = [npx][opx]  
```
