# LygiaTD

This is a TouchDesigner native port of [LYGIA Shader Library](https://github.com/patriciogonzalezvivo/lygia) by [Patricio Gonzalez Vivo](https://github.com/patriciogonzalezvivo).

## Description

This repository is a statically built version of the library ~ and hence no internet connection is needed for file resolution during runtime.  
This version uses TouchDesigner's native include resolution mechanism for all the library's `#include`.  
The provided `.tox` file bundles all the files from the original libraries with modified paths and compliant names for it to work inside TouchDesigner.

## Versioning

> current version is `v.1.1.0`

This port will include static snapshots of the upstream repository and will be updated on every release porviding matching versions for each release.

## Changelog / Divergences

- Imports do not have file extention but `_glsl` termination.
- Since his is a TD only version, there is no longer need to declare a `SAMPLER_FNC` before the imports. The default `SAMPLER_FNC` is now `texture`.

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

> see attached figure.

![lygia](https://user-images.githubusercontent.com/1661889/201487441-4f8f867a-d75a-42f8-a1a6-d38002bd4d22.jpg)

## Motivation

Shortly after the original library's release `v1.0.0` a TouchDesigner version of it was published [here](https://derivative.ca/community-post/asset/lygia-touchdesginer/66804) by [LeithBA](https://github.com/LeithBA).  
While the library works perfectly fine, it uses runtime web resolution for the files, which then makes having an internet connection available a requirement, on top of the overhead of such resolutions.
On the other hand TouchDesigner has native include resolution at it's core.  
For those reasons I decided to bundle a native version of the library.

## Details

The whole library is packaged by cloning the upstream source and parsing all the files, updating the include paths and populating the guts of several `textDAT`s placed in their corresponding project hierarchy.  
The parsing script might be released opensource if there is enough interest.

## LYGIA License

LYGIA is dual-licensed under [the Prosperity License](https://prosperitylicense.com/versions/3.0.0) and the [Patron License](https://lygia.xyz/license) for [sponsors](https://github.com/sponsors/patriciogonzalezvivo) and [contributors](https://github.com/patriciogonzalezvivo/lygia/graphs/contributors).

[Sponsors](https://github.com/sponsors/patriciogonzalezvivo) and [contributors](https://github.com/patriciogonzalezvivo/lygia/graphs/contributors) are automatically added to the [Patron License](https://lygia.xyz/license) and they can ignore any non-commercial rule of [the Prosperity Licensed](https://prosperitylicense.com/versions/3.0.0) software.

Comming soon will be possible to get a permanent comercial license hook to a single and specific version of LYGIA.
