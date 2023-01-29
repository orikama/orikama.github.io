+++
title = 'Models'
+++

## OBJ

- Specification
  - [Object Files (.obj)](http://paulbourke.net/dataformats/obj/)
  - [Wavefront .obj file, Wiki](https://en.wikipedia.org/wiki/Wavefront_.obj_file)
  - [???](http://www.martinreddy.net/gfx/3d/OBJ.spec)
- Implementations
  - [fast_obj](https://github.com/thisistherk/fast_obj)
  - [rapidobj](https://github.com/guybrush77/rapidobj)
  - [tinyobjloader](https://github.com/tinyobjloader/tinyobjloader)
  - [assimp](https://github.com/assimp/assimp/tree/master/code/AssetLib/Obj)
  - Blender OBJ importer improvments by Aras Pranckevicius
    - [Tweet](https://twitter.com/aras_p/status/1512031554322718726)
    - [New C++ based wavefront OBJ importer](https://developer.blender.org/D13958)
    - [OBJ: further optimize, cleanup and harden the new C++ importer](https://developer.blender.org/D14586)
- MTL
  - [MTL material format (Lightwave, OBJ) Excerpt from FILE FORMATS, Version 4.2 October 1995](http://paulbourke.net/dataformats/mtl/)
  - [Alias/WaveFront Material (.mtl) File Format](https://www.fileformat.info/format/material/)
  - Unsupported keywords in materials (Sponza has 'map_disp' for example)
    - https://stackoverflow.com/questions/26453143/simple-curiosity-with-wave-front-resource-material-format
