![image](https://user-images.githubusercontent.com/40031858/170703337-117010a9-0bf2-4128-836e-f58ed6c696ce.png)



## 프로젝트를 실행하기 위한 준비물 🐡
- `mysql` //username : fund password: 1234  default port 사용 (3306)
- `h2` // username : sa  default port 사용 (8082)
- `redis` // default port 사용 (6379)
- `kafka` [카프카 설정](https://github.com/krowdfunding-projects/.github/blob/main/%EC%B9%B4%ED%94%84%EC%B9%B4%EC%84%A4%EC%A0%95.md) 파티션은 3개로 해주고 log가 저장될 경로는 각자 알아서 지정. 
- `elasticsearch` // default port 사용 (9200)
- `zipkin` // default port 사용 (9411)


```markdown
## 프로젝트 실행 순서 🩹
1. run krowdFunding-EureakaServer
2. run KrowdFunding-ApiGateway
// 항상 ./gradlew bootRun이나 스프링애플리케이션 실행하기 귀찮으면 아래와 같이 도커로 띄우시면됩니다 만들어놨어요!!
#### 참고로 김준성은 m1이라 platform붙인거고 안붙이셔도 됩니다.
// docker run -it -p 8888:8888 --platform linux/amd64 anima94/eureka
// docker run -it -p 9001:9001 --platform linux/amd64 anima94/configserver

3. run KrowdFunding-ConfigServer
4. run KrowdFunding domainServer ex) ProductServer 
- 단, spring active profile jvm argument 값을 넣어야함 ex) local, prod , gcp
- 각 server.port는 0으로 해주세요 
```

각 datasource는 config-server에서 읽으며 [구성파일](https://github.com/krowdfunding-projects/Krowdfunding-ConfigProperties)은 여기서 프로파일 정보와 함께 읽어들임.

배포는 gcp에 할예정이며 spring,django,flask, java, kotlin, python언어는 상관없이 eureka를 바라볼 수 있게 개발하면 동작함. (다만 rewritepath필요)

### 스프링프레임워크를 사용할경우 필수 의존성 ⏰
```groovy
implementation("org.springframework.boot:spring-boot-starter-data-jpa")
implementation("org.springframework.boot:spring-boot-starter-hateoas")
implementation("org.springframework.boot:spring-boot-starter-validation")
implementation("org.springframework.boot:spring-boot-starter-web")
implementation("org.springframework.cloud:spring-cloud-starter-netflix-eureka-client")
implementation("org.springframework.cloud:spring-cloud-config-client")
implementation 'org.springframework.cloud:spring-cloud-sleuth-zipkin'
implementation 'org.springframework.cloud:spring-cloud-starter-sleuth'
implementation 'org.springframework.cloud:spring-cloud-starter-openfeign'

runtimeOnly("com.h2database:h2")
runtimeOnly("mysql:mysql-connector-java")


//   optional(필수 사항 아닌 각 도메인 구현하는 사람의 필요하에 추가)
implementation("com.querydsl:querydsl-jpa:$querydslVersion")
implementation 'org.springframework.data:spring-data-elasticsearch:4.4.0'
implementation 'org.springframework.kafka:spring-kafka'
implementation 'org.springframework.boot:spring-boot-starter-security'
implementation 'io.jsonwebtoken:jjwt-api:0.11.1'
implementation 'org.springframework.boot:spring-boot-starter-data-redis'
runtimeOnly 'io.jsonwebtoken:jjwt-impl:0.11.1', 'io.jsonwebtoken:jjwt-jackson:0.11.1'
compileOnly 'org.projectlombok:lombok' //자바로 할사람만
annotationProcessor 'org.projectlombok:lombok'

```

## 현재 대략 구상안

![image](https://user-images.githubusercontent.com/40031858/170803051-a6c77f1b-0e6a-48bd-80dc-834564f241cf.png)




![d32237f759e71cd3c228c27b96601b73_1547457159_4914](https://user-images.githubusercontent.com/40031858/170702700-e47a4576-cb3f-49a9-abbe-a63cd9f84887.gif)






<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
