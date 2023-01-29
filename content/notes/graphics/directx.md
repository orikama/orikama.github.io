+++
title = 'DirectX'
+++

## DirectX 11

- Buffers management
  - [Constant Buffers without Constant Pain (NVIDIA)](https://developer.nvidia.com/content/constant-buffers-without-constant-pain-0)
  - [Copying and Accessing Resource Data (Direct3D 10)](https://docs.microsoft.com/en-us/windows/win32/direct3d10/d3d10-graphics-programming-guide-resources-mapping)

## DirectX 12

- Implementations
  - [Mini engine, DX12, Path Tracing](https://github.com/KaiH0717/Kaguya)
    - https://github.com/KaiH0717/KHRay
  - [Strong DX12 abstraction? Bindless, Render Graph, Path Tracing](https://github.com/man-in-black382/PathFinder)
  - [DX12 renderer with simple design](https://github.com/mateeeeeee/Adria-DX12)
    - Has DX11 version, may be I should start with it

- ??
  - Swap chain | DXGI_SWAP_CHAIN_DESC
    - DXGI_SWAP_EFFECT
      - Only use `DXGI_SWAP_EFFECT_FLIP_SEQUENTIAL` or `DXGI_SWAP_EFFECT_FLIP_DISCARD`
      - [DXGI_SWAP_EFFECT](https://docs.microsoft.com/en-us/windows/win32/api/dxgi/ne-dxgi-dxgi_swap_effect)
      - [For best performance, use DXGI flip model](https://docs.microsoft.com/en-us/windows/win32/direct3ddxgi/for-best-performance--use-dxgi-flip-model)
        - Important part -> What do I have to do to use the flip model?
