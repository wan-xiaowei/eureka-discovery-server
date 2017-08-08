
详解: http://blog.csdn.net/beyannanfei/article/details/52069725



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

