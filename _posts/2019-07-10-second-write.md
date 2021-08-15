---
layout: post
title: "2번째로 쓰는 글"
date: 2019-07-10 11:40:43
image: '/assets/img/'
description: 'laravel with mysql'
tags:
- laravel
- mysql
categories:
- laravel
- mysql
---

저번주부터 라라벨 토이 프로젝트를 실행하기 위해 migrate 명령어를 돌리는데
'The server requested authentication method unknown to the client (SQL: select * from information_schema.tables where table_schema = homestead and table_name = migrations and table_type = 'BASE TABLE')'
라는 오류가 났다. 데이터베이스도 생성하고 database.php 에

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=DB이름
DB_USERNAME=root
DB_PASSWORD=DB비번

로도 맞게 설정했는데 계속해서 오류가 발생했다. 지인에게 물어본 결과
mysql 버전이 높아서 그럴지도 모른다길래 확인해보니 mysql 8버전을 사용하고 있었다.
그래서 mysql 5버전대로 다운그레이드하려고 했으나 비밀번호가 계속해서 안 맞았다.....

결론적으로 mysql을 전체적으로 다시 설치했는데 그 과정을 작성해보겠다.

-- window 기준

1 - 3 까지는 기존에 설정된 mysql server 가 있었을 경우

1. 프로그램 제거
2. mysql server 제거
3. 해당 서버와 관련된 폴더를 찾아서 모두 지움.
4. https://dev.mysql.com/downloads/mysql/5.7.html#downloads
   해당 주소에서 압축파일 다운로드
5. 압축파일을 원하는 폴더에 압축을 품.
6. 커맨드창에서 압축을 푼 파일의 bin 경로로 이동
7. 커맨드창에서 mysql --initialize (안된다면 mysqld --initialize)
8. 커맨드창에서 mysql --install (안된다면 mysqld --install)
9. 커맨드창에서 mysql -uroot -p 를 입력하면 비밀번호를 입력하라고 나오는데, bin 파일 바로 위 경로로 가보면 data 라는 파일이 보일 것이다.
   거기서 '[Note] A temporary password is generated for root@localhost: ' 라는 메세지 뒤에 임시 비밀번호를 비밀번호로 입력하면 끝!

