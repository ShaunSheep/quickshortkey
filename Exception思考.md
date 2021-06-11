你真正的清楚Exception吗？——从Checked Exception引发的思考

今天读《Java8语言文档》（下文以文档简述）的时候，看到下面一段话：

> The checked exception classes are all exception classes other than the unchecked exception classes. That is, the checked exception classes are Throwable and all its subclasses other than RuntimeException and its subclasses and Error and its subclasses.
>
> ​					——11.1EXCEPTIONS-The Kinds and Causes of Exceptions

这段话说的是什么呢？Java Exception API体系中的**对象**按照是否Check，可以划分为Checked Exception和UnChecked Exception；

回答什么是CheckException之前，需要解释什么是UnChecked Exception——文档中Unchecked Exception的定义是：Run-Time Exception类型的对象和Error类型的对象。试想有这么一个大的集合Exception

