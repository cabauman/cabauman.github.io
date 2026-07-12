---
title: "Capgemini Engineering 프로젝트"
excerpt: "2024-2025: Digital Twin & Industry 팀"
project_type: Professional
#classes: wide
date: 2024-05-01
lang: ko
permalink: /portfolio/2024-2025-capgemini-projects/
header:
  teaser: /assets/images/capgemini/capgemini_logo_teaser.png
sidebar:
  - image: /assets/images/capgemini/capgemini_logo.png
    text: "<p><b>2024년 5월 - 2025년 4월</b></p><p><b>시니어 소프트웨어 엔지니어</b></p><p><b>Experience Engineering Team</b> - 자동차, 제조, 리테일, 헬스케어 등 산업군을 위한 실시간 3D 애플리케이션 개발</p>"
---

**참고:** 아래 클라이언트 프로젝트는 공개되지 않아 스크린샷/영상을 포함할 수 없습니다.
{: .notice--info}

## ADAS HMI 프로젝트

**기간:** 2024년 8월 - 2025년 5월<br />
**플랫폼:** Windows<br />
**역할:** 리드 엔지니어<br />
**엔지니어:** 2명<br />
**엔진:** Unreal 5.3<br />
**태그:** [Advanced Driver-Assistance System](https://en.wikipedia.org/wiki/Advanced_driver-assistance_system) | [Human-Machine Interface](https://en.wikipedia.org/wiki/User_interface)

**배경**

이 프로젝트는 Unity Technologies 시절에 진행했던 프로젝트의 2단계입니다(팀이 Capgemini로 이관되기 전). 1단계는 Unity로 개발되었지만, 2단계에서는 고객 요구로 Unreal Engine 포팅이 필요했습니다. 당시 엔지니어는 저 한 명뿐이었고, Unreal Engine은 대학 이후 오랜만이었습니다. 계약 세부 조율 기간 동안 Unreal과 C++ 감각을 빠르게 되살리는 데 집중했고, 첫 과업은 사실상 Unity 프로젝트를 Unreal로 복제하는 것이었습니다. 두 단계 모두 최종 납품물은 빌드가 아닌 에디터 프로젝트였기 때문에, 런타임 기능뿐 아니라 커스텀 에디터 툴링도 필수였습니다. 약 4개월 후에 추가 엔지니어 1명이 합류했습니다.

**요약**

이 프로젝트의 런타임 핵심은 차량에서 ECU(전자 제어 장치) 측정값을 읽어 RT3D 시뮬레이션으로 시각화하는 것입니다. 에디터 툴링 측면에서는 특정 신호 수신 시 어떤 에셋을 표시할지 사용자가 직접 커스터마이즈할 수 있도록 했습니다.

**용어 정리**

[CAN](https://en.wikipedia.org/wiki/CAN_bus) - Controller Area Network: 차량 및 기타 시스템 내 전자 제어 장치(ECU) 간 통신을 가능하게 하는 메시지 기반 프로토콜

[Vector CANoe](https://www.vector.com/int/en/products/products-a-z/software/canoe/#): 자동차 산업에서 버스 시스템 분석/시뮬레이션에 사용되는 도구

[COM](https://en.wikipedia.org/wiki/Component_Object_Model) – Component Object Model: 서로 다른 소프트웨어 컴포넌트 간 통신을 위한 Microsoft 표준. 서로 다른 언어로 구현된 컴포넌트도 상호 운용 가능.

CANoe COM Server: CANoe와 연동/상호작용하는 자체 애플리케이션 또는 컴포넌트를 작성할 수 있도록 지원 ([API 가이드](https://cdn.vector.com/cms/content/know-how/_application-notes/AN-AND-1-117_CANoe_CANalyzer_as_a_COM_Server.pdf))

**API 통합**

1단계에서는 Vector CANoe의 C# COM dll을 사용했지만, 2단계에서는 C/C++ COM API로 전환이 필요했습니다. 그래서 첫 번째 과업이 Unreal에 해당 API를 통합하는 일이었습니다.

C++에서 CANoe 애플리케이션을 시작하면 호출 스레드가 약 15초 동안 블로킹되므로, Unreal의 [AsyncTask](https://dev.epicgames.com/documentation/en-us/unreal-engine/API/Runtime/Core/Async/AsyncTask)를 사용해 헬퍼 스레드에서 실행하고 완료 시 GameThread로 콜백하도록 구현했습니다. 이 과정에서 애니메이션 로딩 인디케이터를 표시했습니다.

```c++
AsyncTask(ENamedThreads::AnyThread, [this, OnCompleted]()
{
    OpenCANoe();

    AsyncTask(ENamedThreads::GameThread, [this, OnCompleted]()
    {
        InitializeCANoeOnMainThread();
        OnCompleted.ExecuteIfBound();
    });
});
```

**주요 기여**

추정 C++ vs Blueprint 사용 비율: 80% - 20%

- Slate 및 Editor Utility Widgets를 사용한 커스텀 에디터 윈도우 개발
- Unreal 로컬라이제이션 시스템으로 커스텀 에디터 윈도우 다국어화 (한국어/영어)
- CAN 시그널 관리의 "single source of truth"로 데이터 테이블 사용
- 테스트용 CSV 읽기/쓰기 "시나리오 에디터" 툴 개발
  - 3개 컬럼: signal name, timestamp, value
- C++ COM API 통합용 Unreal Plugin 제작
- CANoe API를 인터페이스 뒤로 추상화하여 CANoe 소프트웨어 접근이 없을 때 mock 구현으로 대체 가능하도록 설계
- Widget 및 Actor 풀링 적용
