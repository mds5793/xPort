# Supported Systems and Languages for xPort - Porting Software  

<p align="center">
 <img src="https://github.com/mds5793/xPort-Software-Exporting-Guidelines/blob/main/q_pp.png?raw=true" width=512 align="center">
</p>

Ideally, it would be nice to have a Package Manager in xPort where you can import Open Source or Proprietary Bindings for the Target Systems.  

### Supported Target Systems (Each Target System has to be trained on an LLM):  
Windows  
macOS  
swiftOS  
Linux  
CUDA  
iOS - (Not Currently Supported)  
Android - (Not Currently Supported)  

### Supported Source Languages:  
C  
C++  
Swift  
C# - (Not Currently Supported)  
Java - (Not Currently Supported)  
 
### Supported Target Languages (QOOL - Quantum Object Oriented Languages):  
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
NVIDIA PhysX - (Not Currently Supported)  
OpenPhysics  

### Target Physics API:  
NVIDIA PhysX - (Not Currently Supported)  
OpenPhysics  

### xPort Block Comment Descriptors: 
In order for xPort to function properly, use the following block comments as necessary.  
Using a LLM to produce these following descriptors is recommended.  
Using a LLM to perform Unit Tests and ensuring the return results are the same as the source language or framework is also recommended.  
 
@exclude - Use this before every class, struct, or function you wish to exclude from being ported via xPort if it is a Software Trade Secret.  
@brief - Briefly describe the functionality or purpose of your function.  
@param - Use this to describe all the parameters of your functions.  
@return - Use this to describe the expected result of your function and any values that are returned.    

#### If there is no equivalent function, struct, or class or @exclude is used then it should throw the following error:  
```
Error: No equivalent struct, class, or function in target API. Please provide your own implementation.
```

#### Best Practices:  
It would be helpful for the porting team if when using the @exclude tag, to allow the LLM to offer a brief description inline with @brief,   @param, and @return descriptors.  
However, the LLM WILL not read the data, or algorithms inside the class, function, or struct that is being excluded.  

## CLI COMMANDS 
xport [options...][input directory][output directory]  
(If not input directory is provided it will assume the working directory, likewise output directory also).  

Example Command:  
xport -sys=win -lang=c|qpp -gfx=dx|v -phys=opx|npx ../[curr_dir] ../bin/  

OPTIONS:  
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
