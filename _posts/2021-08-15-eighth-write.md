---
layout: post
title: "엘라스틱서치 기본 개념"
date: 2021-08-15 1:23:14
image: '/assets/img/'
description: 'elasticSearch'
tags:
- elasticSearch
categories:
- elasticSearch
---

## ElasticSearch

확장성이 뛰어난 오픈소스 풀텍스트 검색 및 분석 엔진. 일반적으로 복잡한 검색 기능 및 요구 사항이 있는 애플리케이션을 위한 기본엔진/기술로 사용.

**역인덱스 구조로 저장**

- 인덱스 구조:

    id  → 내용

    1 → 오늘은 비가 왔다

    2 → 비가 오면 파전이 땡긴다.

- 역인덱스 구조:

    토근 → id

    오늘 → 1

    비 → 1,2

    파전 → 2,3

**클러스터**

![chapter_6](assets/img/chapter_7.png)

**도큐먼트**

저장의 기본 단위인 json개체. 관계형 데이터베이스와 비교하자면 테이블의 Row. 키와 값으로 정의된 필드들로 구성되어 있음. 키는 필드의 이름, 값은 String, Number, Boolean...

예약된 필드 : _index(document가 저장되어 있는 index정보), _type(document의 유형을 나타내는 정보), _id(document의 유니크한 고유한 값)

**타입**

document를 유형별로 모아놓은 집합. 관계형 데이터베이스와 비교해보자면 데이터베이스의 테이블.

**인덱스**

엘라스틱서치의 가장 큰 데이터 단위. 관계형 데이터베이스와 비교하자면 데이터베이스와 동일. 엘라스틱서치에서는 원하는 만큼의 index를 가질 수 있고, 각 index는 document를 보유.

유형:

- 샤드
단일 루씬 index. document제한이 없어 호스팅 서버의 제한을 초과하는 디스크 공간을 차지할 수 있음. 이럴 경우 발생하는 문제를 대응하기 위해 index의 데이터를 분산해서 저장하고 나뉜 조각들.
- 복제셋
index의 분산된 shared들을 복사한 것. 노드에 문제가 생길 떄 백업시스템으로 사용

**노드**

데이터를 저장하고 색인하는 등의 중요한 역할을 하는 엘라스틱서치 인스턴스
유형:
- Data Node : 데이터를 저장하거나 검색과 집계 등 데이터와 연관된 작업
- Master Node : 노드의 추가, 제거 등 클러스터의 관리 및 구성 작업 담당

-Ingestion Node : 색인 전 Document를 사전처리

-Machine Learning Node : 머신러닝 작업을 가능하게 하는 용도

**클러스터**

하나이상의 노드로 구성되어 있어야 함. 그 하나의 노드는 master node역할. 여러개의 node가 모여 하나의 시스템처럼 동작하게 하는 노드의 집합
