####HandlerMapping将Request转换成Handler对象
* RequestMappingHandlerMapping
 处理@Controller
* BeanNameUrlHandlerMapping
* SimpleUrlHandlerMapping 处理静态资源

* ControllerBeanNameHandlerMapping[已删除]
* ControllerClassNameHandlerMapping[已删除]
* DefaultAnnotationHandlerMapping[已删除]

####Handler处理并返回ModelAndView
* HandlerMethod
* HttpRequestHandler
* Controller
* Servlet

####HandlerAdapter根据Handler的类型进行适配
* AnnotationMethodHandlerAdapter[已删除]
* HttpRequestHandlerAdapter
* SimpleControllerHandlerAdapter
* SimpleServletHandlerAdapter

####ModelAndView

#### ViewResolver
* BeanNameViewResolver
* ContentNegotiatingViewResolver
* ViewResolverComposite