# 의존성 (Dependency)

- `spring-boot-starter-web`
    
    ```java
    <!-- Spring MVC와 내장된 톰캣 서버를 포함하여 웹 어플리케이션을 만들기 위한 의존성 -->
    <dependency>
    	<groupId>org.springframework.boot</groupId>
    	<artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    ```
    
    - **Spring Boot** 기반의 웹 어플리케이션을 개발하기 위해 필요한 모든 필수 구성 요소들을 포함하고 있는 스타터 패키지이다.
    - 위의 의존성을 추가하면 다음과 같은 기능들을 사용할 수 있다.
        - Spring MVC
            - 어플리케이션의 비즈니스 로직, 프레젠테이션 로직, 데이터 접근 로직을 분리하는 데 도움이 된다.
            - 컨트롤러, RESTful 웹 서비스, 웹 요청 및 응답 처리, 데이터 바인딩, 폼 데이터 처리 등을 위한 다양한 기능을 제공한다.
        - 내장된 톰캣 서버
            - 어플리케이션을 실행하기 위해 별도의 웹 서버를 설치할 필요 없이 어플리케이션을 독립적으로 실행할 수 있도록 해준다.
            - 개발 중에 어플리케이션을 쉽게 실행하고 테스트할 수 있게 해주며, 프로덕션 환경에서는 독립형 어플리케이션으로 배포할 수 있다.
        - Jackson
            - Jackson 라이브러리는 JSON 데이터의 직렬화 및 역직렬화를 처리한다.
            - Spring MVC 컨트롤러는 **요청 및 응답 본문을 JSON 형식으로 변환하는 데 Jackson을 사용**한다.
        - **Spring Boot** 자동 구성
            - **Spring Boot**의 자동 구성 기능을 포함한다.
            - 이는 어플리케이션의 다양한 구성 요소들을 자동으로 설정하여 개발자가 별도로 설정 파일을 작성하지 않고도 쉽게 웹 어플리케이션을 구축할 수 있도록 해준다.
    - 포함된 의존성
        - `spring-web`
        - `spring-webmvc`
        - `spring-boot-starter-tomcat`
        - `spring-boot-starter-json`
        - `spring-boot-starter-validation`
        - `jackson-databind`
        - `jackson-core`
        - `jackson-annotations`
    - 예제
        
        ```java
        pom.xml
        
        <dependencies>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-starter-web</artifactId>
            </dependency>
        </dependencies>
        
        ============================================================
        
        Application.java
        
        import org.springframework.boot.SpringApplication;
        import org.springframework.boot.autoconfigure.SpringBootApplication;
        
        @SpringBootApplication
        public class Application {
            public static void main(String[] args) {
                SpringApplication.run(Application.class, args);
            }
        }
        
        ============================================================
        
        HelloController.java
        
        import org.springframework.web.bind.annotation.GetMapping;
        import org.springframework.web.bind.annotation.RestController;
        
        @RestController
        public class HelloController {
        
            @GetMapping("/hello")
            public String hello() {
                return "Hello, World!";
            }
        }
        
        위의 코드에서 spring-boot-starter-web 의존성을 추가함으로써, Spring Boot
        어플리케이션은 내장된 톰캣 서버를 사용하여 실행되며, `/hello` 엔드포인트를 통해
        간단한 웹 요청을 처리할 수 있게 된다.
        `@RestController`와 `@GetMapping` 어노테이션을 사용하여 HTTP GET 요청을
        처리하는 RESTful 웹 서비스를 쉽게 만들 수 있다.
        ```
        
