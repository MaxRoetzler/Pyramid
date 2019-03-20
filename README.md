# Pyramid

Pyramid is a free, open GUI tool for offline shader validation and analysis. The UI takes HLSL or GLSL as input, and runs them through various shader
compilers and static analyzers.

Here is Pyramid, showing HLSL shader compiled and disassembled for AMD's GCN, and a GLSL shader compiled and disassembled for PowerVR 6 *(click for full-size image)*:

[![AMD GCN from HLSL](doc/ui-hlsl-amddxx-thumb.png)](doc/ui-hlsl-amddxx.png?raw=1)
[![PowerVR disassembly from GLSL](doc/ui-glsl-powervr-thumb.png)](doc/ui-glsl-powervr.png?raw=1)

Currently, Pyramid supports these tools:

* HLSL:
	* Microsoft D3D compiler *(d3dcompiler_47)*: for showing D3D assembly.
	* AMD DXX driver *(Catalyst 14.9)*, used for GCN disassembly and [shader execution simulation](http://www.joshbarczak.com/blog/?p=823).
	* AMD [CodeXL analyzer](http://developer.amd.com/tools-and-sdks/opencl-zone/codexl/) *(version 1.5)*.
    * glslang HLSL front end (2017 January build)
    * [DXC] (https://github.com/microsoft/DirectXShadercompiler)
    * [Intel Shader Analyzer](http://github.com/GameTechDev/IntelShaderAnalyzer)
* GLSL:
	* Khronos reference [glslang](https://github.com/KhronosGroup/glslang) validator *(2017 January build)*.
	* Imagination [PowerVR Rogue compiler](https://community.imgtec.com/developers/powervr/tools/pvrshadereditor/) *(version 3.4)*.
	* ARM [Mali offline compiler](http://malideveloper.arm.com/resources/tools/mali-offline-compiler/) *(version 4.6)*.
	* [glsl-optimizer](https://github.com/aras-p/glsl-optimizer) *(2015 November build)*.

All the above tools are included under bin/ folder for convenience. These are all publicly available binaries, but I do not own them, maintain them,
and am not responsible for them.  If you like you can use the Options screen to point Pyramid at different versions of the tools.

Pyramid is intended to eventually support arbitrary languages and glue together tools and disassemblers from all over
the graphics world.
 
IHVs:  You want developers scrutinizing the ISA for your GPUs.  You know you do :) I will work with you to incorporate your disassemblers into this tool.  I am willing to jump through hoops to make this happen, just tell me what I need to do.


## Obtaining Pyramid

The best way to obtain a copy is to ask github to download a zip of the repository.  The `bin` directory will be updated periodically with an up to date binary.  

Pyramid is built against .NET framework 4.5 and runs on Windows.  If you don't have it, you need to go get it.  Otherwise, just put the contents of `bin` wherever
you like, there is no installer.

Pyramid will create a configuration file under `AppData\Local\Pyramid`.  At runtime, it will also create and delete temporary files in this location.  Apart from that,
there are no other changes made to the system.  In particular, there is no registry nonsense.

Pyramid is distributed as is. There is no warranty of any kind. I will not guarantee timely support, but I will be happy to accept bug fixes, patches, or contributions.
[License](LICENSE.txt) is GPL.

You may send constructive feedback to:  jbarcz1@gmail.com



## Building it Yourself

Due to my use of submodules, downloading a zip will not get you the full source.

The best way to obtain the full source is to install git, open a shell, and type:

    git clone --recurse https://github.com/jbarczak/Pyramid

This will ensure that all of the submodules are downloaded.  github does not include submodules when you download a zip.

I use and recommend MSysGit:  https://msysgit.github.io/

Pyramid was developed using VC++ 2013 express edition (Desktop).  It runs correctly on my machine (Windows 8.1 with VC++ express installed).  

The build products will be copied from `src/bin` into `bin` on each compile.  

By default, Pyramid uses relative paths to look for all of the external binaries.  For debugging, it's best to point the working directory at `bin` so that they will be found.  Alternatively, you can use the options menu to replace the paths with absolutes.
