---
layout: post
title: "5번째로 쓰는 글"
date: 2019-12-05 1:23:14
image: '/assets/img/'
description: 'company'
tags:
- php
---
<br>
...기록할 게 많았는데... 귀찮다는 핑계로 미뤄버렸다 계속 ㅠㅠ
이번에는 대용량 데이터를 DB에 직접 밀어넣는 작업을 해봤다. 
간단하지만 직접 밀어넣는 작업은 처음해봤기에 헤맸는데 결국 처리했다.
<br><br>

````
load data local infile 'path/file_name.csv' into table `DB_name` character set utf8
    fields terminated by ','
    enclosed by '"'
    lines terminated by '\n'
    ignore 1 lines
    (@code)
set field_1 = @code,
    field_2 = 3,
    field_3 = 0
````

``load data local infile``<br>
-> 텍스트 파일을 읽어 테이블에 인서트<br><br>
``character set utf8``<br>
-> 한글로 된 데이터를 위해 필요.
``termiated by``<br>
-> 각 필드 구분 문자(csv라면 컴마)<br><br>
``ignore 1 lines``<br>
-> 제목이 포함된 첫줄은 생략<br><br>
``(@code) ,field1 = @code``<br>
-> 특정 열(code)을 특정 컬럼에 넣음.

이렇게 성공을 했지만 직접적으로 DB에 넣는 것에 대한 위험성은 없을까라는
고민을 하게 되었고 간단히 장단점에 대해 찾아보았다.

장점: Batch 방식을 쓰는 것보다 빠르다. <br>
단점: 대용량의 csv를 밀어 넣을 때, 부하에 대한 컨트롤이 힘들다. 
하지만 csv를 잘게 쪼개서 넣으면 DB부하를 최소화할 수 있다.

* Batch방식 : insert를 Add시킨 후, 한번에 커밋하는 방식