- `spring-boot-starter-test`
    
    ```java
    <!-- Spring Boot에서 테스트를 지원하는 의존성 -->
    <dependency>
    	<groupId>org.springframework.boot</groupId>
    	<artifactId>spring-boot-starter-test</artifactId>
    	<scope>test</scope>
    </dependency>
    ```
    
    - **Spring Boot** 어플리케이션에서 테스트를 지원하기 위한 다양한 라이브러리를 포함하고 있는 스타터 패키지이다.
    - 위의 의존성은 테스트 코드를 작성하고 실행하는데 필요한 다양한 도구와 프레임워크를 제공한다.
    - 위의 의존성을 추가하면 다음과 같은 기능들을 사용할 수 있다.
        - JUnit
            - JUnit은 자바 어플리케이션의 단위 테스트를 작성하고 실행하기 위한 프레임워크이다. **Spring Boot**는 기본적으로 JUnit 5(Jupiter)를 지원한다.
        - Spring TestContext Framework
            - **Spring TestContext Framework**는 통합 테스트를 지원한다.
            - 이 프레임워크는 어플리케이션 컨텍스트의 설정 및 관리를 자동화하여 테스트 중에도 실제와 유사한 환경을 제공한다.
            - `@SpringBootTest`, `@WebMvcTest`, `@DataJpaTest` 등의 어노테이션을 사용하여 다양한 테스트 시나리오를 설정할 수 있다.
        - Mockito …
        - Hamcrest …
        - AssertJ …
        - JsonPath
            - JsonPath는 JSON 데이터를 처리하고 검증하기 위한 라이브러리이다. JSON 응답의 특정 부분을 쉽게 추출하고 검증할 수 있다.
        - Spring MockMvc …
    - 포함된 의존성
        - `JUnit 5 (Jupiter)`
        - `Spring TestContext Framework`
        - `Mockito`
        - `Hamcrest`
        - `AssertJ`
        - `JsonPath`
        - `Spring MockMvc`
    - 예제
        - pom.xml
            
            ```java
            pom.xml
            
            <dependencies>
                <dependency>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-starter-test</artifactId>
                    <scope>test</scope>
                </dependency>
            </dependencies>
            ```
            
        - Application.java
            
            ```java
            Application.java
            
            import org.springframework.boot.SpringApplication;
            import org.springframework.boot.autoconfigure.SpringBootApplication;
            
            @SpringBootApplication
            public class Application {
                public static void main(String[] args) {
                    SpringApplication.run(Application.class, args);
                }
            }
            ```
            
        - HelloController.java
            
            ```java
            HelloController.java
            
            import org.junit.jupiter.api.Test;
            import org.springframework.beans.factory.annotation.Autowired;
            import org.springframework.boot.test.autoconfigure.web.servlet.WebMvcTest;
            import org.springframework.test.web.servlet.MockMvc;
            import org.springframework.test.web.servlet.result.MockMvcResultMatchers;
            
            import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get;
            
            @WebMvcTest(HelloController.class)
            public class HelloControllerTest {
            
                @Autowired
                private MockMvc mockMvc;
            
                @Test
                public void testHello() throws Exception {
                    mockMvc.perform(get("/hello"))
                           .andExpect(MockMvcResultMatchers.status().isOk())
                           .andExpect(MockMvcResultMatchers.content().string("Hello, World!"));
                }
            }
            
            ```
            
        - HelloControllerTest.java
            
            ```java
            HelloControllerTest.java
            
            import org.junit.jupiter.api.Test;
            import org.springframework.beans.factory.annotation.Autowired;
            import org.springframework.boot.test.autoconfigure.web.servlet.WebMvcTest;
            import org.springframework.test.web.servlet.MockMvc;
            import org.springframework.test.web.servlet.result.MockMvcResultMatchers;
            
            import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get;
            
            @WebMvcTest(HelloController.class)
            public class HelloControllerTest {
            
                @Autowired
                private MockMvc mockMvc;
            
                @Test
                public void testHello() throws Exception {
                    mockMvc.perform(get("/hello"))
                           .andExpect(MockMvcResultMatchers.status().isOk())
                           .andExpect(MockMvcResultMatchers.content().string("Hello, World!"));
                }
            }
            ```
            
        - 설명
            - 의존성 : `spring-boot-starter-test` 의존성을 추가하여 다양한 테스트 도구와 프레임워크를 사용할 수 있다.
            - HelloController : 간단한 REST 컨트롤러로, `/hello` 엔드포인트를 통해 문자열을 반환한다.
            - HelloControllerTest : @WebMvcTest 어노테이션을 사용하여 웹 계층의 테스트를 수행한다. MockMvc를 사용하여 `/hello` 엔드포인트를 테스트하고, 응답 상태와 내용을 검증한다.
