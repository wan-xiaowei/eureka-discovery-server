
##详解: http://blog.csdn.net/beyannanfei/article/details/52069725

修改hosts文件;127.0.0.1  discovery discovery2

server:
  context-path: /eureka-server
  port: 8761
debug: false

eureka:
  instance:
    hostname : discovery
  client:
    registerWithEureka: false  #是否将eureka自身作为应用注册到eureka注册中心
    fetchRegistry: false       #为true时，可以启动，但报异常：Cannot execute request on any known server
    serviceUrl :
       defaultZone : http://${eureka.instance.hostname}:${server.port}/eureka/

##注意：
  用1.5.1搭建了一个spring Cloud的环境 但是Eureka 一直报 Java.lang.ClassNotFoundException: org.springframework.boot.context.embedded.FilterRegistrationBean 我看了一些更新说明 说是 spring boot 1.4以后 FilterRegistrationBean的位置换到了 org.springframework.boot.web.servlet 下面 
  修改springcloud版本到 Camden.SR6 即可
  但是，Git了 作者的全部代码 运行正常 不报错。。
  目前的结论： 
  旧版本的 
  <artifactId>spring-boot-starter-parent</artifactId>
  <version>1.3.5.RELEASE</version>
  对应旧版本的 
  <artifactId>spring-cloud-dependencies</artifactId>
  <version>Brixton.RELEASE</version>
  新版本的	
  <artifactId>spring-boot-starter-parent</artifactId>
  <version>1.5.3.RELEASE</version>
  对应新版本的
  <spring-cloud.version>Dalston.SR1</spring-cloud.version>
  otherwise ， 报错。。。
  dependencyManagement里只是声明依赖，并不实现引入.
  
  
#优化:http://blog.csdn.net/lc0817/article/details/54375802
   