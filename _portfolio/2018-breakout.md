---
title: "Breakout Clone"
excerpt: "2018: job interview take-home assignment (5 days)"
project_type: Personal
header:
  teaser: /assets/images/breakout/screen04.png
sidebar:
  - title: "Details"
    image: /assets/images/breakout/screen04.png
    text: "- Team Size: 1\n- Platform: Windows\n- Tech: Unity, UniRx"
  #- nav: portfolio
gallery:
  - url: /assets/images/breakout/screen01.png
    image_path: assets/images/breakout/screen01.png
  - url: /assets/images/breakout/screen02.png
    image_path: assets/images/breakout/screen02.png
  - url: /assets/images/breakout/screen03.png
    image_path: assets/images/breakout/screen03.png
---

This is a Breakout clone made in 5 days with Unity and UniRx. It was a programming task assigned to me as part of the hiring process for a Unity software engineer position at a KidsLoop. For this project I thought it would be fun to combine reactive programming and the model-view-presenter (MVP) pattern. So all key objects (ball, paddle, brick, etc.) are represented by both a MonoBehaviour-derived presenter and a [POCO](https://en.wikipedia.org/wiki/Plain_old_CLR_object) model which the presenter references.

[Source Code](https://github.com/cabauman/UnityBreakoutGame){: .btn .btn--info}

{% include video id="PfqgqGX2Nrg" provider="youtube" %}

{% include gallery %}

Here's an example of the MVP + reactive programming style:

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
