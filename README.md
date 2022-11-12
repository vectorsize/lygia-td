# LygiaTD

This is a native port of [LYGIA Shader Library](https://github.com/patriciogonzalezvivo/lygia) by [Patricio Gonzalez Vivo](https://github.com/patriciogonzalezvivo)'s.

## Description

This library is a statically built version of the library ~ and hence no internet connection is needed for file resolution during runtime.  
This version uses TouchDesigner's native include resolution mechanism for all the library's `#include`.  
The provided `.tox` file bundles all the files from the original libraries with modified paths and compliant names for it to work inside TouchDesigner.

## Versioning
> current version is `v.1.0.0`

This port will include static snapshots of the upstream repository and will be updated on every release porviding mathing versions for each release.

## Usage

You can find along the `.tox` file a demo `sandbox.toe` project showcasing it's use.
Mainly you need to make the `.tox` file to your project either via the global component library or by dragging it inside your project.
Once the file is on your project, all works as expected with one **main difference**: file extensions for the `{filename}.glsl` programs become inside TouchDesigner a corresponding prepopulated `textDAT` named `{filename}_glsl`, hence your import will look as follows:

```
#include "filter/gaussianBlur_glsl"
```

as opposed to

```
#include "filter/gaussianBlur.glsl"
```

## Motivation

Shortly after the original library's release `v1.0.0` a TouchDesigner version of it was published [here](https://derivative.ca/community-post/asset/lygia-touchdesginer/66804) by [LeithBA](https://github.com/LeithBA).
While the library works perfectly fine, it uses runtime web resolution for the files, which then makes having an internet connection available a requirement, on top of the overhead of such resolutions.
On the other hand TouchDesigner has native include resolution at it's core.
For those reasons I decided to bundle a native version of the library.

## Details

The whole library is packaged by cloning the upstream source and parsing all the files, updating the include paths and pipulating the guts of several `textDAT`s placed in their corresponding project hierarchy.
The parsing script might be released opensource if there is enough interest.
