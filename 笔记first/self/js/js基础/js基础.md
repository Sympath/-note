#### 基本包装类型

为了便于操作基本类型值，ECMAScript还提供了3个特殊的引用类型：Boolean、Number和String。每当读取一个基本类型值得时候，后台就会创建一个对应的基本包装类型的对象，从而让我们能够调用一些方法来操作这些数据。

```
var s1="some text";
var s2=s1.substring(2); 
```

这个例子中的变量s1包含一个字符串，字符串当然是基本类型值，而下一行代码调用了s1的substring()方法，并将返回的结果保存在了s2中。我们知道，基本类型值不是对象，因而从逻辑上讲它们不应该有方法（尽管如我们所愿，它们确实有方法）。其实，为了让我们实现这种直观的操作，后台已经自动完成了一系列的处理。当第二行代码访问s1时，访问过程处于一种读取模式，也就是呀从内存中读取这个字符串的值。而在读取模式中访问字符串时，后台都会自动完成下列处理。
1.创建String类型的一个实例；
2.在实例上调用指定的方法；
3.销毁这个实例。







- 删除json中某一项  delete json.a