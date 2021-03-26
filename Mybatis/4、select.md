select返回List：

resultType = List中元素的类型。



select返回Map：

* key：字段名；value：字段值。

  resultType = map

* key：JavaBean一属性；value：JavaBean。

  resultType = JavaBean，接口中的方法添加注解@MapKey，value指定JavaBean一属性作为key



resultMap：自定义返回类型，和resultType只能存在一个。

association：