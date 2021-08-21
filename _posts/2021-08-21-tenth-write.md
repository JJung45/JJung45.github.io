---
layout: post
title: "쓰로틀링"
date: 2021-08-21 09:08:00
image: '/assets/img/'
description: 'throttling'
tags:
- throttling
categories:
- throttling
---

## 쓰로틀링이란?


### 정의

사용자가 특정 기간에 만들 수 있는 API 요청 수를 제한하는 프로세스

### 목적

API를 사용하는 사용자의 수가 증가함에 따라 웹사이트 또는 모바일의 응용프로그램에서 성능 저하가 발생할 수도 있다. 따라서 더 나은 API 연결과 더 빠른 인터페이스를 통해 사용자에게 더 나은 경험을 줄 수 있다. 또한 사용자가 시간당 더 많은 요청이 필요한 경우 비용을 지불해야 하기 때문에 비용적인 측면에서도 필요한 기술이다.

### 계획

요청수 서버 처리 한도를 넘어섰을때, 클라이언트로 바로 429 에러응답을 주면, 초과 요청을 제출한 클라이언트도 빠른 실패 응답을 받을 수 있어, 실패에 대한 대응을 빠르게 처리할 수 있다. 또한, 요청 쓰레드가 밀려서 전체 사용자 응답이 느려지는것을 방지할 수 있다.

### 알고리즘

(1) Leaky Bucket API Throttling Algorithm

FIFO(선입 선출) 특정 크기를 가진 대기열을 사용하여 들어오는 요청을 보관한다. 새로운 API 호출/요청이 수신되면 대기열 끝에 추가된다. 일정한 간격으로 대기열의 앞쪽에서 요청을 제거하고 처리한다. 대기열이 이미 가득 찼을 때 새 요청이 오면 요청이 삭제된다.

(2) Fixed Window API Throttling Algorithm

고정된 기간은 특정 기간에 사용자로부터 N개의 API 호출을 허용한다. 시간 창이 끝나기 전에 카운터가 상한에 도달하면 새 요청이 거부된다. 1분이 시작될 때 카운터가 0으로 재설정된다.

(3) Sliding Window API Throttling Algorithm

요청이 생성될 때 시간 창을 시작하여  Fixed Window API Throttling Algorithm 의 요청 버스트 문제를 해결한다. 사용자가 실제로 첫 번째 요청을 했을 때만 기간이 시작된다. 첫 번째 요청의 타임스탬프는 카운터와 함께 저장되며 사용자는 그 시간 안에 한 번 더 요청할 수 있다.

참고) [https://www.tibco.com/reference-center/what-is-api-throttling](https://www.tibco.com/reference-center/what-is-api-throttling)
