# framework-interview
# contents
## spring核心面试题
## 什么是Spring框架？它是什么主要模块？
Spring Framework是一个Java平台，为开发Java应用程序提供全面的基础架构支持。Spring处理基础结构部分，
以便您可以专注于应用程序部分。在内部，Spring Framework将形式化设计模式编码为一流的对象，您可以将它们集成到自己的应用程序中，
而不必担心它们在后端如何工作。

目前，Spring Framework由大约20个模块组成的特征组成。这些模块分为核心容器，
数据访问/集成，Web，AOP（面向方面​​编程），Instrumentation，Messaging和Test，如下图所示。
<div align="center"><img src="https://howtodoinjava.com/wp-content/uploads/2015/02/spring-modules.png"/></div>

## 使用Spring Framework有什么好处？
以下是使用Spring框架的很多好处的列表 
- 通过依赖注入（DI）方法，依赖关系在构造函数或JavaBean属性中是明确的和明显的。
- 例如，IoC容器通常是轻量级的，尤其是与EJB容器相比时。这对于在内存和CPU资源有限的计算机上开发和部署应用程序很有帮助。
- Spring并没有重新发明轮子，而是真正使用了一些现有技术，如几个ORM框架，日志框架，JEE，Quartz和JDK计时器以及其他视图技术。
- Spring以模块化方式组织。即使包和类的数量很大，你只需要担心你需要的，而忽略其余的。
- 测试用Spring编写的应用程序很简单，因为依赖于环境的代码被移入此框架。此外，通过使用JavaBean风格的POJO，使用依赖注入来注入测试数据变得更加容易。
- Spring的Web框架是一个设计良好的Web MVC框架，它为Web框架提供了一个很好的选择，例如Struts或其他过度设计或不太流行的Web框架。
- Spring提供了一个一致的事务管理接口，可以缩减为本地事务（例如使用单个数据库）并扩展到全局事务（例如使用JTA）。

## 什么是控制反转（IoC）和依赖注入？
在软件工程中，控制反转（IoC）是一种编程技术，其中对象耦合在运行时由汇编对象绑定，并且在编译时通常不知道使用静态分析。
在传统编程中，业务逻辑的流程由静态分配给彼此的对象决定。通过控制反转，流程取决于由汇编程序实例化的对象图形，
并且通过抽象定义对象相互作用使其成为可能。绑定过程是通过“依赖注入”来实现的。

控制反转是一种设计范例，旨在更多地控制应用程序的目标组件，即实际正在执行的工作。

依赖注入是一种用于创建其他对象所依赖的对象实例的模式，而无需知道在编译时将使用哪个类来提供该功能。控制反转依赖于依赖注入，
因为需要一种机制来激活提供特定功能的组件。否则，如果框架不再受控，那么框架如何知道要创建哪些组件？

在Java中，依赖注入可能通过3种方式发生：

- 构造函数注入
- 安装员注射
- 一个接口注入

## 在Spring框架中解释IoC？
在org.springframework.beans和org.springframework.context软件包提供了对Spring框架的IoC容器的基础。
该BeanFactory界面提供了一种高级配置机制，可以管理任何性质的对象。该ApplicationContext接口建立在BeanFactory（它是一个子接口）之上，
并添加了其他功能，例如与Spring的AOP特性的集成，消息资源处理（用于国际化），事件传播以及应用层特定上下文WebApplicationContext用于Web应用程序。

这org.springframework.beans.factory.BeanFactory是Spring IoC容器的实际表示，负责包含和管理上述bean。BeanFactory接口是Spring中的中央IoC容器接口。


## BeanFactory和ApplicationContext之间的区别？
A BeanFactory就像一个包含bean集合的工厂类。在BeanFactory 拥有自身内部多个bean的bean定义，然后实例化豆每当客户端请求。
BeanFactory能够在实例化协作对象时创建关联。这消除了bean本身和bean客户端的配置负担。BeanFactory也参与bean的生命周期，调用自定义初始化和销毁​​方法。

表面上，应用程序上下文与bean工厂相同。两者都加载bean定义，将wire beans加载在一起，并根据请求分配bean。但它也提供了：

- 解决短信的手段，包括支持国际化。
- 加载文件资源的通用方法。
- 事件被注册为侦听器的bean。
- 三个常用的实现ApplicationContext是：