- `spring-boot-devtools`
    
    ```java
    <!-- 어플리케이션의 자동 재시작 및 기타 개발 편의 기능을 제공 -->
    <dependency>
    	<groupId>org.springframework.boot</groupId>
    	<artifactId>spring-boot-devtools</artifactId>
    	<optional>true</optional>
    </dependency>
    ```
    
    - **Spring Boot** 어플리케이션의 개발 편의성을 높이기 위해 다양한 기능을 제공한다.
    - 위의 의존성을 추가하면 다음과 같은 기능들을 사용할 수 있다.
        - 자동 재시작 (Automatic Restart)
            - 소스 코드가 변경될 때 어플리케이션을 자동으로 재시작한다. 이를 통해 개발자는 변경 사항을 즉시 반영할 수 있으며, 어플리케이션을 수동으로 재시작할 필요가 없다.
            - Spring Boot DevTools는 클래스패스(classpath)를 모니터링하여 변경 사항이 감지되면 어플리케이션을 빠르게 재시작한다.
        - 라이브 리로딩 (Live Reload)
            - 브라우저에서 페이지를 자동으로 새로고침하며 이 기능은 프론트엔드 개발 시 매우 유용하다.
        - 캐시 비활성화 (Disable Caching)
            - 템플릿 엔진이나 정적 리소스의 캐싱을 비활성화하여 변경 사항이 즉시 반영되도록 한다.
            - 이는 개발 중 변경 사항을 즉시 확인하는 데 도움을 준다.
        - 개발 전용 설정 (Development-Only Settings) …
        - JMX 리스타트
            - JMX를 통해 어플리케이션을 원격으로 재시작할 수 있는 엔드포인트를 제공한다. 이를 통해 개발자가 IDE 외부에서도 어플리케이션을 재시작할 수 있다.
    - 포함된 의존성
        - 자동 재시작 기능
        - 라이브 리로딩 기능
        - 개발 전용 설정
    - 예제
        - pom.xml
            
            ```java
            pom.xml
            
            <dependencies>
                <dependency>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-devtools</artifactId>
                    <optional>true</optional>
                </dependency>
            </dependencies>
            ```
            
        - Application.java
            
            ```java
            Application.java
            
            import org.springframework.boot.SpringApplication;
            import org.springframework.boot.autoconfigure.SpringBootApplication;
            
            @SpringBootApplication
            public class Application {
                public static void main(String[] args) {
                    SpringApplication.run(Application.class, args);
                }
            }
            ```
            
        - 설명
            - 의존성 : `spring-boot-devtools` 의존성을 추가하면 개발 환경에서 다양한 편의 기능을 사용할 수 있다. `optional` 속성은 이 의존성이 컴파일 또는 런타임 클래스패스에 자동으로 포함되지 않도록 한다. 이는 **DevTools**가 주로 개발 환경에서만 사용되기 때문이다.
            - [Application.java](http://Application.java) : 기본 **Spring Boot** 어플리케이션 클래스로, **DevTools**가 자동 재시작 및 기타 개발 편의 기능을 제공하게 된다.
- `mybatis-spring-boot-starter`
    
    ```java
    <!-- MyBatis와 Spring Boot의 통합을 위한 의존성 -->
    <dependency>
    	<groupId>org.mybatis.spring.boot</groupId>
    	<artifactId>mybatis-spring-boot-starter</artifactId>
    	<version>3.0.3</version>
    </dependency>
    ```
    
    - **MyBatis**와 **Spring Boot**를 통합하여 사용하는 데 필요한 모든 필수 구성 요소들을 포함하고 있는 패키지이다.
    - 위의 의존성을 추가하면 다음과 같은 기능들을 사용할 수 있다.
        - **MyBatis**와 **Spring Boot** 통합
            - **MyBatis**는 SQL, 저장 프로시저 및 고급 매핑을 지원하는 퍼시스턴스 프레임워크로 위의 의존성을 추가함으로써 **MyBatis**를 **Spring Boot** 어플리케이션에 통합하여 사용할 수 있게 된다.
        - 자동 구성
            - **Spring Boot**의 자동 구성 기능을 통해 **MyBatis**와 관련된 설정을 자동으로 처리한다.
            - 즉, **MyBatis** 설정 파일을 명시적으로 작성하지 않아도 기본 설정이 자동으로 적용된다.
        - 매퍼 스캔
            - **`@MapperScan`**어노테이션을 사용하여 매퍼 인터페이스를 스캔하고, 이를 통해 MyBatis 매퍼 인터페이스가 자동으로 빈으로 등록된다.
        - SQL 세션 관리
            - **MyBatis**의 `SqlSessionFactory`와 `SqlSessionTemplate`을 자동으로 구성한다.
            - 이는 **MyBatis**와 상호작용하는 데 필요한 SQL 세션을 관리하는 데 도움을 준다.
    - 포함된 의존성
        - `mybatis`
        - `mybatis-spring`
        - `spring-boot-starter`
        - 기타 **MyBatis**와 **Spring Boot** 통합에 필요한 라이브러리들
    - 예제
        - pom.xml
            
            ```java
            pom.xml
            
            <dependencies>
                <dependency>
                    <groupId>org.mybatis.spring.boot</groupId>
                    <artifactId>mybatis-spring-boot-starter</artifactId>
                    <version>3.0.3</version>
                </dependency>
            </dependencies>
            ```
            
        - Application.java
            
            ```java
            Application.java
            
            import org.springframework.boot.SpringApplication;
            import org.springframework.boot.autoconfigure.SpringBootApplication;
            
            @SpringBootApplication
            public class Application {
                public static void main(String[] args) {
                    SpringApplication.run(Application.class, args);
                }
            }
            ```
            
        - DBConfig.java
            
            ```java
            DBConfig.java
            
            package com.example.demo.config;
            
            import org.mybatis.spring.annotation.MapperScan;
            import org.springframework.context.annotation.Configuration;
            
            @Configuration
            @MapperScan(basePackages = "com.example.demo.mapper")
            public class DBConfig {
            }
            ```
            
        - UserMapper.java
            
            ```java
            UserMapper.java
            
            package com.example.demo.mapper;
            
            import org.apache.ibatis.annotations.Mapper;
            import org.apache.ibatis.annotations.Select;
            import com.example.demo.model.User;
            
            @Mapper
            public interface UserMapper {
            
                @Select("SELECT * FROM users WHERE id = #{id}")
                User getUserById(int id);
            }
            ```
            
        - User.java
            
            ```java
            User.java
            
            package com.example.demo.model;
            
            public class User {
                private int id;
                private String name;
                private String email;
            
                // getters and setters
            }
            ```
            
        - UserService.java
            
            ```java
            UserService.java
            
            package com.example.demo.service;
            
            import com.example.demo.mapper.UserMapper;
            import com.example.demo.model.User;
            import org.springframework.beans.factory.annotation.Autowired;
            import org.springframework.stereotype.Service;
            
            @Service
            public class UserService {
            
                @Autowired
                private UserMapper userMapper;
            
                public User getUserById(int id) {
                    return userMapper.getUserById(id);
                }
            }
            ```
            
        - UserController.java
            
            ```java
            UserController.java
            
            package com.example.demo.controller;
            
            import com.example.demo.model.User;
            import com.example.demo.service.UserService;
            import org.springframework.beans.factory.annotation.Autowired;
            import org.springframework.web.bind.annotation.GetMapping;
            import org.springframework.web.bind.annotation.PathVariable;
            import org.springframework.web.bind.annotation.RestController;
            
            @RestController
            public class UserController {
            
                @Autowired
                private UserService userService;
            
                @GetMapping("/user/{id}")
                public User getUserById(@PathVariable int id) {
                    return userService.getUserById(id);
                }
            }
            
            ```
            
        - 설명
            - 의존성 : `mybatis-spring-boot-starter` 의존성을 추가하여 **MyBatis**와 **Spring Boot**를 통합한다.
            - [DBConfig.java](http://DBConfig.java) : `@MapperScan` 어노테이션을 사용하여 **MyBatis** 매퍼 인터페이스를 스캔한다.
            - [UserMapper.java](http://UserMapper.java) : **MyBatis** 매퍼 인터페이스로, SQL 쿼리를 정의한다.
            - [UserService.java](http://UserService.java) : 비즈니스 로직을 담당하는 서비스 클래스이다.
            - [UserController.java](http://UserController.java) : REST 컨트롤러로, HTTP 요청을 처리한다.
        - 위의 설정을 통해 **MyBatis**와 **Spring Boot**를 사용하여 데이터베이스와 상호작용하는 웹 어플리케이션을 쉽게 구축할 수 있다.
        - **MyBatis**는 SQL 쿼리와 객체 매핑을 자동으로 처리하며, **Spring Boot**는 어플리케이션의 기본적인 설정과 구성을 자동으로 처리한다.
- `mybatis-spring-boot-starter-test`
    
    ```java
    <!-- MyBatis와 Spring Boot 통합 테스트를 위한 의존성 -->
    <dependency>
    	<groupId>org.mybatis.spring.boot</groupId>
    	<artifactId>mybatis-spring-boot-starter-test</artifactId>
    	<version>3.0.3</version>
    	<scope>test</scope>
    </dependency>
    ```
    
    - **MyBatis**를 사용하는 어플리케이션의 테스트를 쉽게 작성하고 실행할 수 있도록 여러 기능을 제공한다.
    - 위의 의존성을 추가하면 다음과 같은 기능들을 사용할 수 있다.
        - **MyBatis**와 **Spring** 통합 테스트 지원
            - **MyBatis**와 **Spring Boo**t 어플리케이션의 통합 테스트를 위한 설정과 기능을 제공한다.
            - **MyBatis** 매퍼와 SQL 세션을 쉽게 모의(mock)하고 테스트할 수 있도록 도와준다.
        - 자동 설정 지원
            - 통합 테스트 환경에서 **MyBatis**와 **Spring Boo**t의 자동 설정을 지원한다.
            - 이를 통해 테스트 시 설정을 간소화하고 일관성을 유지할 수 있다.
        - 트랜잭션 관리
            - 테스트 실행 중에 트랜잭션을 관리하고, 테스트 후 롤백하여 데이터베이스의 상태를 원래대로 복원한다.
            - 이를 통해 테스트 데이터가 실제 데이터에 영향을 미치지 않도록 한다.
    - 포함된 라이브러리
        - **Mybatis-Spring** : **MyBatis**와 **Spring** 간의 통합을 지원하는 라이브러리이다.
        - **Spring TestContext Framework** : 통합 테스트를 지원하는 **Spring**의 테스트 프레임워크이다.
        - **JUnit** : 단위 테스트 및 통합 테스트를 작성하고 실행하기 위한 표준 프레임워크이다.
        - **Mockito** : 모의 객체를 생성하고 동작을 설정할 수 있는 프레임워크이다.
    - 예제
        - pom.xml
            
            ```java
            pom.xml
            
            <dependencies>
                <dependency>
                    <groupId>org.mybatis.spring.boot</groupId>
                    <artifactId>mybatis-spring-boot-starter-test</artifactId>
                    <version>3.0.3</version>
                    <scope>test</scope>
                </dependency>
            </dependencies>
            ```
            
        - UserMapper.java
            
            ```java
            UserMapper.java
            
            package com.example.demo.mapper;
            
            import org.apache.ibatis.annotations.Mapper;
            import org.apache.ibatis.annotations.Select;
            import com.example.demo.model.User;
            
            @Mapper
            public interface UserMapper {
                @Select("SELECT * FROM users WHERE id = #{id}")
                User getUserById(int id);
            }
            ```
            
        - UserMapperTest.java
            
            ```java
            UserMapperTest.java
            
            package com.example.demo;
            
            import com.example.demo.mapper.UserMapper;
            import com.example.demo.model.User;
            import org.junit.jupiter.api.Test;
            import org.mybatis.spring.boot.test.autoconfigure.MybatisTest;
            import org.springframework.beans.factory.annotation.Autowired;
            import org.springframework.boot.test.autoconfigure.jdbc.AutoConfigureTestDatabase;
            import static org.assertj.core.api.Assertions.assertThat;
            
            @MybatisTest
            @AutoConfigureTestDatabase(replace = AutoConfigureTestDatabase.Replace.NONE)
            public class UserMapperTest {
            
                @Autowired
                private UserMapper userMapper;
            
                @Test
                void testGetUserById() {
                    User user = userMapper.getUserById(1);
                    assertThat(user).isNotNull();
                    assertThat(user.getName()).isEqualTo("John Doe");
                }
            }
            ```
            
        - 설명
            - 의존성 : `mybatis-spring-boot-startet-test` 의존성을 추가하여 **MyBatis**와 **Spring Boot** 통합 테스트를 위한 설정을 제공한다.
            - `UserMapper` : **MyBatis** 매퍼 인터페이스로, 데이터베이스의 `users` 테이블에서 데이터를 조회하는 메소드를 정의한다.
            - `UserMapperTest`
                - `@MybatisTest` 어노테이션을 사용하여  **MyBatis** 매퍼를 테스트한다. 이 어노테이션은 **MyBatis** 관련 설정만 로드하고, 기본적으로 인메모리 데이터베이스를 사용한다.
                - `@AutoConfigureTestDatabase(replace = AutoConfigureTestDatabase.Replace.NONE)` 어노테이션을 사용하여 인메모리 데이터베이스 대신 실제 데이터베이스를 사용하도록 설정한다.
                - `testGetUserById` 메소드는 `userMapper`를 통해 사용자 정보를 조회하고, 결과를 검증한다.
- `springdoc-openapi-starter-webmvc-ui`
    
    ```java
    <!-- https://mvnrepository.com/artifact/org.springdoc/springdoc-openapi-starter-webmvc-ui -->
    <!-- SpringDoc을 사용하여 OpenAPI 3 문서 생성을 지원하는 의존성 -->
    <dependency>
        <groupId>org.springdoc</groupId>
        <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
        <version>2.4.0</version>
    </dependency>
    ```
    
    - Spring Boot 어플리케이션에서 SpringDoc을 사용하여 OpenAPI 3 문서를 자동으로 생성하고, 웹 UI를 통해 쉽게 접근할 수 있도록 지원한다.
    - 이 의존성은 OpenAPI 3 스펙을 기반으로 RESTful API 문서를 생성하며, Swagger UI를 통해 웹 브라우저에서 문서를 시각적으로 확인하고 테스트할 수 있는 기능을 제공한다.
    - 위의 의존성을 추가하면 다음과 같은 기능들을 사용할 수 있다.
        - OpenAPI 3 문서 자동 생성
            - SpringDoc은 어플리케이션의 RESTful API를 분석하여 OpenAPI 3 스펙에 맞는 문서를 자동으로 생성한다.
            - 이 문서는 API 엔드포인트, 요청 및 응답 형식, 파라미터, 상태 코드 등을 포함한다.
        - Swagger UI 통합
            - Swagger UI는 웹 브라우저에서 API 문서를 시각적으로 확인하고, 직접 테스트할 수 있는 인터페이스를 제공한다.
            - 이를 통해 개발자와 사용자들은 API의 사용법을 쉽게 이해하고 테스트할 수 있다.
        - API 문서의 실시간 업데이트
            - 어플리케이션이 실행되는 동안 변경된 API 엔드포인트는 자동으로 문서에 반영된다.
            - 이를 통해 항상 최신의 API 문서를 유지할 수 있다.
    - 예제
        - pom.xml
            
            ```java
            pom.xml
            
            <dependencies>
                <!-- SpringDoc을 사용하여 OpenAPI 3 문서 생성을 지원하는 의존성 -->
                <dependency>
                    <groupId>org.springdoc</groupId>
                    <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
                    <version>2.4.0</version>
                </dependency>
            </dependencies>
            ```
            
        - Application.java
            
            ```java
            Application.java
            
            import org.springframework.boot.SpringApplication;
            import org.springframework.boot.autoconfigure.SpringBootApplication;
            
            @SpringBootApplication
            public class Application {
                public static void main(String[] args) {
                    SpringApplication.run(Application.class, args);
                }
            }
            ```
            
        - HelloController.java
            
            ```java
            HelloController.java
            
            import org.springframework.web.bind.annotation.GetMapping;
            import org.springframework.web.bind.annotation.RestController;
            
            @RestController
            public class HelloController {
            
                @GetMapping("/hello")
                public String hello() {
                    return "Hello, World!";
                }
            }
            ```
            
        - 설명
            - 의존성 : `springdoc-openapi-starter-webmvc-ui` 의존성을 추가하여 **SpringDoc**을 통해 OpenAPI 3 문서를 생성하고 Swagger UI를 통합한다.
            - [Application.java](http://Application.java) : **Spring Boot** 어플리케이션의 진입점으로, **SpringDoc**이 어플리케이션의 컨트롤러를 스캔하여 API 문서를 생성할 수 있도록 한다.
            - [HelloController.java](http://HelloController.java) : 간단한 REST 컨트롤러로, `/hello`엔드포인트를 정의한다.
    - Swagger UI 접근
        - 어플리케이션을 실행한 후, 웹 브라우저에서 [`http://localhost:8080/swagger-ui.html`](http://localhost:8080/swagger-ui.html로)로 접근하면 Swagger UI를 통해 자동 생성된 OpenAPI 3 문서를 확인할 수 있다.
        - 여기에서 API 엔드포인트를 시각적으로 확인하고 직접 테스트할 수 있다.
    - 주요 이점
        - 자동화된 문서 생성
            - **SpringDoc**이 어플리케이션의 RESTful API를 자동으로 문서화하여 수작업의 필요성을 줄여준다.
        - 실시간 업데이트
            - API 변경 사항이 실시간으로 문서에 반영되어 항상 최신 상태를 유지한다.
        - 쉬운 접근성
            - Swagger UI를 통해 개발자와 사용자들이 API를 쉽게 탐색하고 테스트할 수 있다.
- `mysql-connector-j`
    
    ```java
    <!-- MySql 데이터베이스에 연결하기 위한 JDBC 드라이버 -->
    <dependency>
    	<groupId>com.mysql</groupId>
    	<artifactId>mysql-connector-j</artifactId>
    </dependency>
    ```
    
    - Java 어플리케이션이 MySql 데이터베이스와 통신할 수 있도록 지원하는 **JDBC (Java Database Connectivity)** 드라이버를 제공한다.
    - 이 드라이버는 Java 어플리케이션과 MySql 데이터베이스 사이에 연결을 설정하고, SQL 쿼리를 실행하며, 데이터베이스로부터 결과를 가져오는 역할을 한다.
    - 위의 의존성을 추가하면 다음과 같은 기능들을 사용할 수 있다.
        - 데이터베이스 연결 설정
            - Java 어플리케이션에서 MySql 데이터베이스에 연결하기 위한 드라이버를 제공한다. 이 드라이버를 통해 Java 어플리케이션은 MySql 데이터베이스에 연결할 수 있다.
            - JDBC URL, 사용자 이름, 비밀번호 등의 연결 정보를 사용하여 데이터베이스 연결을 설정한다.
        - SQL 쿼리 실횅
            - SQL 쿼리를 MySql 데이터베이스로 전달하고 실행할 수 있다. 이를 통해 데이터의 C, R, U, D를 할 수 있다.
            - `statement`, `PreparedStatement`, `CallableStatement`와 같은 **JDBC** 인터페이스를 사용하여 SQL 쿼리를 실행한다.
        - 결과 집합 처리
            - SQL 쿼리의 결과를 ResultSet 객체로 받아와서 Java 어플리케이션에서 처리할 수 있도록 만들어준다. 이를 통해 데이터베이스에서 조회한 데이터를 **Java** 객체로 변환하여 사용할 수 있다.
            - 결과 집합을 반복(iterate)하여 각 행의 데이터를 읽어올 수 있다.
    - 예제
        - pom.xml
            
            ```java
            pom.xml
            
            <dependencies>
                <!-- MySql 데이터베이스에 연결하기 위한 JDBC 드라이버 -->
                <dependency>
                    <groupId>com.mysql</groupId>
                    <artifactId>mysql-connector-j</artifactId>
                </dependency>
            </dependencies>
            ```
            
        - application.properties
            
            ```java
            application.properties
            
            # MySQL 데이터베이스 연결 설정
            spring.datasource.url=jdbc:mysql://localhost:3306/mydatabase
            spring.datasource.username=myusername
            spring.datasource.password=mypassword
            spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
            
            # Hibernate 설정 (JPA를 사용할 경우)
            spring.jpa.hibernate.ddl-auto=update
            spring.jpa.show-sql=true
            ```
            
        - Application.java
            
            ```java
            Application.java
            
            import org.springframework.boot.SpringApplication;
            import org.springframework.boot.autoconfigure.SpringBootApplication;
            
            @SpringBootApplication
            public class Application {
                public static void main(String[] args) {
                    SpringApplication.run(Application.class, args);
                }
            }
            ```
            
        - User.java
            
            ```java
            User.java
            
            import javax.persistence.Entity;
            import javax.persistence.GeneratedValue;
            import javax.persistence.GenerationType;
            import javax.persistence.Id;
            
            @Entity
            public class User {
                @Id
                @GeneratedValue(strategy = GenerationType.IDENTITY)
                private Long id;
                private String name;
                private String email;
            
                // getters and setters
            }
            ```
            
        - UserRepository.java
            
            ```java
            UserRepository.java
            
            import org.springframework.data.jpa.repository.JpaRepository;
            
            public interface UserRepository extends JpaRepository<User, Long> {
            }
            ```
            
        - UserService.java
            
            ```java
            UserService.java
            
            import org.springframework.beans.factory.annotation.Autowired;
            import org.springframework.stereotype.Service;
            import java.util.List;
            
            @Service
            public class UserService {
            
                @Autowired
                private UserRepository userRepository;
            
                public List<User> getAllUsers() {
                    return userRepository.findAll();
                }
            
                public User getUserById(Long id) {
                    return userRepository.findById(id).orElse(null);
                }
            
                public User saveUser(User user) {
                    return userRepository.save(user);
                }
            
                public void deleteUser(Long id) {
                    userRepository.deleteById(id);
                }
            }
            
            ```
            
        - 설명
            - 의존성 : mysql-connector-j 의존성을 추가하면 Java 어플리케이션이 MySql 데이터베이스에 연결할 수 있다.
            - [application.properties](http://application.properties) : MySql 데이터베이스 연결 정보를 설정한다. JDBC URL, 사용자 이름, 비밀번호, 드라이버 클래스를 지정한다.
            - JPA Entity 및 Repository : JPA를 사용하여 User Entity와 UserRepository를 정의하고 이를 통해 데이터베이스와 상호작용한다.
            - 서비스 계층 : UserService 클래스는 Repository를 통해 데이터베이스 연산을 수행한다.
- `jjwt`
    
    ```java
    <!-- https://mvnrepository.com/artifact/io.jsonwebtoken/jjwt-api -->
    <!-- JSON Web Token(JWT)를 생성하고 검증하기 위한 라이브러리 -->
    <dependency>
        <groupId>io.jsonwebtoken</groupId>
        <artifactId>jjwt</artifactId>
        <version>0.9.1</version>
    </dependency>
    ```
    
    - Java 어플리케이션에서 **JSON Web Token(JWT)**를 생성하고 검증하는 데 사용되는 라이브러리이다.
    - **JWT**는 웹 어플리케이션에서 사용자 인증 및 정보 교환을 위한 표준화된 방식이다.
    - `jjwt`라이브러리는 **JWT 토큰**의 생성, 서명, 파싱 및 검증을 쉽게 할 수 있도록 도와준다.
    - 주요 역할
        - `jjwt`라이브러리는 **JWT 토큰**을 생성하는 기능을 제공한다.
        - **JWT**는 일반적으로 **헤더**, **페이로드**, **서명**으로 구성되며, 이 라이브러리를 사용하여 각 부분을 손쉽게 구성할 수 있다.
        - 예를 들어, 사용자 인증 정보를 기반으로 **JWT 토큰**을 생성하여 클라이언트에게 전달할 수 있다.
    - JWT 서명
        - 생성된 **JWT 토큰**에 서명을 추가하여 토큰의 무결성을 보장한다.
        - `jjwt` 라이브러리는 HMAC, RSA 등의 다양한 알고리즘을 지원하여 **JWT**에 서명할 수 있다.
        - 서명된 **JWT**는 토큰의 내용이 변조되지 않았음을 보장한다.
    - JWT 파싱 및 검증
        - 클라이언트로부터 받은 **JWT 토큰**을 파싱하여 페이로드에 포함된 정보를 추출할 수 있고 이 과정에서 토큰의 서명과 유효성을 검증한다.
        - 유효한 **JWT 토큰**인지 확인하고, 토큰이 만료되었는지, 변조되지 않았는지를 검증할 수 있다.
    - 클레임(Claims) 관리
        - **JWT**의 페이로드 부분에 포함되는 클레임(Claims)을 쉽게 설정하고 관리할 수 있다.
        - 클레임은 토큰에 포함된 사용자 정보, 만료 시간, 발급자 등의 데이터를 의미한다.
    - 예제
        - pom.xml
            
            ```java
            pom.xml
            
            <dependency>
                <groupId>io.jsonwebtoken</groupId>
                <artifactId>jjwt</artifactId>
                <version>0.9.1</version>
            </dependency>
            ```
            
        - JWT 유틸리티 클래스
            
            ```java
            JWT 유틸리티 클래스
            
            import io.jsonwebtoken.Jwts;
            import io.jsonwebtoken.SignatureAlgorithm;
            import io.jsonwebtoken.Claims;
            
            import java.util.Date;
            
            public class JwtUtil {
            
                private static final String SECRET_KEY = "mySecretKey";
            
                public static String generateToken(String username) {
                    return Jwts.builder()  // jwt를 만들 수 있는 빌더 인스턴스
                            .setSubject(username)  
                            .setIssuedAt(new Date())
                            .setExpiration(new Date(System.currentTimeMillis() + 1000 * 60 * 60 * 10))  // 10시간 후 만료
                            .signWith(SignatureAlgorithm.HS256, SECRET_KEY)
                            .compact();
                }
            
                public static Claims validateToken(String token) {
                    return Jwts.parser()
                            .setSigningKey(SECRET_KEY)
                            .parseClaimsJws(token)
                            .getBody();
                }
            }
            ```
            
        - JWT 생성 및 검증 테스트
            
            ```java
            JWT 생성 및 검증 테스트
            
            public class JwtTest {
            
                public static void main(String[] args) {
                    String token = JwtUtil.generateToken("username123");
                    System.out.println("Generated Token: " + token);
            
                    Claims claims = JwtUtil.validateToken(token);
                    System.out.println("Token Subject: " + claims.getSubject());
                    System.out.println("Token Expiration: " + claims.getExpiration());
                }
            }
            ```
            
        - 설명
            - JWT 생성
                - `generateToken` 메소드는 주어진 사용자 이름을 기반으로 **JWT 토큰**을 생성한다.
                - 이 토큰은 10시간 동안 유효하며, HMAC SHA-256 알고리즘을 사용하여 서명된다.
            - JWT 검증
                - `validateToken` 메소드는 주어진 **JWT 토큰**을 파싱하여 클레임을 추출한다.
                - 토큰의 서명을 검증하고, 유효하지 않은 토큰은 예외를 발생시킨다.
            - 클레임
                - JWT 페이로드에 포함되는 데이터로, `sutSubject` 메소드를 사용하여 사용자 이름을 설정하고, `setExpiration` 메소드를 사용하여 토큰의 만료 시간을 설정한다.
    - 주요 이점
        - 간편한 JWT 처리
            - `jjwt` 라이브러리는 **JWT 토큰**의 생성, 서명, 파싱 및 검증을 위한 간단하고 직관적인 API를 제공한다.
        - 다양한 알고리즘 지원
            - HMAC, RSA 등의 다양한 서명 알고리즘을 지원하여 보안 요구사항에 맞게 선택할 수 있다.
        - 클레임 관리
            - **JWT**의 페이로드에 포함되는 클레임을 쉽게 설정하고 추출할 수 있다.
    - JWT 설정하는 법
        
        ```java
        Map<String, String> headers = new HashMap<>();
        headers.put("typ", "JWT");
        
        String jwtKey = "sooa-seokmin-love-forever";
        
        Jwts.builder()  // JWT를 만들 수 있는 빌더 인스턴스
        .header()       // 빌더 헤더 객체로 만듦
        .add("name", "Yoo")  // key : value 형태로 추가할 수도 있고
        .add(headers)        // 위에서 정의한 map 객체 형태로 추가할 수도 있다.
        .and()          // JWT 빌더로 돌아간다.
        .subject("study")
        .expiration(new Date(System.currentTimeMillis() + 3000))  // 만료시점이 생성 후 3초이다.
        .signWith(SignatureAlgorithm.HS256, jwtKey.getBytes(StandardCharsets.UTF_8)).compact();  // 토큰의 완성
        
        jwt.io/#debugger-io
        ```
        
- `jaxb-api`
    
    ```java
    <!-- XML 바인딩을 위한 Java API -->
    <dependency>
        <groupId>javax.xml.bind</groupId>
        <artifactId>jaxb-api</artifactId>
        <version>2.3.1</version>
    </dependency>
    ```
    
    - Java 객체를 XML로 변환하고, XMl 데이터를 Java 객체로 변환하는 데 사용된다.
    - 이를 통해 XML 데이터를 쉽게 처리하고, Java 객체와 XML 간의 매핑을 간단하게 할 수 있다.
    - 주요 역할
        - Java 객체를 XML로 변환 (Marshalling)
            - JAXB를 사용하여 Java 객체를 XML 형식으로 변환할 수 있으며 이 과정을 마샬링(marshalling)이라 한다.
            - 예를 들어, Java 객체를 XML 파일이나 XML 문자열로 변환할 수 있다.
        - XML 객체를 Java 객체로 변환 (Unmarshalling)
            - JAXB를 사용하여 XML 데이터를 Java 객체로 변환할 수 있으며 이 과정을 언마샬링(unmarshalling)이라 한다.
            - XML 파일이나 XML 문자열을 Java 객체로 변환할 수 있다.
        - XML 스키마 생성
            - JAXB는 Java 클래스에서 XML 스키마(XSD)를 생성할 수 있는 기능도 제공한다.
            - 이를 통해 XML 데이터의 구조를 정의하고 검증할 수 있다.
        - JAXB 어노테이션 지원
            - JAXB는 다양한 어노테이션을 제공하여 Java 객체와 XML 간의 매핑을 정의할 수 있다.
            - 예를 들어, @XmlElement, @XmlAttribute, @XmlRootElement 등의 어노테이션을 사용하여 XML 요소와 속성을 Java 클래스에 매핑할 수 있다.
            - …