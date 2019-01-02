# 전체 빌드

geth, ethereum, solc 등 설치
```
mvn -DskipTests=true clean package
```

war 파일 생성
```
mvn war:war
```

# cakeshop-api

메인 어플리케이션

## 주요 URL

```
http://127.0.0.1:8080/cakeshop/index.html # 메뉴 포함
http://127.0.0.1:8080/cakeshop/sandbox.html
http://127.0.0.1:8080/cakeshop/swagger-ui.html
```

## index-gen.js 생성

```
cakeshop/cakeshop-api/src/main/resources/static
npm run build # 빌드
npm run start # 테스트 ( js 자동 빌드 )
```

## geth 등 설정 파일 위치

각 환경별로 설정 따로 할 수 있음. 따로 설정이 없으면 application-local.properties 사용. ( -Dspring.profiles.active=local )

```
cakeshop/cakeshop-api/src/main/resources/config
```

# cakeshop-client-js

cakeshop-api 에서 사용하는 cakeshop.js 를 생성해줌. 빌드후 cakeshop/cakeshop-api/src/main/resources/static/js/vondor 에 복사됨.

```
cakeshop/cakeshop-client-js/src/main/javascript$ ./node_modules/gulp/bin/gulp.js install
```

# cakeshop-node-manager

노드 관리, cakeshop-client-java 에서 호출

# cakeshop-abi

ABI 모델 파일, cakeshop-api에 의존성

# cakeshop-client-java

cakeshop-api 와 cakeshop-node-manager 에서 쓰는 api

# cakeshop-client-java-sample

cakeshop-client-java 사용 예제

# cakeshop-client-java-codegen

AppConfig에 @Primary 추가

```java
    @Bean
    @Primary
    public AnnotationMBeanExporter annotationMBeanExporter() {
        AnnotationMBeanExporter annotationMBeanExporter = new AnnotationMBeanExporter();
        annotationMBeanExporter.addExcludedBean("dataSource");
        return annotationMBeanExporter;
    }
```

