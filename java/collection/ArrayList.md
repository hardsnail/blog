
#### ArrayList的存储结构
ArrayList的存储结构是数组，数组随着元素增长自动扩容，通过Arrays.copyOf方法将元素复制到新的数组
，当数组元素将要超过容量时，容量将增大50%。
#### ArrayList的特性
* 有序的，由于数组是有序的
* 随机访问效率高，通过下标获取数组的元素，效率比较高，插入和删除效率比较低（这个前提是插入的元素比较多）
* 不支持并发，比如两个线程同时调用add方法，两个线程有可能获取到的size是一样的，造成一个线程把另一个线程的数据覆盖
* 元素可以为null，数组的元素可以为null
* 元素可以重复，素组的元素可以重复
<p>

##ArrayList的源码解读

####内部属性elementData数组
elementData是用来存储ArrayList的元素的，elementData的大小就是ArrayList当前状态的容量，elementData数组包含ArrayList的数据，下标大于或等于ArrayList的size那部分是空的，是用来放置ArrayList的新元素的
####内部属性size
ArrayList的大小，一个主要的作用就是ArrayList的get方法获取元素时，控制ArrayList获取到真实数据
