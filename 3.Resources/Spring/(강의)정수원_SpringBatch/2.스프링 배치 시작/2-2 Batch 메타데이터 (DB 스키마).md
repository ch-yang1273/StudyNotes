---
created: 2023-11-24
---
키워드:: [[SpringBatch]]

## 메타데이터 DB 스키마 생성

Spring Batch는 스프링 배치의 실행 및 관리를 위한 목적으로 여러 도메인들(Job, Step, JobParameters 등)의 정보를 저장, 업데이트, 조회를 할 수 있는 DB 스키마를 제공한다.

### 수동 생성

External Libraries에서 `spring-batch-core` 까보면 `org.springframework.batch.core`에 각 DB에 맞는 테이블 생성 쿼리 (schema-mysql.sql) 파일이 있다.

이 파일의 생성 쿼리를 복사해서 실행하면 테이블이 생성된다.

이 강의에서 db는 docker로 mysql을 설치해서 사용했고, database는 알아서 생성해서 따라했다.

### 자동 생성

`spring.batch.jdbc.initialize-schema` 설정으로 DB 스키마를 자동 생성할 수도 있다.

- alyays : 스크립트를 항상 실행
- embedded : 내장 DB일 때만 실행되며 스키마가 자동 생성된다. 기본값
- never : 스크립트 실행 안함. 운영에서는 수동으로 생성 후 never로 설정하는 것을 권장

`alyays`로 한번 실행해서 생성하고 `never`로 바꿔서 운영하면 편할 것 같다.

```yml
spring:  
  profiles:  
    active: mysql  
  
---  
spring:  
  config:  
    activate:  
      on-profile: local  
  datasource:  
    hikari:  
      jdbc-url: jdbc:h2:mem:testdb;DB_CLOSE_DELAY=-1;DB_CLOSE_ON_EXIT=FALSE  
      username: sa  
      password:  
      driver-class-name: org.h2.Driver  
  batch:  
    jdbc:  
      initialize-schema: embedded  
  
---  
spring:  
  config:  
    activate:  
      on-profile: mysql  
  datasource:  
    hikari:  
      jdbc-url: jdbc:mysql://localhost:3306/springbatch?useUnicode=true&characterEncoding=utf8  
      username: root  
      password: 1234  
      driver-class-name: com.mysql.cj.jdbc.Driver  
  batch:  
    jdbc:  
      initialize-schema: always
```

## 메타데이터 테이블

### JOB 관련 테이블

- BATCH_JOB_INSTANCE : Job이 실행될 때 JobInstance 정보가 저장
- BATCH_JOB_EXECUTION : Job 실행 정보
- BATCH_JOB_EXECUTION_PARAMS : JobParameter 정보
- BATCH_JOB_EXECUTION_CONTEXT : 실행하는 동안 여러가지 상태 정보, 공유 데이터

### STEP 관련 테이블

- BATCH_STEP_EXECUTION : Step의 실행 정보
- BATCH_STEP_EXECUTION_CONTEXT : 실행하는 동안 여러가지 상태 정보, 공유 데이터

![[Pasted image 20231128072533.png]]