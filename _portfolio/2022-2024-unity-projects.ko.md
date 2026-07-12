---
title: "Unity Technologies 프로젝트"
excerpt: "2022-2024: Digital Twin & Industry 팀"
project_type: Professional
classes: wide
date: 2022-08-01
lang: ko
permalink: /portfolio/2022-2024-unity-projects/
header:
  teaser: /assets/images/unity-employment/unity-logo-teaser.png
sidebar:
  - image: /assets/images/unity-employment/unity-logo.svg
    text: "<p><b>2022년 8월 - 2024년 4월</b></p><p><b>시니어 소프트웨어 엔지니어</b></p><p><b>Experience Engineering Team</b> - 자동차, 제조, 리테일, 헬스케어 등 산업군을 위한 실시간 3D 애플리케이션 개발</p>"
gallery:
  - url: /assets/images/unity-employment/lg-meta-slap1.gif
    image_path: assets/images/unity-employment/lg-meta-slap1.gif
  - url: /assets/images/unity-employment/lg-meta-slap2.gif
    image_path: assets/images/unity-employment/lg-meta-slap2.gif
  - url: /assets/images/unity-employment/lg-meta-slap3.gif
    image_path: assets/images/unity-employment/lg-meta-slap3.gif
  - url: /assets/images/unity-employment/lg-meta-slap4.gif
    image_path: assets/images/unity-employment/lg-meta-slap4.gif
  - url: /assets/images/unity-employment/lg-meta-slap5.gif
    image_path: assets/images/unity-employment/lg-meta-slap5.gif
---

**참고:** 아래 프로젝트는 클라이언트 업무였기 때문에, 공개된 프로젝트만 스크린샷/영상을 포함합니다.
{: .notice--info}

## LG Meta Slap

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/unity-employment/lg-meta-slap6.avif" style="width: 40%" class="align-right"/>

**기간:** 2022년 8월 - 2023년 2월<br />
**플랫폼:** Windows & Mac<br />
**역할:** Unity 엔지니어<br />
**엔지니어:** 4명<br />
**설명:** COVID-19 기간에 개발된 가상 오피스 "메타버스" 애플리케이션

