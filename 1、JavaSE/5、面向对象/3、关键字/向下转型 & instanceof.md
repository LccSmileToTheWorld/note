有了对象的多态性以后，内存中实际上是加载了子类特有的属性和方法的，但是由于变量声明为父类类型，导致
编译时，只能调用父类中声明的属性和方法。子类特有的属性和方法不能调用。

如何才能调用子类特有的属性和方法？
向下转型：使用强制类型转换符。
使用强转时，可能出现ClassCastException的异常
使用强转时，可能出现ClassCastException的异常。

instanceof关键字的使用

ainstanceofA:判断对象a是否是类A的实例。如果是，返回true；如果不是，返回false。

使用情境：为了避免在向下转型时出现ClassCastException的异常，我们在向下转型之前，先
进行instanceof的判断，一旦返回true，就进行向下转型。如果返回false，不进行向下转型。
类B是类A的父类。
如果a instanceof A返回true,则a instanceof B也返回true.
		