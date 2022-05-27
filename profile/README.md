![크라우드펀딩](https://user-images.githubusercontent.com/40031858/170699380-4d388257-5a5b-46b9-a0ef-58156c54a032.png)

## 프로젝트를 실행하기 위한 준비물
- mysql
- h2
- redis
- kafka // TODO
- elasticsearch //TODO


```markdown
## 프로젝트 실행 순서
1. run krowdFunding-EureakaServer
2. run KrowdFunding-ApiGateway
3. run KrowdFunding-ConfigServer
4. run KrowdFunding domainServer ex) ProductServer 
- 단, spring active profile jvm argument 값을 넣어야함 ex) local, prod , gcp
```

각 datasource는 config-server에서 읽으며 [구성파일](https://github.com/krowdfunding-projects/Krowdfunding-ConfigProperties)은 여기서 프로파일 정보와 함께 읽어들임.

배포는 gcp에 할예정이며 spring,django,flask, java, kotlin, python언어는 상관없이 eureka를 바라볼 수 있게 개발하면 동작함. (다만 rewritepath필요)







<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
