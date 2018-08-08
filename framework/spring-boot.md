# Spring boot

### 개요
 - 제품 수준의 스프링 기반의 어플리케이션을 만들때 빠르고 쉽게 만들 수 있다.
 - 일일이 설정을 하지 않아도 컨벤션으로 설정되어 있는 것들을 사용할 수 있다. 하지만 내가 원하는 대로 쉽고 빠르게 변경 할 수 있다.
 - 비지니스 로직에 구현에 필요한 기능 뿐 아니라 non-functional features에 대해서도 지원을 해준다.
 

### spring boot 구조
 - [문서](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#using-boot-structuring-your-code)
 - 메이븐 기본 프로젝트 구조와 동일
 	1. 소스 코드 (src\main\java)
 	2. 소스 리소스 (src\main\resource)
 	3. 테스트 코드 (src\test\java)
	4. 테스트 리소스 (src\test\resource)
 - @SpringBootApplication
 
 

### spring boot  원리
- spring boot는 의존성 관리를 알아서해준다. spring-start-parent에서 모든 버전을 property로 관리를 해준다.

0. [문서](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#boot-features-developing-auto-configuration)
1. @SpringbootApplication => @SpringConfiguration(configuration 이랑 같음), @ComponentScan, @EnableAutoConfiguration
2. @SpringbootApplication 실행
	2.1 처음 @ComponentScan으로 component bean 등록, 자기 자신도 bean 등록.
	2.2 그다음 EnableAutoConfiguration 실행
	2.3 EnableAutoConfiguration => spring-boot-autoconfigure.jar => spring.factories에 org.springframework.boot.autoconfigure.EnableAutoConfiguratio 변수에 정의되어 있는  모든 클랙스를 모두 bean 등록한다.
	
3. spring-boot-autoconfigure를 커스텀마이징 하여 EnableAutoConfigureation에 포함 할 수 있음
	
### EnableAutoConfiguration 커스텀 마이징 구현 방법(jar 만들기)
- 의존성 추가
	
```XML
<dependencies>
  <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-autoconfigure</artifactId>
  </dependency>
  <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-autoconfigure-processor</artifactId>
      <optional>true</optional>
  </dependency>
</dependencies>

<dependencyManagement>
  <dependencies>
      <dependency>
          <groupId>org.springframework.boot</groupId>
          <artifactId>spring-boot-dependencies</artifactId>
          <version>2.0.3.RELEASE</version>
          <type>pom</type>
          <scope>import</scope>
      </dependency>
  </dependencies>
</dependencyManagement>
```

- @Configuration 파일 작성
- @ConditionalOnMissingBean 추가 => 덮어쓰기 방지!
- src/main/resource/META-INF에 spring.factories 파일 만들기
- spring.factories 안에 자동 설정 파일 추가


```
org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
FQCN,\
FQCN
```

- 빈 재정의 수고 덜기
	- @ConfigurationProperties(“helloman”)
	- @EnableConfigurationProperties(HellomanProperties.class)
	- 프로퍼티 키 값 자동 생성 => application.properties에 키 값 정의

```
<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-configuration-processor</artifactId>
   <optional>true</optional>
</dependency>

```

- mvn install