```xml
/usr/lib/jvm/java-1.11.0-openjdk-amd64/bin/java -agentlib:jdwp=transport=dt_socket,address=127.0.0.1:45185,suspend=y,server=n -XX:TieredStopAtLevel=1 -noverify -Dspring.output.ansi.enabled=always -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=41843 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false -Djava.rmi.server.hostname=localhost -Dspring.liveBeansView.mbeanDomain -Dspring.application.admin.enabled=true -javaagent:/home/tei/tools/idea-IU-183.4886.37/lib/rt/debugger-agent.jar -Dfile.encoding=UTF-8 -classpath /home/tei/IdeaProjects/cakeshop/cakeshop-api/target/classes:/home/tei/IdeaProjects/cakeshop/cakeshop-abi/target/classes:/home/tei/.m2/repository/org/springframework/boot/spring-boot-starter-web/1.4.3.RELEASE/spring-boot-starter-web-1.4.3.RELEASE.jar:/home/tei/.m2/repository/org/hibernate/hibernate-validator/5.2.4.Final/hibernate-validator-5.2.4.Final.jar:/home/tei/.m2/repository/javax/validation/validation-api/1.1.0.Final/validation-api-1.1.0.Final.jar:/home/tei/.m2/repository/org/springframework/spring-web/4.3.5.RELEASE/spring-web-4.3.5.RELEASE.jar:/home/tei/.m2/repository/org/springframework/spring-webmvc/4.3.5.RELEASE/spring-webmvc-4.3.5.RELEASE.jar:/home/tei/.m2/repository/org/springframework/spring-expression/4.3.5.RELEASE/spring-expression-4.3.5.RELEASE.jar:/home/tei/.m2/repository/org/springframework/boot/spring-boot-starter/1.4.3.RELEASE/spring-boot-starter-1.4.3.RELEASE.jar:/home/tei/.m2/repository/org/springframework/boot/spring-boot/1.4.3.RELEASE/spring-boot-1.4.3.RELEASE.jar:/home/tei/.m2/repository/org/springframework/boot/spring-boot-autoconfigure/1.4.3.RELEASE/spring-boot-autoconfigure-1.4.3.RELEASE.jar:/home/tei/.m2/repository/org/springframework/spring-core/4.3.5.RELEASE/spring-core-4.3.5.RELEASE.jar:/home/tei/.m2/repository/org/yaml/snakeyaml/1.17/snakeyaml-1.17.jar:/home/tei/.m2/repository/org/springframework/boot/spring-boot-starter-log4j2/1.4.3.RELEASE/spring-boot-starter-log4j2-1.4.3.RELEASE.jar:/home/tei/.m2/repository/org/apache/logging/log4j/log4j-slf4j-impl/2.6.2/log4j-slf4j-impl-2.6.2.jar:/home/tei/.m2/repository/org/apache/logging/log4j/log4j-api/2.6.2/log4j-api-2.6.2.jar:/home/tei/.m2/repository/org/apache/logging/log4j/log4j-core/2.6.2/log4j-core-2.6.2.jar:/home/tei/.m2/repository/org/slf4j/jcl-over-slf4j/1.7.7/jcl-over-slf4j-1.7.7.jar:/home/tei/.m2/repository/org/slf4j/jul-to-slf4j/1.7.7/jul-to-slf4j-1.7.7.jar:/home/tei/.m2/repository/org/springframework/boot/spring-boot-starter-actuator/1.4.3.RELEASE/spring-boot-starter-actuator-1.4.3.RELEASE.jar:/home/tei/.m2/repository/org/springframework/boot/spring-boot-actuator/1.4.3.RELEASE/spring-boot-actuator-1.4.3.RELEASE.jar:/home/tei/.m2/repository/org/springframework/boot/spring-boot-starter-security/1.4.3.RELEASE/spring-boot-starter-security-1.4.3.RELEASE.jar:/home/tei/.m2/repository/org/springframework/spring-aop/4.3.5.RELEASE/spring-aop-4.3.5.RELEASE.jar:/home/tei/.m2/repository/org/springframework/security/spring-security-config/4.1.4.RELEASE/spring-security-config-4.1.4.RELEASE.jar:/home/tei/.m2/repository/org/springframework/security/spring-security-core/4.1.4.RELEASE/spring-security-core-4.1.4.RELEASE.jar:/home/tei/.m2/repository/org/springframework/security/spring-security-web/4.1.4.RELEASE/spring-security-web-4.1.4.RELEASE.jar:/home/tei/.m2/repository/org/springframework/hateoas/spring-hateoas/0.20.0.RELEASE/spring-hateoas-0.20.0.RELEASE.jar:/home/tei/.m2/repository/org/springframework/spring-beans/4.3.5.RELEASE/spring-beans-4.3.5.RELEASE.jar:/home/tei/.m2/repository/org/springframework/spring-context/4.3.5.RELEASE/spring-context-4.3.5.RELEASE.jar:/home/tei/.m2/repository/org/slf4j/slf4j-api/1.7.7/slf4j-api-1.7.7.jar:/home/tei/.m2/repository/org/springframework/plugin/spring-plugin-core/1.2.0.RELEASE/spring-plugin-core-1.2.0.RELEASE.jar:/home/tei/.m2/repository/org/springframework/spring-context-support/4.3.5.RELEASE/spring-context-support-4.3.5.RELEASE.jar:/home/tei/.m2/repository/org/springframework/boot/spring-boot-starter-jetty/1.4.3.RELEASE/spring-boot-starter-jetty-1.4.3.RELEASE.jar:/home/tei/.m2/repository/org/eclipse/jetty/jetty-servlets/9.2.19.v20160908/jetty-servlets-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/jetty-continuation/9.2.19.v20160908/jetty-continuation-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/jetty-http/9.2.19.v20160908/jetty-http-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/jetty-util/9.2.19.v20160908/jetty-util-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/jetty-io/9.2.19.v20160908/jetty-io-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/jetty-webapp/9.2.19.v20160908/jetty-webapp-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/jetty-xml/9.2.19.v20160908/jetty-xml-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/jetty-servlet/9.2.19.v20160908/jetty-servlet-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/jetty-security/9.2.19.v20160908/jetty-security-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/jetty-server/9.2.19.v20160908/jetty-server-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/websocket/websocket-server/9.2.19.v20160908/websocket-server-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/websocket/websocket-common/9.2.19.v20160908/websocket-common-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/websocket/websocket-api/9.2.19.v20160908/websocket-api-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/websocket/websocket-client/9.2.19.v20160908/websocket-client-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/websocket/websocket-servlet/9.2.19.v20160908/websocket-servlet-9.2.19.v20160908.jar:/home/tei/.m2/repository/javax/servlet/javax.servlet-api/3.1.0/javax.servlet-api-3.1.0.jar:/home/tei/.m2/repository/org/eclipse/jetty/websocket/javax-websocket-server-impl/9.2.19.v20160908/javax-websocket-server-impl-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/jetty-annotations/9.2.19.v20160908/jetty-annotations-9.2.19.v20160908.jar:/home/tei/.m2/repository/org/eclipse/jetty/jetty-plus/9.2.19.v20160908/jetty-plus-9.2.19.v20160908.jar:/home/tei/.m2/repository/javax/annotation/javax.annotation-api/1.2/javax.annotation-api-1.2.jar:/home/tei/.m2/repository/org/ow2/asm/asm/5.0.1/asm-5.0.1.jar:/home/tei/.m2/repository/org/ow2/asm/asm-commons/5.0.1/asm-commons-5.0.1.jar:/home/tei/.m2/repository/org/ow2/asm/asm-tree/5.0.1/asm-tree-5.0.1.jar:/home/tei/.m2/repository/org/eclipse/jetty/websocket/javax-websocket-client-impl/9.2.19.v20160908/javax-websocket-client-impl-9.2.19.v20160908.jar:/home/tei/.m2/repository/javax/websocket/javax.websocket-api/1.0/javax.websocket-api-1.0.jar:/home/tei/.m2/repository/org/mortbay/jasper/apache-el/8.0.33/apache-el-8.0.33.jar:/home/tei/.m2/repository/org/freemarker/freemarker/2.3.25-incubating/freemarker-2.3.25-incubating.jar:/home/tei/.m2/repository/org/springframework/spring-messaging/4.3.5.RELEASE/spring-messaging-4.3.5.RELEASE.jar:/home/tei/.m2/repository/org/springframework/spring-websocket/4.3.5.RELEASE/spring-websocket-4.3.5.RELEASE.jar:/home/tei/.m2/repository/org/springframework/spring-tx/4.3.5.RELEASE/spring-tx-4.3.5.RELEASE.jar:/home/tei/.m2/repository/org/springframework/spring-orm/4.3.5.RELEASE/spring-orm-4.3.5.RELEASE.jar:/home/tei/.m2/repository/org/springframework/spring-jdbc/4.3.5.RELEASE/spring-jdbc-4.3.5.RELEASE.jar:/home/tei/.m2/repository/org/hibernate/hibernate-core/5.1.0.Final/hibernate-core-5.1.0.Final.jar:/home/tei/.m2/repository/org/jboss/logging/jboss-logging/3.3.0.Final/jboss-logging-3.3.0.Final.jar:/home/tei/.m2/repository/org/hibernate/javax/persistence/hibernate-jpa-2.1-api/1.0.0.Final/hibernate-jpa-2.1-api-1.0.0.Final.jar:/home/tei/.m2/repository/org/javassist/javassist/3.20.0-GA/javassist-3.20.0-GA.jar:/home/tei/.m2/repository/antlr/antlr/2.7.7/antlr-2.7.7.jar:/home/tei/.m2/repository/org/apache/geronimo/specs/geronimo-jta_1.1_spec/1.1.1/geronimo-jta_1.1_spec-1.1.1.jar:/home/tei/.m2/repository/org/jboss/jandex/2.0.0.Final/jandex-2.0.0.Final.jar:/home/tei/.m2/repository/com/fasterxml/classmate/1.3.3/classmate-1.3.3.jar:/home/tei/.m2/repository/dom4j/dom4j/1.6.1/dom4j-1.6.1.jar:/home/tei/.m2/repository/xml-apis/xml-apis/1.4.01/xml-apis-1.4.01.jar:/home/tei/.m2/repository/org/hibernate/common/hibernate-commons-annotations/5.0.1.Final/hibernate-commons-annotations-5.0.1.Final.jar:/home/tei/.m2/repository/org/hsqldb/hsqldb/2.3.3/hsqldb-2.3.3.jar:/home/tei/.m2/repository/mysql/mysql-connector-java/5.1.9/mysql-connector-java-5.1.9.jar:/home/tei/.m2/repository/org/postgresql/postgresql/9.3-1102-jdbc41/postgresql-9.3-1102-jdbc41.jar:/home/tei/.m2/repository/com/fasterxml/jackson/core/jackson-annotations/2.6.3/jackson-annotations-2.6.3.jar:/home/tei/.m2/repository/com/fasterxml/jackson/core/jackson-core/2.6.3/jackson-core-2.6.3.jar:/home/tei/.m2/repository/com/fasterxml/jackson/core/jackson-databind/2.6.3/jackson-databind-2.6.3.jar:/home/tei/.m2/repository/com/google/guava/guava/19.0/guava-19.0.jar:/home/tei/.m2/repository/io/dropwizard/metrics/metrics-core/3.1.2/metrics-core-3.1.2.jar:/home/tei/.m2/repository/commons-io/commons-io/2.5/commons-io-2.5.jar:/home/tei/.m2/repository/org/apache/commons/commons-collections4/4.1/commons-collections4-4.1.jar:/home/tei/.m2/repository/org/apache/commons/commons-lang3/3.3.2/commons-lang3-3.3.2.jar:/home/tei/.m2/repository/org/apache/commons/commons-math3/3.6/commons-math3-3.6.jar:/home/tei/.m2/repository/com/squareup/okhttp3/okhttp/3.2.0/okhttp-3.2.0.jar:/home/tei/.m2/repository/com/squareup/okio/okio/1.6.0/okio-1.6.0.jar:/home/tei/.m2/repository/com/jcabi/jcabi-manifests/1.1/jcabi-manifests-1.1.jar:/home/tei/.m2/repository/org/bouncycastle/bcprov-jdk15on/1.52/bcprov-jdk15on-1.52.jar:/home/tei/.m2/repository/net/java/dev/jna/jna-platform/4.1.0/jna-platform-4.1.0.jar:/home/tei/.m2/repository/net/java/dev/jna/jna/4.2.2/jna-4.2.2.jar:/home/tei/.m2/repository/org/aspectj/aspectjweaver/1.8.9/aspectjweaver-1.8.9.jar:/home/tei/.m2/repository/org/thymeleaf/thymeleaf-spring4/2.1.4.RELEASE/thymeleaf-spring4-2.1.4.RELEASE.jar:/home/tei/.m2/repository/org/thymeleaf/thymeleaf/2.1.5.RELEASE/thymeleaf-2.1.5.RELEASE.jar:/home/tei/.m2/repository/ognl/ognl/3.0.8/ognl-3.0.8.jar:/home/tei/.m2/repository/org/unbescape/unbescape/1.1.0.RELEASE/unbescape-1.1.0.RELEASE.jar:/home/tei/.m2/repository/org/thymeleaf/extras/thymeleaf-extras-springsecurity4/2.1.3.RELEASE/thymeleaf-extras-springsecurity4-2.1.3.RELEASE.jar:/home/tei/.m2/repository/nz/net/ultraq/thymeleaf/thymeleaf-layout-dialect/2.2.0/thymeleaf-layout-dialect-2.2.0.jar:/home/tei/.m2/repository/org/codehaus/groovy/groovy/2.4.7/groovy-2.4.7.jar:/home/tei/.m2/repository/nz/net/ultraq/thymeleaf/thymeleaf-expression-processor/1.1.2/thymeleaf-expression-processor-1.1.2.jar:/home/tei/.m2/repository/io/springfox/springfox-swagger2/2.6.1/springfox-swagger2-2.6.1.jar:/home/tei/.m2/repository/io/swagger/swagger-annotations/1.5.10/swagger-annotations-1.5.10.jar:/home/tei/.m2/repository/io/swagger/swagger-models/1.5.10/swagger-models-1.5.10.jar:/home/tei/.m2/repository/io/springfox/springfox-spi/2.6.1/springfox-spi-2.6.1.jar:/home/tei/.m2/repository/io/springfox/springfox-core/2.6.1/springfox-core-2.6.1.jar:/home/tei/.m2/repository/io/springfox/springfox-schema/2.6.1/springfox-schema-2.6.1.jar:/home/tei/.m2/repository/io/springfox/springfox-swagger-common/2.6.1/springfox-swagger-common-2.6.1.jar:/home/tei/.m2/repository/io/springfox/springfox-spring-web/2.6.1/springfox-spring-web-2.6.1.jar:/home/tei/.m2/repository/org/springframework/plugin/spring-plugin-metadata/1.2.0.RELEASE/spring-plugin-metadata-1.2.0.RELEASE.jar:/home/tei/.m2/repository/org/mapstruct/mapstruct/1.0.0.Final/mapstruct-1.0.0.Final.jar:/home/tei/.m2/repository/io/springfox/springfox-swagger-ui/2.6.1/springfox-swagger-ui-2.6.1.jar:/home/tei/.m2/repository/org/springframework/spring-test/4.3.5.RELEASE/spring-test-4.3.5.RELEASE.jar:/home/tei/tools/idea-IU-183.4886.37/lib/idea_rt.jar com.jpmorgan.cakeshop.config.SpringBootApplication
Connected to the target VM, address: '127.0.0.1:45185', transport: 'socket'
OpenJDK 64-Bit Server VM warning: Sharing is only supported for boot loader classes because bootstrap classpath has been appended
Defaulting to spring profile: local
[INFO ] 2019-01-01 17:53:17.159 [main] SpringBootApplication - Starting SpringBootApplication on tei-notebook with PID 12745 (/home/tei/IdeaProjects/cakeshop/cakeshop-api/target/classes started by tei in /home/tei/IdeaProjects/cakeshop)
[INFO ] 2019-01-01 17:53:17.169 [main] SpringBootApplication - The following profiles are active: container,spring-boot,local
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.codehaus.groovy.reflection.CachedClass$3$1 (file:/home/tei/.m2/repository/org/codehaus/groovy/groovy/2.4.7/groovy-2.4.7.jar) to method java.lang.Object.finalize()
WARNING: Please consider reporting this to the maintainers of org.codehaus.groovy.reflection.CachedClass$3$1
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
[INFO ] 2019-01-01 17:53:26.298 [main] AppConfig - eth.config.dir=/home/tei/IdeaProjects/cakeshop/data/local
[WARN ] 2019-01-01 17:53:26.300 [main] AppConfig - Authentication disabled.
[INFO ] 2019-01-01 17:53:26.342 [main] AppConfig - Loading config from /home/tei/IdeaProjects/cakeshop/data/local/application.properties
[INFO ] 2019-01-01 17:53:50.904 [main] MetricsBlockListener - Stopping MetricsBlockListener (thread id=90)
[INFO ] 2019-01-01 17:53:51.217 [main] GethHttpServiceImpl - Stopping geth
[INFO ] 2019-01-01 17:53:51.395 [main] GethHttpServiceImpl - Stopping Constellation with pid 13198
[INFO ] 2019-01-01 17:53:51.406 [main] GethHttpServiceImpl - Stopping solc daemon
[ERROR] 2019-01-01 17:53:52.415 [main] LoggingFailureAnalysisReporter -

***************************
APPLICATION FAILED TO START
***************************

Description:

Constructor in org.springframework.boot.autoconfigure.admin.SpringApplicationAdminJmxAutoConfiguration required a single bean, but 2 were found:
	- annotationMBeanExporter: defined by method 'annotationMBeanExporter' in class path resource [com/jpmorgan/cakeshop/config/AppConfig.class]
	- endpointMBeanExporter: defined by method 'endpointMBeanExporter' in class path resource [org/springframework/boot/actuate/autoconfigure/EndpointMBeanExportAutoConfiguration.class]


Action:

Consider marking one of the beans as @Primary, updating the consumer to accept multiple beans, or using @Qualifier to identify the bean that should be consumed

Disconnected from the target VM, address: '127.0.0.1:45185', transport: 'socket'

Process finished with exit code 1

```