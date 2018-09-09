java基础
===


Spring相关
===
### 基本特点
+ 轻量：Spring 是轻量的，基本的版本大约2MB。
+ 控制反转：Spring通过控制反转实现了松散耦合，对象们给出它们的依赖，而不是创建或查找依赖的对象们。
+ 面向切面的编程(AOP)：Spring支持面向切面的编程，并且把应用业务逻辑和系统服务分开。
+ 容器：Spring 包含并管理应用中对象的生命周期和配置。
+ MVC框架：Spring的WEB框架是个精心设计的框架，是Web框架的一个很好的替代品。
+ 事务管理：Spring 提供一个持续的事务管理接口，可以扩展到上至本地事务下至全局事务（JTA）。
+ 异常处理：Spring 提供方便的API把具体技术相关的异常（比如由JDBC，Hibernate or JDO抛出的）转化为一致的unchecked 异常。

### 依赖倒置原则（Dependency Inversion Principle, DIP）
+ 高层模块不应当依赖低层模块，它们都应当依赖抽象。
+ 抽象不应该依赖具体实现。具体实现应该依赖抽象。

### 依赖注入模式（Dependency Injection）
在运行时将类的依赖注入到代码中。
，并将实现这个接口的实体类注入到主类的构造器中来实现这个模式。

### 控制反转容器（Inversion of Control Container，IoC）
控制反转模式的基本概念是，不去实际生成对象，而是去定义如何生成对象。
不用直接在代码中将模块和服务硬编码在一起，而是在配置文件中描述哪个模块需要哪个服务。


### spring bean生命周期

+ 实例化一个Bean－－也就是我们常说的new；
+ 按照Spring上下文对实例化的Bean进行配置－－也就是IOC注入；
+ 如果这个Bean已经实现了BeanNameAware接口，会调用它实现的setBeanName(String)方法，此处传递的就是Spring配置文件中Bean的id值
+ 如果这个Bean已经实现了BeanFactoryAware接口，会调用它实现的setBeanFactory(setBeanFactory(BeanFactory)传递的是Spring工厂自身（可以用这个方式来获取其它Bean，只需在Spring配置文件中配置一个普通的Bean就可以）；
+ 如果这个Bean已经实现了ApplicationContextAware接口，会调用setApplicationContext(ApplicationContext)方法，传入Spring上下文（同样这个方式也可以实现步骤4的内容，但比4更好，因为ApplicationContext是BeanFactory的子接口，有更多的实现方法）；
+ 如果这个Bean关联了BeanPostProcessor接口，将会调用postProcessBeforeInitialization(Object obj, String s)方法，BeanPostProcessor经常被用作是Bean内容的更改，并且由于这个是在Bean初始化结束时调用那个的方法，也可以被应用于内存或缓存技术；
+ 如果Bean在Spring配置文件中配置了init-method属性会自动调用其配置的初始化方法。
+ 如果这个Bean关联了BeanPostProcessor接口，将会调用postProcessAfterInitialization(Object obj, String s)方法、；
  注：以上工作完成以后就可以应用这个Bean了，那这个Bean是一个Singleton的，所以一般情况下我们调用同一个id的Bean会是在内容地址相同的实例，当然在Spring配置文件中也可以配置非Singleton，这里我们不做赘述。
+ 当Bean不再需要时，会经过清理阶段，如果Bean实现了DisposableBean这个接口，会调用那个其实现的destroy()方法；
+ 最后，如果这个Bean的Spring配置中配置了destroy-method属性，会自动调用其配置的销毁方法。

以上10步骤可以作为面试或者笔试的模板，另外我们这里描述的是应用Spring上下文Bean的生命周期，如果应用Spring的工厂也就是BeanFactory的话去掉第5步就Ok了。


springMVC
===
+ 前端控制器（DisatcherServlet）:接收请求，响应结果，返回可以是json,String等数据类型，也可以是页面（Model）。
+ 处理器映射器（HandlerMapping）:根据URL去查找处理器，一般通过xml配置或者注解进行查找。
+ 处理器（Handler）：就是我们常说的controller控制器啦，由程序员编写。
+ 处理器适配器（HandlerAdapter）:可以将处理器包装成适配器，这样就可以支持多种类型的处理器。
+ 视图解析器（ViewResovler）:进行视图解析，返回view对象（常见的有JSP,FreeMark等）。

![Image text](https://github.com/IceDarron/Ice/blob/master/Image/springMVC.png)

mybatis相关
===
### #{}和${}的区别是什么？

Mybatis在处理#{}时，会将sql中的#{}替换为?号，调用PreparedStatement的set方法来赋值；
Mybatis在处理${}时，就是把${}替换成变量的值。
使用#{}可以有效的防止SQL注入，提高系统安全性。#{}是预编译处理，${}是字符串替换。

### 关联查询
多个resultmap。
实例对象组合对象。


RESTfull
===
https://blog.csdn.net/shog808/article/details/79932968