---
title: "GPU Instancing & Compute Shader 데모"
excerpt: "2023: GPU instancing 및 compute shader 데모"
project_type: Personal
lang: ko
permalink: /portfolio/2023-gpu-instancing/
header:
  teaser: /assets/images/gpu-instancing/gpu-instancing-orbit.png
sidebar:
  - title: "상세 정보"
    image: /assets/images/gpu-instancing/gpu-instancing-orbit.png
    text: "- 팀 규모: 1\n- 플랫폼: Windows\n- 기술: Unity, URP"
  #- nav: portfolio
---

<a href="{{ site.url }}{{ site.baseurl }}/assets/images/gpu-instancing/gpu-instancing-inspector.png">
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/gpu-instancing/gpu-instancing-inspector.png" style="width: 40%" class="align-right"/>
</a>

기능
- 100만 개 이상의 쿼드 렌더링 가능
- [Graphics.RenderMeshPrimitives](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/Graphics.RenderMeshPrimitives.html) API 사용
- 빌보딩 on/off 지원(메시가 항상 카메라를 바라보도록 설정 가능)
- 위치/회전을 compute shader에서 갱신
- 렌더 영역 bounds를 전달해 프러스텀 컬링 적용
- 구(sphere) 내부 랜덤 포인트 및 랜덤 회전축 생성
- 속도/크기 리스트에서 랜덤 선택

{% include video id="l0RC5X2zB3Y" provider="youtube" %}
