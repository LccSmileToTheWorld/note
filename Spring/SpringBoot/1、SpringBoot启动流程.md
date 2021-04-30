1. new SpringApplication()；
   1. 判断web服务类型 WebApplicationType。
   2. 初始化应用上下文。获取所有依赖 jar 包的 META-INF/spring.factories 文件，读取org.springframework.context.ApplicationContextInitializer 属性对应的全类名，通过 java 反射创建对象。
   3. 初始化监听器。获取所有依赖 jar 包的 META-INF/spring.factories 文件，读取 org.springframework.context.ApplicationListener 属性对应的全类名，通过 java 反射创建对象。
2. 调用 run();
   1. 启动秒表 StopWatch
   2. 配置 java.awt.headless
   3. 启动监听器。
   4. 准备环境，创建应用上下文 ApplicationContext
   5. 初始化异常报告器。读取所有依赖 jar 包 的 META-INF/spring.factories 文件，读取org.springframework.boot.SpringBootExceptionReporter 属性对应的全类名，通过 java 反射创建对象。

