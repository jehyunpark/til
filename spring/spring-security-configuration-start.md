# Spring Security 설정

- spring boot으로 프로젝트를 생성할 때 security를 설정하면 spring security이 설정되고 의존성도 추가된다.
- 일단 `WebSecurityConfiguration.java` 를 만들어서 `/` 경로에 대한 접근을 풀어보자.

- 아래와 같은 java 파일을 추가하면 기본 `/` 경로에 대한 접근이 허가 되고, 이 파일을 수정해서 원하는 사용자에 대한 권한을 관리 할 수 있다.

``` java
package com.jehyunpark.configuration;

import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;

/**
 * @author jehyunpark
 *
 */
@Configuration
@EnableWebSecurity
public class WebSecurityConfiguration extends WebSecurityConfigurerAdapter {

	protected void configure(HttpSecurity httpSecurity) throws Exception {
		httpSecurity.authorizeRequests().antMatchers("/").permitAll();
	}
}
```
