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
Linux  
steamOS  
swiftOS  
razerOS  
CUDA  
Playstation - (Not Currently Supported)  
XBOX - (Not Currently Supported)  
Nintendo - (Not Currently Supported)  
iOS - (Not Currently Supported)  
Android - (Not Currently Supported)  

### Source Languages:  
C/C++  
Swift  
C# - (Not Currently Supported)  
Java - (Not Currently Supported)  
 
### Target Languages  
C/C++  
Swift  
C# - (Not Currently Supported)  
Java - (Not Currently Supported)  

Q++  
Q# - (Not Currently Supported)  

### Source Graphics API:  
DirectX  
Metal  
Vulkan  

### Target Graphics API:  
DirectX  
Metal  
Vulkan  

### Source Physics API:  
NVIDIA PhysX  
OpenPhysics  

### Target Physics API:  
NVIDIA PhysX  
OpenPhysics  

### xPort Block Comment Descriptors: 
In order for xPort to function properly, use the following block comments as necessary.  
Using an LLM to produce these following descriptors is recommended.  
Using an LLM to perform Unit Tests and ensuring the return results are the same as the source language or framework is also recommended.  
```
@exclude - Use this tag to tell xPort to ignore the class, struct or function if it's proprietary. 
@brief - Briefly describe the functionality or purpose of your function.  
@param - Use this to describe all the parameters of your functions.  
@return - Use this to describe the expected result of your function and any values that are returned.
```

#### If there is no equivalent function, struct, or class OR @exclude is used then it should throw the following error:  
```
Error: No equivalent struct, class, or function in target API. Please provide your own implementation.
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
```xport -sys=win -lang=c|qpp -gfx=dx|v -phys=opx|npx ../[curr_dir] ../bin/```

#### OPTIONS  
```
-sys = [TAR_SYS]  

[win = WINDOWS]  
[mac = MACOS]  
[lin = LINUX]  
[sos = SWIFTOS]  
[ios = iOS]  
[apk = ANDROID]  
[cuda = CUDA]  
TAR_SYS = [win][mac][lin][sos][ios][apk][cuda]  

-lang = [IN_LANG | OUT_LANG]  

[c = ANSI C]  
[cpp = C++]  
[csh = C#]  
[java = Java]  
[swift = Swift]  
IN_LANG = [c][cpp][csh][java][swift]  

[qsh = Q#]  
[qpp = Q++]  
OUT_LANG = [qsh][qpp]  

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
