---
title: "Breakout 클론"
excerpt: "2018: 채용 과제(5일)"
project_type: Personal
github: https://github.com/cabauman/UnityBreakoutGame
lang: ko
permalink: /portfolio/2018-breakout/
header:
  teaser: /assets/images/breakout/screen04.png
sidebar:
  - title: "상세 정보"
    image: /assets/images/breakout/screen04.png
    text: "- 팀 규모: 1\n- 플랫폼: Windows\n- 기술: Unity, UniRx"
  #- nav: portfolio
gallery:
  - url: /assets/images/breakout/screen01.png
    image_path: assets/images/breakout/screen01.png
  - url: /assets/images/breakout/screen02.png
    image_path: assets/images/breakout/screen02.png
  - url: /assets/images/breakout/screen03.png
    image_path: assets/images/breakout/screen03.png
---

Unity + UniRx로 5일 동안 만든 Breakout 클론입니다. KidsLoop의 Unity 소프트웨어 엔지니어 채용 과정에서 받은 과제를 바탕으로 만들었습니다. 이 프로젝트에서는 리액티브 프로그래밍과 MVP(Model-View-Presenter) 패턴을 결합해 보는 것이 목표였습니다. 핵심 오브젝트(공, 패들, 벽돌 등)는 `MonoBehaviour` 기반 Presenter와 Presenter가 참조하는 [POCO](https://en.wikipedia.org/wiki/Plain_old_CLR_object) 모델로 분리해 구성했습니다.

[소스 코드](https://github.com/cabauman/UnityBreakoutGame){: .btn .btn--info}

{% include video id="PfqgqGX2Nrg" provider="youtube" %}

{% include gallery %}

다음은 MVP + 리액티브 스타일의 예시입니다.

{% highlight csharp linenos %}
using UniRx;

public class Paddle
{
    public Paddle()
    {
        Width = new ReactiveProperty<float>(1);
        ResetBallPos = new ReactiveCommand<Unit>();
    }

    public IReactiveProperty<float> Width { get; }

    public ReactiveCommand<Unit> ResetBallPos { get; }
}
{% endhighlight %}

{% highlight csharp linenos %}
using UniRx;
using UnityEngine;

public class PaddlePresenter : MonoBehaviour
{
    [SerializeField]
    private BallPresenter _ballPresenter;
    [SerializeField]
    private Transform _initialBallPosTrfm;
    [SerializeField]
    private Transform _graphicTrfm;

    public void Init()
    {
        Paddle = new Paddle();

        Observable
            .EveryUpdate()
            .Select(_ => Input.mousePosition)
            .Subscribe(UpdateXPosition)
            .AddTo(this);

        Paddle
            .Width
            .Subscribe(xScale => _graphicTrfm.localScale = new Vector3(xScale, _graphicTrfm.localScale.y))
            .AddTo(this);

        Paddle
            .ResetBallPos
            .Subscribe(_ => ResetBallPos())
            .AddTo(this);
    }

    public Paddle Paddle { get; private set; }

    private void UpdateXPosition(Vector3 mousePos)
    {
        mousePos.x = Mathf.Clamp(mousePos.x, 0, Screen.width);
        var xPos = Camera.main.ScreenToWorldPoint(mousePos).x;
        transform.position = new Vector3(xPos, transform.position.y, transform.position.z);
    }

    private void ResetBallPos()
    {
        _ballPresenter.transform.parent = transform;
        _ballPresenter.transform.position = _initialBallPosTrfm.position;
    }
}
{% endhighlight %}
