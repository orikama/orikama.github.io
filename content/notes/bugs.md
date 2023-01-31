+++
title = 'Bugs'
+++

## MSVC

### Open

- [VS 2022 17.5.0 Preview 2 C++20 modules bug: values in a static array in an inline function are always initialized to zero](https://developercommunity.visualstudio.com/t/VS-2022-1750-Preview-2-C20-modules-b/10229203)
- [VS 2022 17.5.0 Preview 2 C++20 modules bug: [[maybe_unused]] doesn't work](https://developercommunity.visualstudio.com/t/VS-2022-1750-Preview-2-C20-modules-b/10230159)
- [VS 2022 17.5.0 Preview 2 C++20 modules bug: static variable in a function doesn't updates](https://developercommunity.visualstudio.com/t/VS-2022-1750-Preview-2-C20-modules-b/10232773)
- [C++20 modules: returning anonymous type from a method breaks object layout](https://developercommunity.visualstudio.com/t/C20-modules:-returning-anonymous-type/10233191)  
  What is this syntax? Seems like [only MSVC compiles it](https://godbolt.org/z/17zr471EY)
  ```cpp
  struct Struct
  {
      struct { float x; float y; } GetXY() { return { _x, _y }; };
      float _x;
      float _y;
  };
  ```

### Fixed

- [\<fstream\>: Importing as a header unit leads to error C2079: undefined class 'std::basic_ofstream<char,std::char_traits<char>>'](https://github.com/microsoft/STL/issues/3112)
- [\<atomic\>: Building a header unit with /ZI emits warning C5260](https://github.com/microsoft/STL/issues/3287)

## Unity

### Questions without an answer

- [Missing RayTracing API features, RayTracingAccelerationStructure bugs?](https://forum.unity.com/threads/missing-raytracing-api-features-raytracingaccelerationstructure-bugs.1158698/)
  - [It actually was partially answered, sadly I was just not worty enough](https://forum.unity.com/threads/dxr-raytracing-effect-from-scratch.794928/#post-7115344)

### Fixed

- [Fog and volumetric lights in Path Tracing](https://forum.unity.com/threads/fog-and-volumetric-lights-in-path-tracing.1151009/)
- [Editor hangs when importing certain .fbx files](https://issuetracker.unity3d.com/product/unity/issues/guid/UUM-15346)
- [[HDRP] Camera view is rendered on objects with a Distortion Blur material when Dynamic Resolution is enabled](https://issuetracker.unity3d.com/issues/hdrp-camera-view-is-rendered-on-objects-with-a-distortion-blur-material-when-dynamic-resolution-is-enabled)
