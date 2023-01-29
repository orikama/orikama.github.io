+++
title = 'MSVC'
+++

## Diagnostics

- [ADSP Episode CX: Compiler Diagnostics](https://www.reddit.com/r/cpp/comments/zz1f4f/adsp_episode_cx_compiler_diagnostics/)
- [The Future of C++ Compiler Diagnostics in MSVC and Visual Studio](https://devblogs.microsoft.com/cppblog/the-future-of-c-compiler-diagnostics-in-msvc-and-visual-studio/)

## Flags

- `/vmm`, `/vms`, `/vmv` [docs](https://learn.microsoft.com/en-us/cpp/build/reference/vmm-vms-vmv-general-purpose-representation)
  - apparently it's possible to control the size of the pointer to member function?
  - learned about it in "Game Engine Gems 3, Chapter 13: Generic, Lightweight, and Fast Delegates in C++"

### Hidden

- [MSVC hidden flags](https://lectem.github.io/msvc/reverse-engineering/build/2019/01/21/MSVC-hidden-flags.html)
- `/d1ifcInlineFunctions` or `/dxifcInlineFunctions`
  - [reddit comments from microsoft devs](https://www.unddit.com/r/cpp/comments/ze0w89/instead_of_a_c_template_parlor_trick_why_not_just/)
    - https://developercommunity.visualstudio.com/t/Functions-imported-from-modules-are-neve/1593838
  - [this flag enabled by default in 17.5 Preview 2 is the reason for my bug report](https://developercommunity.visualstudio.com/t/VS-2022-1750-Preview-2-C20-modules-b/10229203#T-N10250784)
- `/d2cgsummary` and `/d1reportTime`
  - [Slow to Compile Table Initializers](https://aras-p.info/blog/2017/10/24/Slow-to-Compile-Table-Initializers/)
  - [Best unknown MSVC flag: d2cgsummary](https://aras-p.info/blog/2017/10/23/Best-unknown-MSVC-flag-d2cgsummary/)
  - [Another cool MSVC flag: /d1reportTime](https://aras-p.info/blog/2019/01/21/Another-cool-MSVC-flag-d1reportTime/)
- `/d1reportAllClassLayout` `/d1reportSingleClassLayout<name>`
  - [/d1reportAllClassLayout – Dumping Object Memory Layout](https://ofekshilon.com/2010/11/07/d1reportallclasslayout-dumping-object-memory-layout/)
  - [Diagnosing Hidden ODR Violations in Visual C++ (and fixing LNK2022)](https://devblogs.microsoft.com/cppblog/diagnosing-hidden-odr-violations-in-visual-c-and-fixing-lnk2022/)
  - [Add tools to display c++ class memory layout](https://developercommunity.visualstudio.com/t/Add-tools-to-display-c-class-memory-la/392536)
