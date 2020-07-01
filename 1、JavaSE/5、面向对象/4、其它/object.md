  java.lang.Object类
  1.Object类是所有Java类的根父类
  2.如果在类的声明中未使用extends关键字指明其父类，则默认父类为java.lang.Object类 
  3.Object类中的功能(属性、方法)就具有通用性。
  	属性：无
   方法：equals() / toString() / getClass() /hashCode() / clone() / finalize()
      wait() 、 notify()、notifyAll()

  4. Object类只声明了一个空参的构造器

  

  Object类中toString()的使用：

  1. 当我们输出一个对象的引用时，实际上就是调用当前对象的toString()
  
  2. Object类中toString()的定义：

    public String toString() {
        return getClass().getName() + "@" + Integer.toHexString(hashCode());
     }

  3. 像String、Date、File、包装类等都重写了Object类中的toString()方法。
     使得在调用对象的toString()时，返回"实体内容"信息
     
  4. 自定义类也可以重写toString()方法，当调用此方法时，返回对象的"实体内容"





  面试题：
  final、finally、finalize的区别？