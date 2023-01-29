+++
title = 'Graphics'
+++

## Ray Tracing

- BVH
  - [How to build a BVH – Part 1: Basics](https://jacco.ompf2.com/2022/04/13/how-to-build-a-bvh-part-1-basics/)
- Denoiser
  - [Intel Open Image Denoise](https://www.openimagedenoise.org/)
  - [NVIDIA OptiX Ray Tracing Engine](https://developer.nvidia.com/rtx/ray-tracing/optix)
  - [NVIDIA REAL-TIME DENOISERS (NRD)](https://developer.nvidia.com/rtx/ray-tracing/rt-denoisers)

## Transparency

- Terms
  - depth peeling
  - stencil routed k-buffer
  - Order-independent transparency

## RenderGraph

- [Render Graph Optimization Scribbles](https://www.jeremyong.com/rendering/2019/06/28/render-graph-optimization-scribbles/)
  Scheduling RenderPasses so that they can overlap
- [Render graphs and Vulkan — a deep dive](https://themaister.net/blog/2017/08/15/render-graphs-and-vulkan-a-deep-dive/)
  - https://github.com/Themaister/Granite
- [Organizing GPU Work with Directed Acyclic Graphs](https://levelup.gitconnected.com/organizing-gpu-work-with-directed-acyclic-graphs-f3fd5f2c2af3)
  - https://www.reddit.com/r/GraphicsProgramming/comments/hov5wl/organizing_gpu_work_with_directed_acyclic_graphs/
  - [PathFinder, DX12 renderer](https://github.com/man-in-black382/PathFinder)
- [High-Level Rendering Using Render Graphs](https://ourmachinery.com/post/high-level-rendering-using-render-graphs/)

## API

- [The smooth resize test](https://raphlinus.github.io/rust/gui/2019/06/21/smooth-resize-test.html)
  - His blog has more articles about window/swapchain
  - [Swapchains and frame pacing](https://raphlinus.github.io/ui/graphics/gpu/2021/10/22/swapchain-frame-pacing.html)
  - [StackOverflow long read](https://stackoverflow.com/questions/53000291/how-to-smooth-ugly-jitter-flicker-jumping-when-resizing-windows-especially-drag/)
  - [DXGI overview](https://docs.microsoft.com/en-us/windows/win32/direct3ddxgi/d3d10-graphics-programming-guide-dxgi)

- Texture View performance
  - [Texture views cause unnecessary memory bandwidth use](https://github.com/gpuweb/gpuweb/issues/744)
  - [What are 'typeless' DXGI texture formats in DirectX?](https://stackoverflow.com/questions/63988220/what-are-typeless-dxgi-texture-formats-in-directx)

### Web GPU Discussions

- [Investigation: Viewport and Scissor Test](https://github.com/gpuweb/gpuweb/issues/120)

### API Differences

- https://github.com/gpuweb/gpuweb/issues/416
  - Use the same as they are?
    "Solution 1: Y up in NDC, Y down in other coordinate systems"
    spirv shaders can be compiled with Y fliped?
  - https://veldrid.dev/articles/backend-differences.html

- Face winding
  - GL:   CCW
  - DX11: CW

## Stuff

- Resizable BAR, uploading without staging buffers
  - https://www.reddit.com/r/vulkan/comments/kkmu5z/resizable_bar_staging_buffers/
  - https://twitter.com/sebaaltonen/status/1327159607068864512?lang=en
  - Texture uloading without staging buffer?
    - https://twitter.com/SebAaltonen/status/1327171850485559296

- Rasterization in slow motion
  - https://github.com/michal-z/zig-gamedev/tree/main/samples/rasterization
  - https://twitter.com/MichalZiulek/status/1486375154536128523

## MSAA

- [A Quick Overview of MSAA](https://therealmjp.github.io/posts/msaa-overview/)
- [Anti-aliased Alpha Test: The Esoteric Alpha To Coverage](https://bgolus.medium.com/anti-aliased-alpha-test-the-esoteric-alpha-to-coverage-8b177335ae4f)
