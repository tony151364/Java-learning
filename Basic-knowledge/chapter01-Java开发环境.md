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
  
  
 ## 四、类体、方法体
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
	
    
## 五、args

```java

public class Test2 {

    // args 可以改为其他名字，对于主方法来说只能修改这个位置    
    public static void main(String[] args) {
        System.out.println("Test2");
        
        String[] strString = new String[] {"and", "apple", "ban"};
        main2(strString);
    }
    
    public static void main2(String[] args) {
        System.out.println("Test3");
        
        for(String i : args) {
            System.out.println(i);  // output every elements of array String
        }
    }
}

```


## 六、public
