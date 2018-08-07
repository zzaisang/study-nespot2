# Spring security
---- 


### 개요
	-

### spring security 적용 방법(spring boot에서..)
	- WebSecurityConfigureAdapter를 상속한 class 생성
	- @Configuration, @EnableWebSecurity annotation 추가 작업
	- configure(HttpSecurity http) 오버라이드 메소드 생성

```java

@Configuration
@EnableWebSecurity
public class WebSecurity extends WebSecurityConfigurerAdapter {

  @Override
  protected void configure(HttpSecurity http) throws Exception {

    http.authorizeRequests()
        .antMatchers("/").permitAll().anyRequest().authenticated().and().formLogin()
        .loginPage("/login").permitAll();
  }
}

```
### configure 메소드 분석

	- HttpSecurity 객체를 이용하여 각 path 마다 권한 부여
	- http 객체는 builder 패턴으로 구현되어 있으며 체이닝 방식으로 메소드를 호출한다.
	- authorizeRequests()는 HttpServletRequest 접근을 제한한다.
	- antMathchers("/") 및 permitAll()은 / 로 접근하면 모든 권한을 제공한다는 뜻이다.
	- formLogin()은 login process를 커스텀마이징 한다는 뜻이다.
	- loginPage("/login") login custom page 입니다.

