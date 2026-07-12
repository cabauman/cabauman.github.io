---
title: "오픈 소스 기여 모음"
excerpt: "주요 오픈 소스 저장소 기여 사례"
project_type: Personal
#classes: wide
toc: true
toc_sticky: true
lang: ko
permalink: /portfolio/open-source-contributions/
header:
  teaser: /assets/images/open-source/open-source.webp
sidebar:
  - title: "주요 기여"
    image: /assets/images/open-source/open-source.webp
  #- nav: portfolio
---

## Oh My Posh Unity Segment

[Website](https://ohmyposh.dev/){: .btn .btn--success}

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/open-source/ohmyposh-unity-segment1.png"/>

**Tags:** Go

> Oh My Posh는 다양한 "segment"를 조합해 현재 폴더, 사용자 정보, git 상태 등 컨텍스트를 표시하는 커스텀 프롬프트 엔진입니다.

Unity Engine을 자주 사용하고 oh-my-posh를 선호해서, 현재 작업 디렉터리의 Unity/C# 버전을 표시하는 커스텀 segment를 기여했습니다. 이때 처음으로 Go를 본격 사용했습니다.

[Unity Segment Docs](https://ohmyposh.dev/docs/segments/cli/unity)

[GitHub PRs](https://github.com/JanDeDobbeleer/oh-my-posh/pulls?q=is%3Apr+is%3Aclosed+author%3Acabauman)

## Versionize

[GitHub](https://github.com/versionize/versionize){: .btn .btn--info} [NuGet](https://www.nuget.org/packages/Versionize){: .btn .btn--primary}

> Conventional Commit 메시지를 이용한 자동 버전 관리 및 CHANGELOG 생성 도구

**Tags:** C#, conventional commits

- 코어 메인테이너 2명 중 1명으로 활동
- 다른 메인테이너가 원 제작자이고, 저는 이후 합류

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/open-source/versionize1.png" />

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/open-source/versionize2.png" />

## ReactiveUI

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/open-source/reactiveui-logo.png" class="align-right" />

[GitHub](https://github.com/reactiveui/reactiveui){: .btn .btn--info} [Website](https://www.reactiveui.net/){: .btn .btn--success}

**Tags:** C#, Rx.NET, iOS, Android, UWP, WPF

약 2018년부터 2022년까지 [core maintainer](https://github.com/reactiveui/ReactiveUI#core-team)로 활동했습니다. 코드 기여뿐 아니라 ReactiveUI Slack 지원, [Stack Overflow](https://stackoverflow.com/users/5984310/colt-bauman?tab=answers) 답변 활동도 수행했습니다.

[PRs](https://github.com/reactiveui/ReactiveUI/pulls?q=is%3Apr+is%3Aclosed+author%3Acabauman)
- [fix(memory leak): original view model is not released when swapped out](https://github.com/reactiveui/ReactiveUI/pull/2504)
- [fix(threading): RxApp scheduler logic makes unit tests unpredictable](https://github.com/reactiveui/ReactiveUI/pull/2496)

## PropertyChanged

[NuGet](https://www.nuget.org/packages/ReactiveMarbles.PropertyChanged){: .btn .btn--primary}

**Tags:** C#, Rx.NET

[성능 및 벤치마크 PR](https://github.com/reactivemarbles/PropertyChanged/pulls?q=is%3Apr+is%3Aclosed+author%3Acabauman)

{% include video id="dLqqcMDGi1o" provider="youtube" %}

## H5P-Nodejs-library

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/open-source/h5p-logo.png" style="width: 30%" class="align-right" />

**Tags:** H5P, NodeJS, TypeScript, S3, MongoDB

KidsLoop에서 백엔드 엔지니어로 근무할 때 실제로 사용하던 라이브러리여서 기여했습니다.

> 이 TypeScript 라이브러리는 NodeJS 기반 커스텀 H5P 서버 구축에 필요한 기능을 제공합니다.

[2 Contributions](https://github.com/Lumieducation/H5P-Nodejs-library/pulls?q=is%3Apr+is%3Aclosed+author%3Acabauman)
- fix(h5p-mongos3): s3 lifecycle helper not taking effect
- perf(h5p-server): reduce memory and IO when uploading package

## .NET-Ogg-Vorbis-Encoder

[NuGet](https://www.nuget.org/packages/OggVorbisEncoder){: .btn .btn--primary}

**Tags:** C#, Vorbis

[대규모 성능 개선 PR](https://github.com/SteveLillis/.NET-Ogg-Vorbis-Encoder/pull/11)

**Before**

|         Method |    Mean |    Error |   StdDev | Allocated |
|--------------- |--------:|---------:|---------:|----------:|
| ConvertPCMFile | 4.174 s | 0.0828 s | 0.1835 s | 608.78 MB |

**After**

|         Method |    Mean |    Error |   StdDev | Allocated |
|--------------- |--------:|---------:|---------:|----------:|
| ConvertPCMFile | 1.605 s | 0.0374 s | 0.1073 s | 162.53 MB |

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/open-source/ogg-vorbis-encoder1.png" />

- IList 파라미터를 구체 타입(array, OffsetArray)으로 변경
- OffsetArray 대신 Span<T> 활용
- stackalloc 및 MemoryPool 최적화 추가

작은 크기의 임시 배열은 힙이 아닌 스택에 할당하고, 큰 경우에는 풀에서 대여 후 필요한 범위만 slice해서 사용했습니다.

```csharp
float[] seedArr = null;
Span<float> seed = _totalOctaveLines <= 128
    ? stackalloc float[_totalOctaveLines]
    : (seedArr = ArrayPool<float>.Shared.Rent(_totalOctaveLines));

seed = seed.Slice(0, _totalOctaveLines);
```
