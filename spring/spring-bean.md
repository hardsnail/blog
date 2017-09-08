####Bean scopes
1. singleton
<br>
IOC容器内存在一个实例，Spring Bean scope的默认值
2. prototype
<br>
prototype scope的Bean被另一个Bean引用时，会生成一个新的对象
3. request
<br>
同一个HTTP请求是一个实例
4. session
<br>
同一个session内是一个实例
5. global session
<br>
针对基于portlet的web应用，如果在web应用中，作用域和session一样
6. application
<br>
应用级别的实例

####Lifecycle callbacks
1. InitializingBean
<br>
Bean如果实现了InitializingBean接口，bean初始化之后，会调用afterPropertiesSet，效果等同于@PostConstruct
2. DisposableBean
Bean如果实现了DisposableBean接口，bean被销毁之前，会调用destroy方法，效果等同于@PreDestroy

####Spring Aware
1. ApplicationContextAware
<br>
当Spring的ApplicationContext对象生成好之后，会将ApplicationContext对象的引用通知到实现了ApplicationContextAware接口的Bean
2. BeanNameAware
<br>
当Spring Bean的一般属性初始化好之后，会调用实现了BeanNameAware接口的Bean实例的setBeanName方法，并把Bean name作为参数，这个动作会在初始化回调（InitializingBean的afterPropertiesSet）之前完成

####容器扩展点
1. BeanPostProcessor
<br>
获取到每个Bean初始化之前和初始化之后的Hook，例如：

	public class InstantiationTracingBeanPostProcessor implements BeanPostProcessor{
	
		@Override
		public Object postProcessBeforeInitialization(Object bean, String beanName) throws BeansException {
			System.out.println("postProcessBeforeInitialization, beanName="+beanName);
			return bean;
		}
	
		@Override
		public Object postProcessAfterInitialization(Object bean, String beanName) throws BeansException {
			System.out.println("postProcessBeforeInitialization, beanName="+beanName);
			return bean;
		}
	
	}
