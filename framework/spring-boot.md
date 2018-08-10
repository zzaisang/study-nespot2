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
 
 

### spring boot  의존성 관리

- [문서](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#using-boot-dependency-management)
- spring boot는 의존성 관리를 알아서해준다. spring-start-parent에서 모든 버전을 property로 관리를 해준다.

### spring boot 자동 설정

0. [문서](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#boot-features-developing-auto-configuration)
1. @SpringbootApplication => @SpringConfiguration(configuration 이랑 같음), @ComponentScan, @EnableAutoConfiguration
2. @SpringbootApplication 실행
	- 처음 @ComponentScan으로 component bean 등록, 자기 자신도 bean 등록.
	- 그다음 EnableAutoConfiguration 실행
	- EnableAutoConfiguration => spring-boot-autoconfigure.jar => spring.factories에 org.springframework.boot.autoconfigure.EnableAutoConfiguratio 변수에 정의되어 있는  모든 클랙스를 모두 bean 등록한다.
	
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


### spring boot 내장 웹 서버

- spring boot는 서버가 아닙니다.
- ServletWebServerFactoryAutoConfiguration 에서 웹 서버를 생성하고
- DispatcherServletAutoConfiguration에서 dispatcher servlet을 생성하고 웹 서버에 등록하는 역할을 합니다.

```java

	//서버 생성
	Tomcat tomcat = new Tomcat();
    tomcat.setPort(8080);
    Context context = tomcat.addContext("/","/");

	//서블렛 생성
    HttpServlet servlet = new HttpServlet() {
      @Override
      protected void doGet(HttpServletRequest req, HttpServletResponse resp)
          throws ServletException, IOException {
        PrintWriter writer = resp.getWriter();
        writer.println("<html>");
        writer.println("<head>");
        writer.println("<head/>");
        writer.println("<body>");
        writer.println("<h1>hello</h1>");
        writer.println("<body/>");
        writer.println("<html/>");

      }
    };

	//서블렛 등록
    tomcat.addServlet("/","hello",servlet);
    context.addServletMappingDecoded("/hello","hello");


	//서비 시작
    tomcat.start();
    tomcat.getServer().await();
```

- 위 코드를 ServletWebServerFactoryAutoConfiguration, DispatcherServletAutoConfiguration가 대신합니다!
- spring-boot-autoconfigure.jar, spring.factories에 포함되어 있기 때문입니다.

### 독립적으로 실행 가능한 JAR

- mvn package를 하면 실행 가능한 JAR 파일 “하나가” 생성 됨.
- spring-maven-plugin이 해주는 일 (패키징)
- 스프링 부트의 전략
	- 내장 JAR : 기본적으로 자바에는 내장 JAR를 로딩하는 표준적인 방법이 없음.
	- 애플리케이션 클래스와 라이브러리 위치 구분
	- org.springframework.boot.loader.jar.JarFile을 사용해서 내장 JAR를 읽는다.
	- org.springframework.boot.loader.Launcher를 사용해서 실행한다.


### Spring boot 원리 정리

- 의존성 관리
	- 이것만 넣어도 이만큼이나 다 알아서 가져오네?
- 자동 설정
	- @EnableAutoConfiguration이 뭘 해주는지 알겠어.
- 내장 웹 서버
	- 아 스프링 부트가 서버가 아니라 내장 서버를 실행하는 거군.
- 독립적으로 실행 가능한 JAR
	- spring-boot-maven 플러그인이 이런걸 해주는구나..