ClassPathXmlApplicationContext：它从位于类路径中的XML文件加载上下文定义，将上下文定义视为类路径资源。
应用程序上下文是通过使用代码从应用程序的类路径加载的。
`ApplicationContext context = new ClassPathXmlApplicationContext(“bean.xml”);`
FileSystemXmlApplicationContext：它从文件系统中的XML文件加载上下文定义。应用程序上下文是通过使用代码从文件系统加载的。
`ApplicationContext context = new FileSystemXmlApplicationContext(“bean.xml”);`
XmlWebApplicationContext ：它从Web应用程序中包含的XML文件加载上下文定义。

## 在多少种方式中，您可以将Spring配置到我们的应用程序中？
您可以通过3种方式将spring配置到您的应用程序中：

- 基于XML的配置
- 基于注释的配置
- 基于Java的配置

## 什么是基于Spring XML的配置？
在Spring框架中，bean所需的依赖项和服务在配置文件中指定，配置文件通常采用XML格式。这些配置文件通常以<beans>标签开头，
并包含大量的bean定义和应用程序特定的配置选项。

Spring XML Configuration的主要目标是通过使用xml文件来配置所有Spring组件。
这意味着将不会出现任何其他类型的Spring配置（如通过Java类的注释或配置）。

Spring XML Configuration使用Spring命名空间来提供配置中使用的XML标记集合; 主要的Spring命名空间是：上下文，bean，jdbc，tx，aop，mvc，aso。
```xml
<beans>

	<!-- JSON Support -->
	<bean name="viewResolver" class="org.springframework.web.servlet.view.BeanNameViewResolver"/>
	<bean name="jsonTemplate" class="org.springframework.web.servlet.view.json.MappingJackson2JsonView"/>
	
	<bean id="restTemplate" class="org.springframework.web.client.RestTemplate"/>

</beans>
```
最简单的web.xml文件可以使您的应用程序加载配置文件并为您配置运行时组件，这些文件位于仅配置DispatcherServlet的位置。
```xml
<web-app>
  <display-name>Archetype Created Web Application</display-name>
  
  <servlet>
		<servlet-name>spring</servlet-name>
			<servlet-class>
				org.springframework.web.servlet.DispatcherServlet
			</servlet-class>
		<load-on-startup>1</load-on-startup>
	</servlet>

	<servlet-mapping>
		<servlet-name>spring</servlet-name>
		<url-pattern>/</url-pattern>
	</servlet-mapping>
	
</web-app>
```
## springMVC相关面试题
## 什么是Spring MVC框架？
Spring web MVC框架提供了模型 - 视图 - 控制器体系结构和可用于开发灵活和松散耦合的Web应用程序的组件。MVC模式导致分离应用程序的不同方面
（输入逻辑，业务逻辑和UI逻辑），同时在应用程序的模型，视图和控制器部分之间提供松散耦合。与其他MVC框架相比，Spring框架提供了许多优势
- 清除角色分离 - 控制器，验证器，命令对象，表单对象，模型对象，DispatcherServlet，处理程序映射，视图解析器等。每个角色都可以由专门的对象来完成。
- 作为JavaBeans的框架和应用程序类的强大而直接的配置。
- 可重用的业务代码 - 无需重复。您可以将现有业务对象用作命令或表单对象，而不是镜像它们以扩展特定的框架基类。
- 可定制的绑定和验证
- 可定制的处理程序映射和视图解析
- 可自定义的区域设置和主题解析
- Spring 2.0中引入了一个JSP表单标记库，它使JSP页面中的表单变得更加容易。等等

## 什么是DispatcherServlet和ContextLoaderListener？
与许多其他Web MVC框架一样，Spring的Web MVC框架也是由请求驱动的，围绕一个处理所有HTTP请求和响应的中央Servlet进行设计。
然而，Spring的DispatcherServlet不仅仅是这一点。它与Spring IoC容器完全集成，因此它允许您使用Spring提供的每个功能。

