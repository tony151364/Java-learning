## 一、标识符(Identifier)

### 1.标识符可以标识 
(1) 类名  
(2) 方法名  
(3) 接口名  
…… 凡是程序员可以自己命名的单词都是标识符

### 2.标识符命名规则
(1) 标识符由字母、数字、下划线“\_”、美元符号“$”或者人民币符号“￥”组成  
(2) 标识符首字母不能是数字，标识符中不能有空格  
(3) 关键字不能做标识符，如：public、static、void

### 3.标识符命名规范
(1) 命名时要有意义，见名知意  
(2) 遵循驼峰命名法  
(3) 类名、接口名首字母大写，后面每个单词首字母大写  
(4) 变量名首字母小写，后面每个单词首字母大写：childrenAge  
(5) 所有常量名大写，并单词和单词之间采用下划线衔接：USER_AGE  

```java

public class Identifier {
    
    public static void main(String[] args) {
        doSome();
    }
    
    public static void doSome() {
        int childrenAge = 20;
        int USER_AGE = 20;
        
        System.out.println(childrenAge);
        System.out.println(USER_AGE);
    }
}
```
