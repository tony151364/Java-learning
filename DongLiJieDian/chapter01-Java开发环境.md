## 零、Java是跨平台语言
```
编译完成后可以在多个系统上运行，如Window编译的文件可以在Linux、macOS运行，即：一次编译，到处运行。
```

## 一、常用DOS命令
	1.清屏：cls
	2.查看当前文件夹：dir
	3.删除文件：del *.txt
	4.查看两台计算机是否可以正常通讯：ping
	5.d：回车 切换盘符
	6.cd 切换目录
	7.mkdir 创建目录
	
    
## 二、vi（Visual interface）编辑器
	1.光标在行尾时选中一行：shift + home 
	光标在行首时选中一行:shift + end 
	
	2.回到文件首：ctrl + home
	回到文件尾：ctrl + end
	
	3.不用鼠标选中单词：ctrl + shift + 右箭头/左箭头
	查找： ctrl + f
	
    
## 三、JDK 、JRE、 JVM关系
	JDK：Java开发工具箱
	JRE（java Runtime Environment）：Java运行环境
	JVM：java虚拟机
  
  
 ## 五、类体、方法体
 ```java
 
 public class Test {  // 定义一个类命名为Test
	//类体
	
	/* main方法，也称为主方法（程序的入口，SUN公司java语言的规定）
	 JVM在执行程序时，会主动去找这样一个方法。没有这个规格的方法，程序无法运行。
	 方法必须放到类体中，不能放到类体外边*/
	public static void main(String[] args) {
		// 方法体
		System.out.println("Test1");
	}
}

```
	
    

## 六、public

```java

public class Test4 {
	/*  
	1.public 类不是必须的，如果有的话public修饰的类名必须与源文件一致
	2.public 有且只能有一个，这表示，每个编译单元都有单一的公共入口， 
		用public类来表现。该接口可以按要求包含众多的支持包访问权限的类
	3.每个类都会生成一个.class文件 */
	public static void main(String[] args) {
		System.out.println("T1....");
		T2.main(args);
}

class T2 {
	public static void main(String[] args) {
		System.out.println("T2....");
	}
}

class T3 {
	public static void main(String[] args) {
		System.out.println("T3....");
	}
}

```