在接收到HTTP请求后，DispatcherServlet会查询HandlerMapping（配置文件）
以调用相应的Controller。Controller接受请求并调用相应的服务方法并设置模型数据，
然后将视图名称返回给DispatcherServlet。DispatcherServlet将从ViewResolver获取帮助以获取请求的已定义视图。
View完成后，DispatcherServlet将模型数据传递给最终在浏览器中呈现的视图。
```xml
<web-app>
  <display-name>Archetype Created Web Application</display-name>
  
  <servlet>
		<servlet-name>spring</servlet-name>
			<servlet-class>
				org.springframework.web.servlet.DispatcherServlet
			</servlet-class>
		<load-on-startup>1</load-on-startup>
	</servlet>

	<servlet-mapping>
		<servlet-name>spring</servlet-name>
		<url-pattern>/</url-pattern>
	</servlet-mapping>
	
</web-app>
```
默认情况下，DispatcherServlet使用加载它的配置文件<servlet_name>-servlet.xml。例如，
使用上面的web.xml文件，DispatcherServlet将尝试在classpath中查找spring-servlet.xml文件。

ContextLoaderListener读取spring配置文件（对web.xml 中的“ contextConfigLocation ” 给出的值），解析它并加载在该配置文件中定义的bean。例如
```xml
<servlet>
	<servlet-name>spring</servlet-name>
	<servlet-class>
		org.springframework.web.servlet.DispatcherServlet
	</servlet-class>
	
	<init-param>
		<param-name>contextConfigLocation</param-name>
		<param-value>/WEB-INF/applicationContext.xml</param-value>
	</init-param>
	
	<load-on-startup>1</load-on-startup>
</servlet>
```
## 什么是Spring MVC的前端控制器类？
前端控制器定义为“处理所有Web应用程序请求的控制器” 。DispatcherServlet
（实际上是一个servlet）是Spring MVC中的前端控制器，它截获每个请求，然后将请求分发/转发给适当的控制器。

当一个Web请求发送到Spring MVC应用程序时，调度程序servlet首先收到请求。然后，
它组织在Spring的Web应用程序上下文中配置的不同组件（例如实际的请求处理程序控制器和视图解析程序）或控制器本身中存在的注释，这些都是处理请求所需的。

## @Component，@Controller，@Repository和@Service注释之间的区别？
- @Component注释将java类标记为bean，因此spring的组件扫描机制可以将其选中并将其引入应用程序上下文中。要使用此注释，请将其应用于类
- @Repository注释是@Component具有类似用途和功能的注释专业化。除了将DAO导入DI容器之外，它还会使未经检查的异常（从DAO方法抛出）有资格转换为Spring DataAccessException。
- @Service注释也是组件注释的专业化。它目前不提供任何超过@Component注释的额外行为，但@Component在服务层类中使用@Service是一个好主意，因为它更好地指定了意图。
- @Controller注解将一个类标记为Spring Web MVC控制器。它也是一种@Component专业化，所以标记的bean会自动导入到DI容器中。将@Controller注释添加到类时，可以使用另一个注释，即@RequestMapping; 将URL映射到类的实例方法。

## ViewResolver类是什么？
ViewResolver是一个接口，可以通过可以按名称解析视图的对象来实现。有很多方法可以用来解析视图名称。这些接口的各种内置实现都支持这些方法。最常用的实现是InternalResourceViewResolver类。它定义了前缀和后缀属性来解析视图组件。
```xml
<bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
	<property name="prefix" value="/WEB-INF/views/" />
	<property name="suffix" value=".jsp" />
</bean>
```
因此，使用上面的视图解析器配置，如果控制器方法返回“ login ”字符串，那么“ /WEB-INF/views/login.jsp”文件将被搜索和渲染。

## 什么是MultipartResolver以及何时使用？
Spring自带MultipartResolver处理Web应用程序中的文件上传。Spring中包含两个具体实现：
- CommonsMultipartResolver for Jakarta Commons FileUpload
- 用于Servlet 3.0 Part API的StandardServletMultipartResolver
要定义一个实现，请在DispatcherServlet的应用程序上下文中创建一个ID为“ multipartResolver ” 的bean 。这样的解析器会应用于该DispatcherServlet处理的所有请求。

如果DispatcherServlet检测到多部分请求，它将通过配置解析它MultipartResolver并传递一个HttpServletRequest包装。然后控制器可以将他们的请求转发给MultipartHttpServletRequest接口，从而允许访问任何接口MultipartFiles。

##

##

##

























