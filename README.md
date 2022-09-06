# MyBatis integration with Spring Native feature

[![Java CI](https://github.com/mybatis/spring-native/actions/workflows/ci.yaml/badge.svg)](https://github.com/mybatis/spring-native/actions/workflows/ci.yaml)
[![Samples](https://github.com/mybatis/spring-native/actions/workflows/samples.yaml/badge.svg)](https://github.com/mybatis/spring-native/actions/workflows/samples.yaml)
[![Coverage Status](https://coveralls.io/repos/github/mybatis/spring-native/badge.svg?branch=master)](https://coveralls.io/github/mybatis/spring-native?branch=master)
[![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=mybatis_spring-native&metric=reliability_rating)](https://sonarcloud.io/summary/new_code?id=mybatis_spring-native)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=mybatis_spring-native&metric=security_rating)](https://sonarcloud.io/summary/new_code?id=mybatis_spring-native)
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=mybatis_spring-native&metric=sqale_rating)](https://sonarcloud.io/summary/new_code?id=mybatis_spring-native)

[![Maven central](https://maven-badges.herokuapp.com/maven-central/org.mybatis.spring.native/mybatis-spring-native/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.mybatis.spring.native/mybatis-spring-native)
[![Sonatype Nexus (Snapshots)](https://img.shields.io/nexus/s/https/oss.sonatype.org/org.mybatis.spring.native/mybatis-spring-native.svg)](https://oss.sonatype.org/content/repositories/snapshots/org/mybatis/spring/native/mybatis-spring-native/)
[![License](https://img.shields.io/:license-apache-brightgreen.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)

![mybatis-spring](http://mybatis.github.io/images/mybatis-logo.png)

The project that the MyBatis integration with Spring Native feature.

## Requirements

* Java 11+
* [GraalVM](https://github.com/graalvm/graalvm-ce-builds/releases)
* [Spring Boot](https://github.com/spring-projects/spring-boot) 2.6.3+
* [Spring Native](https://github.com/spring-projects-experimental/spring-native) 0.11.2+
* [MyBatis Spring](https://github.com/mybatis/spring) 2.0.7+
* [MyBatis Spring Boot](https://github.com/mybatis/spring-boot-starter) 2.2.2+

## Essentials

* [Quick Start](https://github.com/mybatis/spring-native/wiki/Quick-Start)
* [Reference documentation](docs/src/site/markdown/index.md)

### Translations

* [Reference documentation (简体中文)](docs/src/site/zh/markdown/index.md)
* [Reference documentation (한국어)](docs/src/site/ko/markdown/index.md)

## How to install on your application

Specify the `mybatis-spring-native-core` on `pom.xml` as follows:

**Maven:**

```xml
<dependencies>
  <dependency>
    <groupId>org.mybatis.spring.native</groupId>
    <artifactId>mybatis-spring-native-core</artifactId>
    <version>0.1.0-SNAPSHOT</version>
  </dependency>
</dependencies>
```

**Gradle:**

```groovy
dependencies {
  compile("org.mybatis.spring.native:mybatis-spring-native-core:0.1.0-SNAPSHOT")
}
```

If you use other extension modules provided by mybatis, please specify the `mybatis-spring-native-extensions` instead of `mybatis-spring-native-core`.

**Maven:**

```xml
<dependencies>
  <dependency>
    <groupId>org.mybatis.spring.native</groupId>
    <artifactId>mybatis-spring-native-extensions</artifactId>
    <version>0.1.0-SNAPSHOT</version>
  </dependency>
</dependencies>
```

**Gradle:**

```groovy
dependencies {
  compile("org.mybatis.spring.native:mybatis-spring-native-extensions:0.1.0-SNAPSHOT")
}
```

Add Sonatype OSS snapshot repository when use MyBatis's snapshot modules.

**Maven:**

```xml
<repositories>
  <repository>
    <id>sonatype-oss-snapshots</id>
    <name>Sonatype OSS Snapshots Repository</name>
   <url>https://oss.sonatype.org/content/repositories/snapshots</url>
  </repository>
</repositories>
```

**Gradle:**

```groovy
repositories {
  maven { url "https://oss.sonatype.org/content/repositories/snapshots" }
}
```

## How to build

If you want to build this project, please will execute following procedures.

> **NOTE: Pre Conditions**
>
> Need to following environment variables are defined.
>
> * `JAVA_HOME`
> * `GRAALVM_HOME`

### All modules

```
./mvnw -Pnative clean package
```
> **WARNING:**
>
> **Building all modules takes long time.**


### Core module and specific sample module

```
./mvnw -pl core,samples/simple -Pnative clean package
```

> **NOTE:**
>
> Please replace the 'simple' part  on above example to sample's suffix value(e.g. xml, sqlprovider and more) that you want to build.

### Extension module and specific sample module

```
./mvnw -pl core,extensions,samples/thymeleaf -Pnative clean package
```

## How to run a sample

Execute the following command when the build is completed.

### Run with Native Image


```
./samples/simple/target/mybatis-spring-native-sample-simple
```

```
2022-01-22 13:45:10.453  INFO 2265 --- [           main] o.s.nativex.NativeListener               : AOT mode enabled

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::                (v2.6.3)

2022-01-22 13:45:10.455  INFO 2265 --- [           main] s.s.MybatisSpringNativeSampleApplication : Starting MybatisSpringNativeSampleApplication v0.1.0-SNAPSHOT using Java 17.0.1 on fv-az136-971 with PID 2265 (/home/runner/work/mybatis-spring-native/mybatis-spring-native/samples/simple/target/mybatis-spring-native-sample-simple started by runner in /home/runner/work/mybatis-spring-native/mybatis-spring-native)
2022-01-22 13:45:10.455  INFO 2265 --- [           main] s.s.MybatisSpringNativeSampleApplication : No active profile set, falling back to default profiles: default
2022-01-22 13:45:10.487  INFO 2265 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Starting...
2022-01-22 13:45:10.491  INFO 2265 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Start completed.
2022-01-22 13:45:10.496  INFO 2265 --- [           main] s.s.MybatisSpringNativeSampleApplication : Started MybatisSpringNativeSampleApplication in 0.054 seconds (JVM running for 0.056)
2022-01-22 13:45:10.497  INFO 2265 --- [           main] s.s.MybatisSpringNativeSampleApplication : New city: City{id=4, name='NYC', state='NY', country='USA'}
2022-01-22 13:45:10.497  INFO 2265 --- [           main] s.s.MybatisSpringNativeSampleApplication : City{id=1, name='San Francisco', state='CA', country='USA'}
2022-01-22 13:45:10.497  INFO 2265 --- [           main] s.s.MybatisSpringNativeSampleApplication : City{id=2, name='Boston', state='MA', country='USA'}
2022-01-22 13:45:10.497  INFO 2265 --- [           main] s.s.MybatisSpringNativeSampleApplication : City{id=3, name='Portland', state='OR', country='USA'}
2022-01-22 13:45:10.497  INFO 2265 --- [           main] s.s.MybatisSpringNativeSampleApplication : City{id=4, name='NYC', state='NY', country='USA'}
2022-01-22 13:45:10.498  INFO 2265 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown initiated...
2022-01-22 13:45:10.499  INFO 2265 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown completed.
```

### Run with executable jar

```
./samples/simple/target/mybatis-spring-native-sample-simple-exec.jar
```

```
2022-01-22 13:45:14.191  INFO 2305 --- [           main] o.s.nativex.NativeListener               : AOT mode disabled

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::                (v2.6.3)

2022-01-22 13:45:14.295  INFO 2305 --- [           main] s.s.MybatisSpringNativeSampleApplication : Starting MybatisSpringNativeSampleApplication v0.1.0-SNAPSHOT using Java 17.0.1 on fv-az136-971 with PID 2305 (/home/runner/work/mybatis-spring-native/mybatis-spring-native/samples/simple/target/mybatis-spring-native-sample-simple-0.1.0-SNAPSHOT-exec.jar started by runner in /home/runner/work/mybatis-spring-native/mybatis-spring-native)
2022-01-22 13:45:14.296  INFO 2305 --- [           main] s.s.MybatisSpringNativeSampleApplication : No active profile set, falling back to default profiles: default
2022-01-22 13:45:15.349  INFO 2305 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Starting...
2022-01-22 13:45:15.578  INFO 2305 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Start completed.
2022-01-22 13:45:15.718  INFO 2305 --- [           main] s.s.MybatisSpringNativeSampleApplication : Started MybatisSpringNativeSampleApplication in 1.892 seconds (JVM running for 2.406)
2022-01-22 13:45:15.774  INFO 2305 --- [           main] s.s.MybatisSpringNativeSampleApplication : New city: City{id=4, name='NYC', state='NY', country='USA'}
2022-01-22 13:45:15.804  INFO 2305 --- [           main] s.s.MybatisSpringNativeSampleApplication : City{id=1, name='San Francisco', state='CA', country='USA'}
2022-01-22 13:45:15.805  INFO 2305 --- [           main] s.s.MybatisSpringNativeSampleApplication : City{id=2, name='Boston', state='MA', country='USA'}
2022-01-22 13:45:15.805  INFO 2305 --- [           main] s.s.MybatisSpringNativeSampleApplication : City{id=3, name='Portland', state='OR', country='USA'}
2022-01-22 13:45:15.806  INFO 2305 --- [           main] s.s.MybatisSpringNativeSampleApplication : City{id=4, name='NYC', state='NY', country='USA'}
2022-01-22 13:45:15.816  INFO 2305 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown initiated...
2022-01-22 13:45:15.823  INFO 2305 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown completed.
```

## Related Links

* https://spring.io/blog/2021/12/29/go-go-graalvm-with-spring-native-my-adventures-in-native-image-ville
* https://joshlong.com/jl/blogPost/mybatis-and-spring-native.html
* https://github.com/spring-projects-experimental/spring-native/issues/404
* https://www.youtube.com/watch?v=EWWq3ts9Tv4&t=1s

## Special Thanks

Thanks for helping this project creation!!

* Josh Long([@joshlong](https://github.com/joshlong))  
  Josh provided [the first sample application](https://github.com/joshlong/mybatis-spring-native/tree/mybatis-spring).


* Stéphane Nicoll([@snicoll](https://github.com/snicoll))  
  Stéphane resolved and helped some issues for running MyBatis on native image. 
