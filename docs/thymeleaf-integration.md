# Thymeleaf 与 Spring Boot 集成


在 `media-type`项目基础上，我们构建了一个新的项目`thymeleaf-in-action`。项目的包名也做了调整，改为`com.waylau.spring.boot.thymeleaf`。

## 所需环境

本例子采用的开发环境如下：

* Gradle 3.4
* Spring Boot 1.5.2.RELEASE 
* Thymeleaf 3.0.3.RELEASE
* Thymeleaf Layout Dialect 2.2.0


## build.gradle

修改 build.gradle 文件，让我们的`thymeleaf-in-action`项目成为一个新的项目。

修改内容也比较简单，修改项目名称及版本即可。

```groovy
jar {
	baseName = 'thymeleaf-in-action'
	version = '1.0.0'
}
```

近期 Spring Boot 版本做了升级，我们升级到最新的版本：

```groovy
ext {
	springBootVersion = '1.5.2.RELEASE'
}
```
同时，我们需要添加 Thymeleaf 的依赖。

```groovy
// 依赖关系
dependencies {
	...
 
	// 添加 Thymeleaf 的依赖
	compile('org.springframework.boot:spring-boot-starter-thymeleaf')
	
 	...
}
```

	
	
由于 `spring-boot-starter-thymeleaf`库，默认使用的是 Thymeleaf 2.1 版本。为了学习最前沿的技术，我们采用了 Thymeleaf 最新的版本[Thymeleaf 3.0.3](http://www.thymeleaf.org/)。我们要使用Thymeleaf 3去替换 Spring Boot 依赖库中的thymeleaf和thymeleaf-layout-dialect版本号，如下：


```groovy
buildscript {
 	...	
 	
	// 自定义 Thymeleaf 和 Thymeleaf Layout Dialect 的版本
	ext['thymeleaf.version'] = '3.0.3.RELEASE'
	ext['thymeleaf-layout-dialect.version'] = '2.2.0'
	
	...
}
```


## 升级 Gradle Wrapper

由于近期 Gradle 刚升级到了 3.4 版本，所以，我们紧跟潮流，设置 Gradle Wrapper使用 3.4 最新版本。

修改`gradle/wrapper/gradle-wrapper.properties`文件：

```
distributionUrl=https\://services.gradle.org/distributions/gradle-3.4-bin.zip
```
