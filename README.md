# gradle-tutorial

## gradle folder file info
cmd - gradlew build --> builds successful how?\
gradlew.bat ---> wrapper to execute on windows\
gradlew --> for mac and linux\
settings.gradle -->  only one file per gradle, contains root project and modules
included in the project (** multi-module or single module here)
## Module structure
src  --> packages, java classes, resources (tests)
build.gradle\
build folder --> compiled classes, test reports, libs folder --> module exec here
```
 gradlew clean
 ```
removes build folder
```
cmd - gradlew test
```
goes to all module tests -> exec tests -> generate test results @ app/build/reports/tests...\
This test results can be integration in jenkins.
```
gradlew test -p <submodule path> eg. my-webapp/
```
** no new classes or test results created as that can be cached if already\
ran earlier (gradle is smart!!!!!!!!! saves time!!!!!)\

## build.gradle structure

*dependencies come from repositories.
```
repositories {
   mavenCentral()
}

dependencies {
   implementation 'org.springframework.boot:spring-boot-starter-actuator'
   implementation 'org.springframework.boot:spring-boot-starter-web'
   implementation project(':my-backend')              // reference other project
   testImplementation 'org.springframework.boot:spring-boot-starter-test'
}
```
implementation vs testImplementation ---> dependency scopes --> eg. dependency will be available during compile or compilation of tests

** backend-app (module) ---> my-webapp (module)
but implementation in backend-app not accessible in my-webapp, use api '<dependency>' i.e. api scope\
but it will not work, need plugin
```
plugins {
   id 'org.springframework.boot' version '2.6.3'
   id 'io.spring.dependency-management' version '1.0.11.RELEASE'
   id 'java'
}
```
```
group = 'com.example'
version = '0.0.1-SNAPSHOT'
sourceCompatibility = '1.8
```

## How to create gradle project from scratch?

1\. install gradle

2\. ProjectFolder/    ---> gradle init\
                            --> select sub other instructions.\
voila!!!!!!!!!!! Project created.
