---
layout: post
title: "Information Quantity"
author: "yinfinited"
categories: 'ML'
tags: ['information theory']
typora-root-url: ../
---

## Information Quantity

언론에서 일반적인 사실과 뉴스를 설명할 때 자주 인용하는 말이 있다.

> 개가 사람을 물면 뉴스가 아니지만 사람이 개를 물면 뉴스가 된다. 

우연인지는 몰라도 정보 이론에서 위와 동일한 방법으로 정보량이라는 것을 정의한다. 발생확률이 낮은 사건은 정보량이 적고, 발생확률이 높은 사건은 정보량이 많다고 보는 것이다. 

마침 음의 로그 함수가 이러한 정보량의 정의에 부합하는 형태였고, 사건 $x$ 의 발생확률 $P(x)$ 를 이용하여  정보량 $I$ 을 아래와 같이 정의한다.
$$
I(x) = - \log P(x)
$$
그래프를 그려보면 아래와 같다.

![](/assets/img/information-quantity-plot.png)



가로축은 $P(x)$, 세로축은 $I(x)$ 가 된다. $P(x)$ 가 확률이므로 [0, 1] 사이에서 정의되기 때문에 나머지 영역은 볼 필요가 없다. 

발생확률이 0 에 가까울 수록 정보량은 무한대가 되며, 발생확률이 1이면 정보량이 0 인 것을 확인할 수 있다.

발생확률에 따른 정보량의 변화가 로그의 밑을 무엇으로 사용하느냐에 따라 약간 차이가 있는데, 2 를 사용하면 섀넌, 자연상수($e$) 를 사용하면 네트(nat) 라고 한다.

## Reference

- https://ratsgo.github.io/statistics/2017/09/22/information/