# SQL
Structured Query Language <br>
즉, 구조화된 Query 언어 <br><br><br>

## Query란?
직역하면 "질의문".<br>
가장 대표적인 예시로는 검색창에 적는 검색어도 Query의 일종<br>
즉, 저장되어있는 정보를 필터 하기 위한 질문.<br>
(ex. 구글에 데이터를 저장하기 위한 정리 된 데이터 베이스가 있는데, 검색창에 검색어를 적음으로 그 데이터 베이스에 있는 데이터 중 필요한 것을 필터링 해서 보여준다) <br><br><br>
 

## 즉, SQL이란
- 데이터 베이스 용 프로그래밍 언어
- 데이터 베이스에 Query를 보내 원하는 데이터만 필터링 할 수 있다. <br>
(구조화된 Query 언어이기 때문에 구조를 배우고 문법에 맞게 써야한다.) <br><br><br>
 

# 데이터 베이스가 필요한 이유
- In-memory는 끄면 데이터가 없어진다.
- File I/O는 원하는 데이터만 가져올 수 없고 항상 모든 데이터를 가져온 뒤 서버에서 필터링 해야한다. (서버에 부하가 많이 생긴다.) <br><br>

- DataBase
필터링 외에도 File I/O로 구현하기 힘든 데이터 관리를 위해 여러 기능들을 가지고 있는 데이터에 특화된 서버 <br><br>


![IntelliJ의 Database Navigator를 이용해 시각화한 데이터베이스](https://blog.kakaocdn.net/dn/R6H5M/btrEnvVwvKk/a2dRCoxHHVXkicCsIN1xek/img.png)
IntelliJ의 Database Navigator를 이용해 시각화한 데이터베이스 <br><br>
그런데 이 데이터 베이스를 보면 엑셀(스프레드시트)와 비슷하게 생겼다.<br><br>

실제로 이 둘은 거의 비슷하다.<br>
데이터 베이스를 이해하기 위해 엑셀을 생각하며 학습하면 쉽게 이해할 수 있다.<br><br>

 

- 엑셀의 시트  ->  데이터베이스의 테이블(Ex. 위 그림의 EMPLOYEES 테이블)
- 둘 다 Column(열), Row(행)이 있음
 

**EX. SQL을 이용해서 필터링**
```sql
SELECT *                 // *(모든 Column을) 선택하라
FROM EMPLOYEES           // EMPLOYEES 테이블에서
WHERE JOB_ID = IT_PROG;  // JOB_ID가 IT_PROG인 데이터들을
```
 
<br><br><br>
 

 

![클라이언트-서버-데이터베이스 관계 (Three Tier Architecture)](https://blog.kakaocdn.net/dn/lZd9g/btrEn9dyGtM/fSMhoGZKr8Jk3hipLIKLqK/img.png)
<br>클라이언트-서버-데이터베이스 관계 (Three Tier Architecture)
 <br><br><br>

# SQL 명령어 모음
https://goodmemory.tistory.com/51
<br><br>
 

☆ SQL 명령어 학습을 위한 유용한 사이트 (복습할 것.)

https://www.w3schools.com/sql/exercise.asp?filename=exercise_select1 

<br><br><br>

*엑셀(스프레드시트)를 연상하며 데이터베이스와 SQL을 학습하자.*
