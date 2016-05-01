# get-opencl-headers

## Description
This script automatically fetches OpenCL header files from Khronos Group repositories:

* https://github.com/KhronosGroup/OpenCL-Headers 
* https://github.com/KhronosGroup/OpenCL-CLHPP

## Usage

Get OpenCL headers including cl.h, cl_ext.h, cl_go.h and so on.

```bash
sh get-opencl-headers.sh
```

Get cl.hpp header (for OpenCL 1.0, 1.1, 1.2) or cl2.hpp (for OpenCL 2.0, 2.1)

```bash
sh get-opencl-headers.sh --include-clhpp
```

**Notice:** to get the cl.hpp header, **_python_** is required.

### Local file structures

After fetching, the headers are put into _include_ folder with the following structure:

```
-include
    |-CL10
    |-CL11
    |-CL12
    |-CL20
    |-CL21
    |-CL
```

The _CL_ folder is a symbolic link, by default, pointing to _CL11_. You can change it based on your need. For example, if we want _CL_ to link to _CL20_:

```bash
rm CL
ln -s CL20 CL
```
Therefore, in your OpenCL program, you can easily include OpenCL header file by doing the following:

```C++
#include <CL/cl.h>
```

or 

```C++
#include <CL/cl.hpp>
```
