---
layout: post
title: "Conditional Probability"
author: "yinfinited"
categories: 'Statistics'
tags: ['stat']
typora-root-url: ../
---

## Conditional Probability

표본공간을 S 라고 하고 그 부분집합인 어떤 사상을 A 라고 하면, 그 확률은 아래와 같다.

$$
P(A) = \frac{n(A)}{n(S)}
$$

이때 다른 사상 B가 이미 발생했다는 사실을 알고 있다면, 이 시점에서 사상 A 의 확률은 B 에 대한 조건부 확률로 정의된다.

$$
P(A|B)
$$

위 식에서 `|` 오른쪽은 이미 그 결과를 알고 있는 사상이다.

조건부 확률을 계산하기 위해서는 기존 확률 식에서 분모를 전체 표본공간이 아닌 조건이 되는 사상으로 바꾸고, 분자는 조건이 되는 사상과의 교집합으로 바뀐다.

$$
P(A|B) = \frac{P(A \cap B)}{P(B)}
$$

실생활에서는 조건부확률을 더 쉽게 알수 있는 경우도 있어서 



