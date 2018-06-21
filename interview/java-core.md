## 基础
### 静态变量和实例变量的区别？ 
在语法定义上的区别：静态变量前要加static关键字，而实例变量前则不加。  
在程序运行时的区别：实例变量属于某个对象的属性，必须创建了实例对象，其中的实例变量才会被分配空间，
才能使用这个实例变量。静态变量不属于某个实例对象，而是属于类，所以也称为类变量，只要程序加载了类的字节码，
不用创建任何实例对象，静态变量就会被分配空间，静态变量就可以被使用了。总之，实例变量必须创建对象后才可以通过这个对象来使用，
静态变量则可以直接使用类名来引用。
例如，对于下面的程序，无论创建多少个实例对象，永远都只分配了一个staticVar变量，并且每创建一个实例对象，
这个staticVar就会加1；但是，每创建一个实例对象，就会分配一个instanceVar，即可能分配多个instanceVar，并且每个instanceVar的值都只自加了1次。
```java
public class VariantTest{
		public static int staticVar = 0; 
		public int instanceVar = 0; 
		public VariantTest(){
			staticVar++;
			instanceVar++;
			System.out.println(“staticVar=” + staticVar + ”,instanceVar=” + instanceVar);
		}
}
```
备注：这个解答除了说清楚两者的区别外，最后还用一个具体的应用例子来说明两者的差异，体现了自己有很好的解说问题和设计案例的能力，思维敏捷，超过一般程序员，有写作能力！
### 请说出作用域public，private，protected，以及不写时的区别
这四个作用域的可见范围如下表所示。  
说明：如果在修饰的元素上面没有写任何访问修饰符，则表示friendly。

作用域 |   当前类 | 同一package| 子孙类 |其他package 
:--:|:--:|:--:|:--:
public |   √    | √|          √    |   √ 
protected | √  |   √|          √  |    × 
friendly  | √ |    √ |         × |     × 
private    |√|     ×  |        ×|      × 

备注：只要记住了有4种访问权限，4个访问范围，然后将全选和范围在水平和垂直方向上分别按排从小到大或从大到小的顺序排列，就很容易画出上面的图了。




