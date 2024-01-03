---
created: 2023-11-29
---
키워드:: [[SpringBatch]]

## Job

- 배치 계층 구조에서 가장 상위에 있는 개념으로 하나의 배치 작업 자체를 의미한다.
- 배치 작업을 어떻게 구성하고 실행할지 **명세하는 객체**
- 여러 Step을 포함하는 컨테이너

### SimpleJob

순차적으로 Step을 실행시키는 Job

### FlowJob

특정한 조건과 흐름에 따라 Step을 실행시키는 Job

## JobInstance

Job의 논리적 실행 단위 객체

### BATCH_JOB_INSTANCE 테이블과 매핑

- `JOB_NAME(Job)`과 `JOB_KEY(JobParameter 해시값)`가 동일하면 중복 저장 할 수 없다.
- 중복이면 Job 실행도 안해준다. 날짜라도 다르게 넣어야겠다.

## JobParameter

### 코드로 생성

- **JobParameterBuilder**, DefaultJobParametersConverter (주로 JobParameterBuilder 쓴다)

#### JobParameter 설정과 같이 job 실행

```java
@RequiredArgsConstructor  
@Component  
public class JobParameterTest implements ApplicationRunner {  
  private final JobLauncher jobLauncher;  
  private final Job job;  

  @Override  
  public void run(ApplicationArguments args) throws Exception {  
  
      JobParameters jobParameters = new JobParametersBuilder()  
              .addString("name", "user1")  
              .addLong("swq", 2L)  
              .addDate("date", new Date())  
              .addDouble("age", 16.5)  
              .toJobParameters();  
  
      jobLauncher.run(job, jobParameters);  
  }  
}
```

#### Tasklet에서 JobParameters 참조

StepContribution, ChunkContext 파라미터의 필드들을 따라 들어가면 JobParameter가 있으니 참조할 수 있다.

```java
@Bean
public Step step1() {
  return stepBuilderFactory.get("step1")
    .tasklet(new Tasklet() {
      @Override
      public RepeatStatus execute(StepContribution contribution, ChunkContext chunkContext) throws Exception {
        // step은 기본적으로 tasklet을 무한 반복시킨다.
        System.out.println("===========================");
        System.out.println(">> Step1 Spring Batch!!!");

        // StepContribution에서 JobParameters를 참조
        JobParameters jobParameters1 = contribution.getStepExecution().getJobExecution().getJobParameters();
        String name = jobParameters1.getString("name");
        Long seq = jobParameters1.getLong("seq");
        Date date = jobParameters1.getDate("date");
        Double age = jobParameters1.getDouble("age");
        System.out.println("Name: " + name + ", Seq: " + seq + ", Date: " + date + ", Age: " + age);

        // ChunkContext에서 JobParameters를 참조
        Map<String, Object> jobParameters2 = chunkContext.getStepContext().getJobParameters();
        System.out.println(jobParameters2);

        System.out.println("===========================");

        return RepeatStatus.FINISHED; // 종료
      }
    })
    .build();
}
```

### 어플리케이션 실행 시 주입

![[SpringBatch_Jar실행시_JobParameter전달.png]]

- String 타입 외에는 타입을 `( )`안에 지정해줘야 한다.
- date는 `-`로 구분하지 않고 `/`로 구분해야 한다.

다음과 같이 IDE에서 `Program arguments`를 설정할 수도 있다.

![[SpringBatch_IDE에서_JobParameter전달.png]]

### SpEL 이용

- @Value("#{jobParameter[requestDate]}"), @JobScope, @StepScope 선언 필수
- 강의에서 설명 안한 것 같은데
