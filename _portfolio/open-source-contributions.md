---
title: "Various Open Source Contributions"
excerpt: "Some notable contributions to open source repositories"
project_type: Personal
#classes: wide
toc: true
toc_sticky: true
header:
  teaser: /assets/images/open-source/open-source.webp
sidebar:
  - title: "Notable Contributions"
    image: /assets/images/open-source/open-source.webp
  #- nav: portfolio
---

## Oh My Posh Unity Segment

[Website](https://ohmyposh.dev/){: .btn .btn--success}

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/open-source/ohmyposh-unity-segment1.png"/>

**Tags:** Go

> Oh My Posh is a custom prompt engine for any shell that is structured around the concept of "segments", which renders a single context like showing the current folder, user information or git status when relevant.

Because I frequently use Unity Engine and am a fan of the oh-my-posh terminal extension, I decided to contribute a custom *segment* that displays the Unity version and C# version of the current working directory. This was my first time using Go.

[Unity Segment Docs](https://ohmyposh.dev/docs/segments/cli/unity)

[GitHub PRs](https://github.com/JanDeDobbeleer/oh-my-posh/pulls?q=is%3Apr+is%3Aclosed+author%3Acabauman)

## Versionize

[GitHub](https://github.com/versionize/versionize){: .btn .btn--info} [NuGet](https://www.nuget.org/packages/Versionize){: .btn .btn--primary}

> Automatic versioning and CHANGELOG generation, using conventional commit messages

**Tags:** C#, conventional commits

- I'm one of two core maintainers.
- The other developer was the original creator and I joined on later.

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/open-source/versionize1.png" />

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/open-source/versionize2.png" />

## ReactiveUI

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/open-source/reactiveui-logo.png" class="align-right" />

[GitHub](https://github.com/reactiveui/reactiveui){: .btn .btn--info} [Website](https://www.reactiveui.net/){: .btn .btn--success}

**Tags:** C#, Rx.NET, iOS, Android, UWP, WPF

I was a [core maintainer](https://github.com/reactiveui/ReactiveUI#core-team) from about 2018 to 2022. This includes code contributions, providing support in the ReactiveUI Slack channel and answering questions on [Stack Overflow](https://stackoverflow.com/users/5984310/colt-bauman?tab=answers).

[PRs](https://github.com/reactiveui/ReactiveUI/pulls?q=is%3Apr+is%3Aclosed+author%3Acabauman)
- [fix(memory leak): original view model is not released when swapped out](https://github.com/reactiveui/ReactiveUI/pull/2504)
- [fix(threading): RxApp scheduler logic makes unit tests unpredictable](https://github.com/reactiveui/ReactiveUI/pull/2496)

## PropertyChanged

[NuGet](https://www.nuget.org/packages/ReactiveMarbles.PropertyChanged){: .btn .btn--primary}

**Tags:** C#, Rx.NET

[Performance and benchmark PRs](https://github.com/reactivemarbles/PropertyChanged/pulls?q=is%3Apr+is%3Aclosed+author%3Acabauman)

{% include video id="dLqqcMDGi1o" provider="youtube" %}

## H5P-Nodejs-library

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/open-source/h5p-logo.png" style="width: 30%" class="align-right" />

**Tags:** H5P, NodeJS, TypeScript, S3, MongoDB

I contributed this repository while working as a backend engineer at KidsLoop because we were using this library.

> This TypeScript library provides everything needed to create custom H5P servers running on NodeJS.

[2 Contributions](https://github.com/Lumieducation/H5P-Nodejs-library/pulls?q=is%3Apr+is%3Aclosed+author%3Acabauman)
- fix(h5p-mongos3): s3 lifecycle helper not taking effect
- perf(h5p-server): reduce memory and IO when uploading package

## .NET-Ogg-Vorbis-Encoder

[NuGet](https://www.nuget.org/packages/OggVorbisEncoder){: .btn .btn--primary}

**Tags:** C#, Vorbis

[Major Performance Improvement PR](https://github.com/SteveLillis/.NET-Ogg-Vorbis-Encoder/pull/11)

**Before**

|         Method |    Mean |    Error |   StdDev | Allocated |
|--------------- |--------:|---------:|---------:|----------:|
| ConvertPCMFile | 4.174 s | 0.0828 s | 0.1835 s | 608.78 MB |

**After**

|         Method |    Mean |    Error |   StdDev | Allocated |
|--------------- |--------:|---------:|---------:|----------:|
| ConvertPCMFile | 1.605 s | 0.0374 s | 0.1073 s | 162.53 MB |

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/open-source/ogg-vorbis-encoder1.png" />

- Change IList parameters to concrete types (array and OffsetArray)
- Use Span<T> instead of OffsetArray
- Add stackalloc and MemoryPool optimizations

Allocate temporary arrays on the stack instead of the heap when the size is small enough. Otherwise, use a pool and slice it to the needed size.

```csharp
float[] seedArr = null;
Span<float> seed = _totalOctaveLines <= 128
    ? stackalloc float[_totalOctaveLines]
    : (seedArr = ArrayPool<float>.Shared.Rent(_totalOctaveLines));

seed = seed.Slice(0, _totalOctaveLines);
```
