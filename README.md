# spring-actuator
spring actuator


## config

### 1. gradle 추가  

- 스프링 버전에 맞는 버전 설치
``` kotlin
// https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-actuator
implementation("org.springframework.boot:spring-boot-starter-actuator:${버전}")
```
### 2. 마이크로미터에서 프로메테우스를 사용하기 위한 gradle 추가
```kotlin
	// https://mvnrepository.com/artifact/io.micrometer/micrometer-registry-prometheus
	implementation("io.micrometer:micrometer-registry-prometheus:1.11.4")
```  
(옵션) actuator/info에서 git정보 설정 확인을 위한 git.properties 파일 생성을 위한 플러그인 추가
git으로 형상관리가 되지 않으면 빌드에러 발생함 주의
```kotlin
plugin{
	//https://docs.spring.io/spring-boot/docs/current/reference/html/howto.html#howto.build.generate-git-info
	id("com.gorylenko.gradle-git-properties") version "2.4.1"
}
```
info 접근시에 에러페이지 발생시에 참조 -> https://github.com/munseop-sim/spring-actuator/issues/3

### 3. 프로메테우스에서 tomcat정보 노출을 위한 설정
**actuator관련 설정인 management하위에 설정하는거 아님!**

```yml
# server
server:
  tomcat:
    mbeanregistry:
      enabled: true
  

```
