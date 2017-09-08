####HandlerMapping将Request转换成Handler对象
* RequestMappingHandlerMapping 
<br>
根据请求URL和请求方式获取到对应的HandlerMethod
* BeanNameUrlHandlerMapping
* SimpleUrlHandlerMapping
* ControllerBeanNameHandlerMapping[已删除]
* ControllerClassNameHandlerMapping[已删除]
* DefaultAnnotationHandlerMapping[已删除]

####Handler处理并返回ModelAndView
* HandlerMethod
* HttpRequestHandler
* Controller
* Servlet

####HandlerAdapter根据Handler的类型进行适配，
* AnnotationMethodHandlerAdapter[已删除]
* HttpRequestHandlerAdapter
* SimpleControllerHandlerAdapter
* SimpleServletHandlerAdapter

####ModelAndView

####ViewResolver
* BeanNameViewResolver
* ContentNegotiatingViewResolver
* ViewResolverComposite

####注解
* `<context:component-scan base-package="com.demo.*"\>` 
<br>
扫描package，将带有注解的Class自动注册成Spring Bean，注解包括@Component, @Repository, @Service, @Controller等
* `<mvc:annotation-driven\>` 
<br>
自动注册DefaultAnnotationHandlerMapping与AnnotationMethodHandlerAdapter 两个bean，RequestBody和ResonseBody注解的参数和返回值支持JSON

####HandlerMethod处理过程
* HandlerMethod对象包含Controller Bean，以及handler的Method对象
* 根据Controller解析出handler的参数
* 通过反射，调用handler的method,传入参数
* 将controller的返回值通过转换成ModelAndView