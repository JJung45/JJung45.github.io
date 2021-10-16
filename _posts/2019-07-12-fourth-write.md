---
layout: post
title: "데이터베이스 테이블 옮기기"
date: 2019-07-12 12:40:43
image: '/assets/img/'
description: 'company'
tags:
- php
- mysql
categories:
- php
- mysql
---

오늘 회사에서 데이터를 A라는 데이터베이스 A-1테이블에서 B라는 데이터베이스 B-1테이블로 옮겨야하는 경우가 생겼다.
걸리는 사항들이 몇 개 있었는데,

1. A-1테이블과 B-1테이블의 컬럼이 다름.
2. A-1테이블의 가장 뒤에서부터(가장 최근의 것) 500개의 데이터를 뽑아와야 함.
3. A-1테이블에서 B-1테이블로 옮긴 후 옮긴 데이터는 B-1테이블에서 삭제해야함.

생각해보면 간단한 건데 insert 한 후 insert한 idx값들을 가지고 바로 그 idx값을 지워야 한다고만 생각했다...

````
결론:

insert into A-1(code, coupon_idx, expiry_date, entry_date) select code, 2, '2020-08-31', now() from B-1 where user_id is null order by id desc limit 500;

delete from B-1 where code in (select code from A-1 where entry_date >= '2019-07-11' and coupon_idx = 2);
````