[Unity 블로그: LG U+ fosters real connections for virtual offices](https://unity.com/blog/industry/lg-u-plus-fosters-connections-for-virtual-offices)

{% include gallery %}

**주요 기여:**
- [SendBird](https://sendbird.com/docs/chat/sdk/v4/unity/getting-started/send-first-message) 기반 인앱 메신저 구현 (사실상 카카오톡 유사 기능)
  - 스크롤 기반 메시지 히스토리 점진 로딩
  - 만료 정책이 있는 파일/이미지 업로드
  - 1:1 및 그룹 채팅
  - 사용자 프로필, 즐겨찾기, 멘션 자동완성
- [Agora](https://www.agora.io/en/blog/agora-video-sdk-for-unity-quick-start-programming-guide/) 기반 영상/음성 채팅 구현
- Windows/Mac 네이티브 플러그인 구현
  - 파일 선택/저장 다이얼로그
  - 윈도우 리사이즈 및 Always-on-top
- AWS API 호출을 커스텀 백엔드 API로 교체
- Unity Analytics 연동

## 앱 최적화 - Project Makeover

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/unity-employment/project-makeover.webp" style="width: 40%" class="align-right"/>


**기간:** 2023년 2월 - 2023년 4월<br />
**플랫폼:** Android<br />
**역할:** Unity 엔지니어<br />
**엔지니어:** 3명<br />
**설명:** 애플리케이션 전체를 프로파일링하고 가능한 많은 최적화를 적용하는 것이 목표인 프로젝트

[Google Play의 Project Makeover](https://play.google.com/store/apps/details?id=com.bgg.jump&hl=en)

**주요 기여:**
- GC 감소 (클로저, 박싱, 임시 할당 등)
- 오디오/텍스처 저장 공간 절감
- 설정값 및 캐싱 기반 로딩 속도 개선

## 멀티플레이어 게임

**기간:** 2023년 4월 - 2023년 7월<br />
**플랫폼:** Windows<br />
**역할:** .NET 백엔드 엔지니어<br />

**주요 기여:**
- 기본 플레이어 매칭 구현
- 실제 외부 의존성과 교체 가능한 Mock .NET 백엔드 서비스 개발 (결정적 테스트를 위해 중요); 이 mock 서비스에는 RPC 및 Redis 사용 포함
- 코드 커버리지 및 CI 개선으로 회귀/엣지 케이스를 조기에 포착해 안정성 향상

## NUHS Holomedicine

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/unity-employment/nuhs-holomedicine.png" style="width: 40%" class="align-right"/>

**기간:** 2023년 7월 - 2023년 9월<br />
**플랫폼:** Microsoft HoloLens 2<br />
**역할:** Unity 엔지니어<br />
**엔지니어:** 4명<br />
**설명:** 싱가포르 [National University Health System](https://www.nuhs.edu.sg/) 대상 프로젝트로, [Mixed Reality Toolkit (MRTK)](https://learn.microsoft.com/en-us/windows/mixed-reality/mrtk-unity/mrtk3-overview/)를 활용.

**주요 기여:**
- Burst + Unity Job System 기반 고성능 필터링 구현
- 초음파(ultrasound) 사용자 플로우 구현
  - 사용자가 큐보이드를 이동/회전/스케일하도록 안내하고 의료 핸드헬드 장치로 내부 스캔
  - 월드 좌표를 큐보이드 좌표계로 변환
  - 스캔 데이터 gRPC로 백엔드 전송
  - 3D 메시 재구성 결과를 비동기로 기다리는 동안 로딩 인디케이터 표시
- 에디터에서 XR 상호작용(버튼 클릭, 큐보이드 조작 등)을 시뮬레이션하는 Play Mode 테스트 구현

<iframe src="https://www.linkedin.com/embed/feed/update/urn:li:ugcPost:7114952710122049536?compact=1" height="399" width="504" frameborder="0" allowfullscreen="" title="Embedded post"></iframe>

## 위성 모니터링 프로토타입

**기간:** 2023년 10월 - 2023년 11월<br />
**플랫폼:** Windows<br />
**역할:** Unity 엔지니어<br />
**엔지니어:** 1명 (및 TA 1명)

**주요 기여:**
- 카메라 컨트롤 구현 (지구 모델 회전, 확대/축소)
- 일식(eclipse) 방정식을 활용한 결정적 궤도 구현 및 TA가 조정 가능한 프로퍼티 제공
  - 초기에는 Splines 패키지를 사용했지만 비효율적이어서 대체
- 위성이 파편/다른 위성과 너무 가까워지면 알림을 트리거하고, 충돌 예측 시뮬레이션 모드로 전환
- 항상 카메라를 바라보는 쿼드를 수천 개 렌더링하고 무작위 궤도로 지구를 공전시키는 Compute Shader 작성

## 스마트 시티 프로젝트

**기간:** 2023년 11월 - 2024년 2월<br />
**플랫폼:** Windows & Mac<br />
**역할:** Unity 엔지니어<br />
**엔지니어:** 2명<br />
**설명:** 건물 방문자, 매출, 날씨, 인구 등 도시 데이터를 시각화. Day/Night 시스템, 비/구름, 히트맵, 월드 스페이스 UI, 포인트 클라우드 등 다양한 시각화 포함.

**주요 기여:**
- UI Toolkit 기반 커스텀 에디터 윈도우 개발
  - CSV 데이터를 파싱/필터링/변환하여 바이너리로 저장하고 런타임에서 빠르게 읽을 수 있는 임포터 설계
  - Unity의 [Background Tasks Window](https://docs.unity3d.com/6000.2/Documentation/Manual/BackgroundTasksWindow.html)와 [Progress API](https://docs.unity3d.com/6000.2/Documentation/ScriptReference/Progress.html)를 활용해 비동기 임포트 구현; 최대 10GB CSV로 테스트
- 시뮬레이션 재생 기능 구현: 캘린더 피커로 날짜 범위를 선택하고 재생/일시정지 버튼 및 슬라이더로 시뮬레이션
  - 두 날짜 범위를 나란히 비교하는 분할 화면 모드도 구현
- [MemoryMappedFile API](https://learn.microsoft.com/en-us/dotnet/standard/io/memory-mapped-files)와 저수준 코드를 활용해 전체 바이너리를 메모리에 올리지 않고 특정 데이터 범위만 참조
- 커스텀/미니멀 DI 적용으로 프로젝트 내 싱글턴 0개 유지
- 단위/통합 테스트로 데이터 임포트 및 런타임 데이터 표시 버그 조기 발견

## ADAS HMI 프로젝트

**기간:** 2024년 2월 - 2024년 4월<br />
**플랫폼:** Windows<br />
**역할:** Unity 엔지니어<br />
**엔지니어:** 3명<br />
**태그:** [Advanced Driver-Assistance System](https://en.wikipedia.org/wiki/Advanced_driver-assistance_system) | [Human-Machine Interface](https://en.wikipedia.org/wiki/User_interface)<br />
**설명:** 프로젝트 중반에 에디터 툴링 지원을 위해 합류했습니다. 이 프로젝트의 2단계에 대한 더 자세한 내용은 제가 리드 엔지니어로 참여한 [여기](../2024-2025-capgemini-projects)에서 확인할 수 있습니다.

**주요 기여:**
- IMGUI와 UI Toolkit을 모두 활용한 커스텀 에디터 윈도우 개발
  - 데이터 아이템 추가/삭제/수정 및 ScriptableObject 저장
  - 여러 에디터 윈도우 간 통신 처리 (트리 뷰 기반 마스터-디테일 UI)
