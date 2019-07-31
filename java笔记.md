[TOC]
### 01.windows基础知识
#### 原码反码补码
* 最高位为符号位，“0”表示正，“1”表示负
* 正数:原码反码补码是一样
* 负数： 负数的反码是符号位除外,其余原码逐位取反,负数的补码是在其反码的末位加1

#### 数据大小B,KB,MB,GB
* 1Byte = 8bit
* 1KB = 1024B, 1MB = 1024KB, 1GB = 1024MB, 1TB = 1024GB

#### 人机交互
* 命令行交互
* 图形化界面 - 起源施乐公司 发迹苹果  火于微软

#### windows快捷键
|		|		|
| ---- | ---- |
|win+L  |切换用户|
|win+D  |返回桌面|
|win+E  |文件资源管理器|
|win+R  |运行命令|

#### Dos 命令
|	|	|	|
| ---- | ---- | ---- |
|cd 	|改变当前目录。切换盘符| c:   e|
|dir 	|列文件名 相当于ls	| dir  路径|
|md 		|创建目录 			| md a\b\c|
|rd 		|删除文件夹   		| rd /S（递归删除，默认只能删除空文件） /Q（不询问） 文件名|
|del 	|删除文件或者文件夹 	| del  /S /Q|
|ren	 	|重命名			| ren 原文件名  修改后文件名|
|ping	| ||
|ipconfig|| |
|cls  	|清屏||
|exit  	|退出命令行||
|echo 	|打印	,重定向：覆盖	| echo 'fdsafd' > a.txt  |
|echo 	|重定向：在文件后追加 	| echo 'dfsafa' >> a.txt  |
|notepad |用记事本创建文件		| notepad a.txt |
|move 	|移动文件 ||
|copy 	|拷贝文件 			| copy 源 位置  目标位置  |
|xcopy 	|复制文件夹 		| xcopy /E 源 目标   /E递归|
|type 	|查看文件内容		| type a.txt|
|find 	|查找				| find "xxx"|
|path  	|路径||
|date 	|日期||
|time  	|时间||
|mspaint |画图工具||

### 02.JAVA基础知识
* Java之父- James Gosling  
* Java发展- sun公司，oak -> java 
* Java版本- javase5.0 tiger -> javase 6.0 mustang -> javase7.0 dolphin
* Java语言平台版本
    - J2SE- 是为开发普通桌面和商务应用程序提供的解决方案,该技术体系是其他两者的基础，可以完成一些桌面应用程序的开发
    - J2EE- 是为开发企业环境下的应用程序提供的一套解决方案,该技术体系中包含的技术如 Servlet、Jsp等，主要针对于Web应用程序开发
    - J2ME- 是为开发电子消费产品和嵌入式设备提供的解决方案
* `java语言特点`: 简单性，面向对象，分布式，健壮性，安全性，可移植性，解释型，高性能，多线程，动态性，开源，跨平台(write once, run anywhere,每个系统装专有的jvm)
* `Java虚拟机(JVM)`: 实现Java程序跨平台,但虚拟机不能跨平台
* `JRE和JDK区别`
    - JRE（运行java程序只需要JRE）：JVM+核心类库
    - JDK（java开发人员使用）：JRE+java开发工具（javac,jar..)
    - JDK用来开发，JRE用来运行
* `Java程序运行过程`:java源文件(.java)-->编译器(编译)-->字节码文件(.class)-->解释器(解释)

### 03.Java安装和Eclipse安装
#### Java安装
* 1.下载JDK，并安装
    - bin：该目录用于存放一些可执行程序。
    - db JDBC数据库
    - jre
    - lib lib是library的缩写，意为 Java 类库或库文件，是开发工具使用的归档包文件。
    - include 由于JDK是通过C和C++实现的，因此在启动时需要引入一些C语言的头文件，该目录就是用于存放这些头文件的
    - src src中放置的是JDK核心类的源代码，通过该文件可以查看Java基础类的源代码。jar xvf src.zip解压
* 2.配置环境变量：
    - JAVA_HOME: C:\Program Files\Java\jdk1.8.0_201
    - path: %Java_Home%\bin;%Java_Home%\jre\bin
    - classpath（1.5之后不用配置，默认当前文件）: .;%Java_Home%\bin;%Java_Home%\lib\dt.jar;%Java_Home%\lib\tools.jar
* 3.验证是否安装成功：
    - 运行cmd，  java ， javac ， java -version
* 4.HelloWorld程序注意事项：
    - 区别大小写，Hello 和 hello不一样
    - 编译器需要一个文件名（javac Welcome.java) , 而运行程序时,只需要指定类名（java Welcome ) ,不要带扩展名 
    - 注意拓展名windows默认.txt
    - 必须包含main函数，从main开始执行,且必须声明为public static void
    - 一个源程序中只能有一个类声明为公有的
    - 源代码的文件名必须与公共类的名字相同

#### Eclipse安装
* 1.下载Eclipse:https://www.eclipse.org/downloads/packages/, 一般选Eclipse IDE for Java Developers
* 2.选择工作目录，创建java项目：File->New->Java project->finish
* 3.新建java类：右键New->class->输入类名—>finish

### Java编码规范

#### `命名规范`

- 类名和接口：大驼峰命名（如：FirstExample） 
- 方法名：小驼峰命名 (如：toString)

* 常量名: 全大写,下划线 (如: PER_OF_MONTH)
* 变量名: 小驼峰 (如: isTrue)
* 包名: 全小写,.分割,公司或域名倒置(如:com.apple)

### 04.Java的基本程序结构

#### 标识符,关键字

`标识符要求`: 区分大小写; 字母数字_$; 不能是关键字; 变量名的长度基本上没有限制 

`关键字包括`: ....

#### 注释：
1. // 单行注释  
2. /* xxx */  多行注释,**不能嵌套** 
3. /** xxx */ 用来自动生成javadoc文档
	

#### 变量
* 变量名命名: 参照标识符, 小驼峰(如: superCarry)
* 声明: 数据类型 变量名;
* 初始化: 数据类型 变量名 = 初始值;
* `注意`:　**局部变量使用前必须先初始化**
* `变量分类`：类变量，局部变量，成员变量
* `局部变量和成员变量区别`: 

|      | 局部变量                  | 成员变量                |
| ---- | ------------------------- | ----------------------- |
|      | 无默认值,使用前必须初始化 | 未初始化,系统会赋默认值 |
|      |                           |                         |
|      |                           |                         |
|      |                           |                         |

#### 常量
* 字面值常量
    * 整型常量   	二进制,八进制,十六进制
    * 浮点数常量	
    * 字符常量		'x'
    * 字符串常量	"xx"
    * 布尔常量		true,false
    * null
    
* 自定义常量 

  final,只能初始化一次,(类似于c++的const)

  `格式`: final 数据类型 变量名 = 初始值; 

  `命名格式`: 常量命名应大写，多个单词用下划线_连接

  `常见于类变量`: 如： public static final double PI = 3.1415;  
### 05.基本数据类型 4类8种
#### 整型
* byte  1个字节 -128~127 Byte.MIN_VALUE, Byte.MAX_VALUE, Byte.SIZE 
* short 2个字节 -2^15~2^15-1   Short
  
* int   4个字节 -2^31~2^31-1   Integer
* long  8个字节 -2^63~2^163-1  Long



* **默认是int**，如果要long类型，**加后缀L**，如11111111111000L

* 不同于c++，**没有无符号（unsigned）类型**

* 进制
		|      |      |
   | ---- | ---- |
	|十进制  |	|
   |二进制 0b|0b1001,   （java7.0以上才有）|
   |八进制 0   |0144,  尽量别用，易混淆|
   |十六进制 0x | 0x14|

   ​    

#### 浮点型
* float	4字节     Float.MIN_VALUE
* double   8字节     Double.MIN_VALUE
* **默认是double**，**如果要float，加后缀F**，如: float f = 3.14F
* **浮点数不精确**，2.0-1.1 = 0.89999999999，可用BigDecimal
* IEEE 754: INF，NAN，规格化，非规格化
* 0.0/0.0 = NaN,  1/0.0 = INF
* x == Double.NaN   //永远都是false,应为NaN不等于任何数
* 要判断是不是NaN, 可以用Double.isNaN(x)

#### char类型
* char **2个字节**   Character.MIN_VALUE

* char c = 'a'; char c = '\u2122'

* **Unicode编码**，范围：\u0000~\uffff

* **尽量不要在程序中使用char类型,用字符串代替**

* **转义字符**: \n, \t, \b, \\", \\', \\\, \r

* 参与运算时将被转为 int类型, 如：System.out.println('a'+'b') 

  
#### 布尔类型 
* boolean  b = true / false
* **不能与int等数值类型进行数学计算或类型转换**
* `同C++区别`: c++中可以, 于是注意 if(x = 0) c++中可以，java不可以

#### 类型转换
* 强制类型转换 (int) ，(double)   在把容量大的类型转换为容量小的类型时必须使用强制类型转换。
* 自动类型转换 short, byte, char ->  int -> long -> float -> double 
* **不能对boolean类型进行类型转换**。

#### Math函数，见常用类-》Math类
### 06.字符串  String 
* 不可改变,  c++中的string是可修改的
* 但可实现字符串的共享，但是 + 或者 substring产生的不共享 
* 字符串池, String s1 = "hello";String s2="hello"; s1==s2 # true
* 空串： "" <==>  s.length() = 0 <==> s.equals("")
* null串: if (s != null && s.length() != 0)

#### 构建字符串 StringBuilder
* StringBuilder builder = new StringBuilder();
* append：builder.append();
* insert: builder.insert(int offset, char c);
* delete: builder.delete(int start, int end);
* replace: builder.replace(int start, int end, String str); 
* toString: String s = builder.toString();

#### 字符串运算
* length 长度

  * s.length()
* 拼接 + 
  * 可以是字符串和非字符串，非字符串会被转换为字符串
* 查找
  * indexof(int ch)
  * indexof(String str, int fromIndex)
  * lastIndexof...
* 子串

  * s.substring(begin[,end])
* join
  * String.join(delim, ....)
  * String.join("," ,"a", "b", "c") == "a,b,c"
* split
  * s.split(" ") -> String[] 
* equals 检测字符串是否相等,比较的是值
  * s.equals(t)
  	 忽略大小写： s.equalsIgnoreCase(t)	
  * 不要用==检测两个字符串是否相等，==比较的地址
  * c语言用strcmp比较， 
* 大小写
  * s.toLowerCase()
  * s.toUpperCase()
* 前后缀
  * startsWith(String str)
  * endsWith(String str)
* 去空格trim

  * s.trim()

### 07.运算符
#### 算术运算符

`包括`: +, -, *, /, %, ++, --

* +号在java中有三种作用,代表正号[少用],做加法运算,**字符串的连接**

- java中 整数除法 / **向 0 取整**, 如 -7/2 = -3，  py中是-4
- 注意 ++x,x++的区别
  - int x = 4; int y = (x++)+(++x)+(x*10);
  - 4 + 6 + 60 = 70
- 注意 **4++,错误的**，只能是变量

#### 关系运算符: 

`包括`: <, >, <=, >=, !=, ==

- **== 比较的是地址**，类用equals，数值型的可以用==，字符串用equals
- **运算结果是boolean类型** 
- "=="不能写成"="
- `" > "`、`" < "`、`" >= "`、`" <= "`只支持数值类型的比较，`" == "`、`" != "`支持所有数据类型的比较

#### 位运算符:  

`包括`: &，| , ^ ,  ~,  << ,>>, >>>（无符号右移）

- ^ 异或同一个数两次，值不变, a^b^b = a;  a^0 = a;  a^a = 0
- \>>>逻辑右移补0， >> 算术右移补符号位

#### 逻辑运算符:

`包括`: &&, ||, !

- 注意 && 和 || 的**短路原理**

#### 三元运算符

`包括`: condition ? expr1 : expr2;

#### 枚举类型: 

`包括`: enum,

- enum Size {SMALL, MEDIUM, LARGE}
- Size s = Size.SMALL
- 不能做局部变量

#### 赋值运算符: 

`包括`: =, +=, -=, /=

* 右边赋值给左边


* 扩展运算符会**自动进行强制类型转换**
  - int x=0;  x += 3.5 <==> (int)(x+3.5)

#### 结合性和优先级

* 从右到左的有：一元运算，三元运算符，赋值运算
* 单目 > 算术 > 位移 > 关系 > 位运算 > 逻辑 > 三目 > 赋值。

| 优先级 | 运算符                                                       | 结合性   |
| ------ | ------------------------------------------------------------ | -------- |
| 1      | ( )　[ ] 　.                                                 | 从左到右 |
| 2      | ! 　~　 ++　 --    (强制类型转换)    new                     | 从右到左 |
| 3      | *　 /　 %                                                    | 从左到右 |
| 4      | +　 -                                                        | 从左到右 |
| 5      | << 　>>　 >>>                                                | 从左到右 |
| 6      | < 　<=　 > 　>=　 instanceof                                 | 从左到右 |
| 7      | == 　!=                                                      | 从左到右 |
| 8      | &                                                            | 从左到右 |
| 9      | ^                                                            | 从左到右 |
| 10     | \|                                                           | 从左到右 |
| 11     | &&                                                           | 从左到右 |
| 12     | \|\|                                                         | 从左到右 |
| 13     | ? :                                                          | 从左到右 |
| 14     | = 　+= 　-= 　*=　 /=　 %=　 &=　 \|=　 ^=　 ~= 　<<= 　>>=　 >>>= | 从右到左 |
| 15     | ，                                                           | 从右到左 |

### 08.流程控制
#### 选择语句
##### if ....else if ..... else

* **必须是boolean类型**

- else 与**最近的 if 匹配**，可以加大括号解决歧义

```JAVA
    if (boolean expr1) {
    	statement1;
    } else if(boolean expr2) {
    	statement2;
    } else {	
    	statement3;
    }
    //注意：
    if (x = 0) {  //ERROR, c++中可以，java中整形和boolean不能相互转换
    	statements;
    }
```
##### switch

* 变量类型可以是： 整型：byte、short、int或者 char。字符串类型, 枚举型
* **注意break**

```JAVA
   switch(常量或常量表达式，枚举，或字符串型) {
   case value1:
       statement1;
       break;  //注意break，没有break会执行statement2
   case value2:
       statement2;
       break;
   default:
       statement2
       break;
   }
```
#### 循环语句
* for
* while
* do-while
* for-each
* break, continue

### 09. 函数

#### 函数基本概念

* **方法不能嵌套定义**
* static（静态）成员函数只能访问static（静态）成员函数


```JAVA
修饰符 返回值类型 方法名(参数类型 参数名1,参数类型 参数名2...) { 
	方法体语句; 
	return 返回值; 
 } 

```

#### 函数重载

* **有相同的函数名**

 - **与返回值类型无关**
 - **参数列表不同**
    - 个数，类型， 顺序（一般不用）

#### 参数传递 

* 按值传递， C++中有按值传递和引用传递
* 一个方法**不能修改一个基本数据类型**的参数 （ 即数值型或布尔型 ） 。
* 一个方法**可以改变一个对象参数的状态** 。如：raiseSalary(Employee x)
* 一个方法**不能让对象参数引用一个新的对象**，如: swap（Employee x, Employee y）, 不改变实参

#### 匿名函数(Lambda表达式)

`形式`: 

```java
(参数列表) -> {
	// Lambda表达式体
}
// 简化形式
//  可以根据上下文判断参数类型
(a, b)-> {
    // 
}
// 只有一个参数
a -> {
	//
}
// 只有一条语句,可省略return 和大括号
a -> a * a
```

`使用条件`:

函数式接口: 这种接口只有一个方法

`用途`:

`作为函数参数传递给方法`:

```JAVA
interface Calculable {
    int calculate(int a, int b);
}

public class Main {
    public static void main(String[] args) {
        int n1 = 10;
        int n2 = 5;

        display((a,b)->{
            return a + b;
        }, n1, n2);   // 使用lambda作为函数参数

        display((a,b)-> {
            return a - b;
        }, n1, n2);  // 使用lambda作为函数参数
    }

    public static void display(Calculable calc, int a, int b) {
        System.out.println(calc.calculate(a, b));
    }
}
```

`未完待续`

### 10. 数组
#### 一维数组

* 数组对象打印格式
  * [F@7852e922
  * [代表是数组,有几个就代表几维（[[表示二维）
  * F代表float类型
  * 7852e922表示数组的地址


* `声明`：**数据类型[] 数组名;**
  - int[] arr;  
* `静态初始化`: 

  * int[] arr = {1,2,3,4,5};
* `动态初始化`：**数据类型[] 数组名 = new 数据类型[数组的长度];** 
  * int[] arr = new int[5];   //默认初始值都为  0 
  * 同c++中： int* arr = new int[5];
  * 在数组元素堆中分配，数组名变量arr在栈中
  * **默认初始值**
    * 整型()：0
    * 浮点型（double，float）： 0.0
    * boolean型：false
    * char型: '\u0000'
    * 引用类型（如：String）：null

#### 二维数组
* **动态初始化：数据类型\[][] 数组名 = new 数据类型\[m][n] (推荐使用这种)**
  - int\[][] arr = new int\[3][4];
* **静态初始化：数据类型\[][] 数组名 = {{}, {}, {}};**
  - int\[][] arr = {{1,3,4}, {2,3,4}};  //等价于 int\[][] arr = new int\[][]  {{1,3,4}, {2,3,4}};
#### 数组遍历
* 逐一通过索引获取

  ```java
  //一维数组
  for (int i = 0; i < arr.length; ++i) {
  	statements;
  }
  //二维数组
  for (int i = 0; i < arr.length; ++i){
      for (int j = 0; j < arr[i].length; ++j) {
          statements;
      }
  }
  ```

* 使用for-each遍历
  ```java
  //一维
  for (int v : arr) {
  	statements;
  }
  //二维
  for (int[] row : arr) {
      for (int col : row) {
          statements;
      }
  }
  ```

#### 用Arrays来操作数组
* import java.util.Arrays; //导入
* Arrays.toString(type[] arr) //把数组转变成字符串
* Arrays.sort(type[] arr)		//排序
* Arrays.binarySearch(type[] arr, type key) //二分查找
* Arrays.fill(type[] arr, type fill) 	//填充
* Arrays.equals(type[] arr1, type[] arr2) //判断相等
* Arrays.copyOf(type[] arr, int new_len) //复制

### 11. 输入输出
#### 输入
##### Scanner
* 标准输入流 ：System.in
* import java.util.Scanner; //导入
* Scanner in = new Scanner(System.in) //构造Scanner对象，并与标准输入流关联
* 常用方法
  * in.nextLine() 	//读取一行
  * in.next() //读取一个单词
  * in.nextInt() //读取一个整数
  * in.hasNextLine()  //判断是否有行输入
  * in.hasNext() //判断是否有输入
  * in.hasNextInt() //判断是否有整数
##### 命令行参数
* 例如:java Hello -h nmsl wsnd
* args[0] = "-h", 与c++不同，c++是 文件名"Hello"
#### 输出 
* System.out.println() //会换行
* System.out.print()   //不会换行
* System.out.printf(format, args)  //同c++



### 面向对象基础知识
#### 类的基本结构

```JAVA
[public] [final | abstract] class className [extends superClass] [implements interfaceName1[,interfaceName2..]]
{
	[public|private|protected] [static] [final] type varname;
	
	[public|private|protected] [static] [abstract | final] [native] [synchronized] type functname([parmlist]) [throws exception] {

	}

}
```



* 类和对象
* 属性和行为
```JAVA
class ClassName
{
    //instance field
	field1;
	field2;
    //constructor
	constructor1;
	constructor2;
    //method
	method1;
	method2;
}
```
* 文件名必须与 public 类的名字相匹配
* 源文件只能有一个公有类， 但可以有任意数目的非公有类 
* 成员变量建议声明为private
* 成员变量的声明和成员函数的声明和调用
* 内存的分析  堆，栈，方法区
* **类之间的关系**
  - is-a 继承
  - has-a 聚合
  - uses-a 依赖
* Java垃圾回收机制， 代替了析构函数
* 所有的方法中不要命名与实例域同名的变量 
* **参数名**：Java中**参数变量用同样的名字将实例域屏蔽起来， 然后通过this.field访问实例域**
* 初始化块
* 成员变量和局部变量的区别
  * 初始值
  * 内存中存储地方
  * 生存周期
  * 就近原则
* 类方法
  - Java定义在类内，但是否是内联由JVM决定；c++一般定义在类外，类内的为内联函数
* **匿名对象**： 只使用一次，节省代码； 可做实参传递
* **final 实例域**
  * 类似于C++中的 const
  * **构造时必须进行初始化**(The blank final field name may not have been initialized)，且后**面的操作不能对它进行修改**（The final field xxx cannot be assigned）
  * 常用于：**基本数据类型**或者**不可变数据类型**（如String）
  * 如果是修饰**可变数据类型**，如 StringBuilder , **表示不能再指向其他对象**， 类似于C++中的常量指针


#### 类的访问控制符：

- public
- default
- private

#### this

- **类成员函数第一个参数为隐式参数(implicit)**，不再声明中写
- 用this表示隐式参数，避免参数名和实例域名相同的冲突, 例如：this->name = name;
- 如果构造器的第一个语句形如 this ( . . . )， 这个构造器将调用同一个类的另一个构造器

#### static

- 可以理解为C++中的**类变量**和**类方法**
- **类对象所共有的**，可以通过 **类名.静态成员** , **类名.静态成员函数**  直接进行访问
- **静态域**
  * 通过 ClassName.field 调用,如：Math.PI

  * **静态成员变量**使用较少，

    * 如果时**静态成员变量最好用private声明**, 防止被类对象通过公有域修改
    * 如: public static int nextId = 1; 

  * **静态成员常量**（final）

    * 静态成员常量可以用public或者private，因为不会被修改
    * 如Math库中的PI：public static final double PI = 3.1415926; 可通过Math.PI访问
    * System.out: public static final PrintStream out = ....;

  * 静态成员变量和成员变量的区别，
- **静态方法**
  * 可通过 ClassName.method 调用, 如：Math.pow(x, a) 
  * 只能访问静态成员,**不能访问非静态的成员变量**
  * 静态成员函数和成员函数的区别
  * 常用来：
    * 1.只需要访问类的静态域 
    * 2.不需要访问对象状态 , 其所需参数都是通过显式参数提供, 如：Math.pow(x, a)
- **工厂函数**
  - 如LocalDate.now()

#### 构造函数

* **基本要求**：
  * 构造器与类**同名**
  * 每个类可以有**一个以上的构造函数**
  * 构造器可以有 **0 个 、 1 个或多个参数**
  * 构造器**没有返回值**
  * 构造器总是**伴随着 new 操作**一起调用	
* **构造函数重载**, 见函数部分的函数重载
* **默认域初始化**：
  * 构造函数中如果没有**显示给域赋予初值**，**会自动赋初值**，数值为 0 、布尔值为 false、对象引用为 null。
  * 只有缺少程序设计经验的人才会这样做 ，一般都会明确的进行初始化
  * 不同于局部变量，**局部变量必须明确初始化**
* **无参默认构造函数**
  * **如果没有编写构造器** ， 那么**系统就会默认提供一个无参数构造器** ，为所有实例域设置为默认值
  * **如果类中提供了至少一个构造器** ， 但是没有提供无参数的构造器 ， 则在构造对象时如果
    没有提供参数就会被视为不合法（The constructor Employee() is undefined）
    * 可以是提供简单的默认构造器: public ClassName() {}
* **调用另一个构造函数**： 如果构造器的第一个语句形如 this ( . . . )， 这个构造器将调用同一个类的另一个构造器
* **构造函数执行过程**：
  * 1 ) 所有数据域被**初始化为默认值** （ 0、 false 或 null )。
  * 2 ) 按照在类声明中出现的次序 ， **依次执行所有 域初始化语句 和 初始化块 。**
  * 3 ) 如果构造器第一行调用了第二个构造器， 则执行第二个构造器主体
  * 4 ) 执行这个构造器的主体 

#### 析构函数

* Java中没有析构函数

*  C + + ,有显式的析构器方法，由于Java 有自动的垃圾回收器， 不需要人工回收内存 ， 所以Java 不支持析构器 
* 析构器中， 最常见的操作是回收分配给对象的存储空间
* finalize方法：某些对象使用了内存之外的其他资源 ，例如， 文件或使用了系统资源的另一个对象的句柄，可以为任何一个类添加 finalize 方法 ，finalize 方法将在垃圾回收器清除对象之前调用 。

#### 封装

* 封装的**基本内容**:
  * private **私有的数据域**
  * public set/get 公有的**访问器和更改器方法**

* **优点**：内部修改对外不可见， 同时set方法可以检查错误

* **注意事项**：

  * get方法不要返回**引用对象**，不然破坏封装性，可以对它进行克隆 .clone()

继承

#### 多态

#### 内部类

* Java语言中允许在一个类（或方法、代码块）的内部定义另一个类，后者称为“内部类”（Inner Classes），也称为“嵌套类”（Nested Classes），封装它的类称为“外部类”
* 内部类一般只用在封装它的外部类或代码块中使用。

### 抽象类

`概念`: 具有抽象方法(只有方法声明,没有方法体; 可以是0个或多个)的类称为抽象类(abstract class)

`特征`: 1.抽象类不能实例化,只有具体类才能实例化;2.如果父类是抽象类，则子类必须实现父类的抽象方法，或者声明为抽象类

`基本形式`:

```JAVA
public abstract class ClassName {
	
	public abstract type funcName();  //抽象方法 
}

public class SubClass extends ClassName {
    
    @Override
    public abstract type funcName() { 
        // 覆盖父类的抽象方法
    }
}
```



### 接口

`概念`: 用interface声明, 接口中的所有方法都是public abstract,所有变量都是public static final.(JAVA8后添加了默认方法和静态方法)

`特征`: 子类实现接口使用关键字implements, 可实现多个接口; 不能实例化; 接口之间可以继承(extends),可多继承

`基本形式`:

```JAVA
// InterfaceName1.java
public interface InterfaceName1 {
	
	type variableName;  // 省略了 public static final
	type funcName();  // 省略public abstract
}
// SubClass.java
public class SubClass implements InterfaceName1 {
    
    @Override
    public type funcName() {
        // 对接口中的方法进行实现
    }
}
```

`JAVA8的默认方法和静态方法`:

```JAVA
public interface InterfaceName1 {

    type funcName();  // 抽象方法,必须实现
    
    default type funcName1() { 
         // 默认方法,可选择实现
    }
    
    static type funcName2() {
        // 静态方法,不需要实现
    }
}
```

`接口和抽象类的区别`:

* 接口可以多继承, 抽象类(包括具体类)只能继承一个父类
* 接口中不能声明实例变量,只有静态变量(public static final), 抽象类各种形式的变量都可以

### 枚举类

### 包

* 为了保证包名的绝对唯一性 Sun 公司建议将公司的**因特网域名 （ 这显然是独一无二的 ） 以逆序**的形式作为包名 ， 并且对于不同的项目使用不同的子包

#### 类的导入

* import  
* import 语句应该位于源文件的顶部， 但位于 package 语句的后面 
* import java.time.*;   和  import java.time.LocalDate; 的区别



### 异常

#### 异常继承层次及分类

```
- Throwable   (java.lang.Throwable)
	- Exception:
		- RuntimeException
			- ArithmeticException
			- NullPointerException
			- IndexOutOfBoundsException
			- ClassCastException
		- IOException
			- FileNotFoundException
		- ParseException
	- Error:  // 无法恢复的严重错误
		- VirtualMechineError
		- LinkageError
		
		
Exception:
	- 受检查的异常  (编译器会检查是否被处理, 要么捕获,要么抛出,否则将编译错误)
		出RuntimeException外的异常类
	- 运行时异常  (编译器不会检查, 可以不捕获不抛出, 编译可以通过, 一般要提前预判防止发生)
		RuntimeException类及其子类
```

##### `Throwable类`:

```JAVA
// 常见方法
String getMessage();  // 获得发生异常的详细消息。
void printStackTrace();  // 打印异常堆栈跟踪信息
String toString();		// 获得异常对象的描述

```

#### 捕获异常

```JAVA
// try-catch-finally
try {
   // 可能产生异常的语句
} catch (Throwable e1) {  // Throwable的子类
    // 异常处理
} catch(Throwable e2) {
    // 异常处理
} finally {
    // 一般用来释放资源
}
```

`注意:`

* 捕获异常顺序与catch代码块的顺序有关。当捕获的多个异常类时,一般先捕获子类,后捕获父类,否则子类捕获不到。
* 注意释放资源(如文件打开关闭,网络连接,数据库连接)

`自动资源管理`: 

Java7以后,try后面添加(),  不用在finally中手动close

前提需要实现AutoCloseable接口

```JAVA
// try-catch-finally
try (声明或初始化资源语句) {
   // 可能产生异常的语句
} catch (Throwable e1) {  // Throwable的子类
    // 异常处理
} catch(Throwable e2) {
    // 异常处理
} finally {
    // 一般用来释放资源
}
```

#### 抛出异常

`throws和throw的区别`:

throws: 用于方法名后声明抛出异常

throw: 用于人工引发异常

`throw`

```JAVA
throw Throwable或其子类的实例;

// 如:
throw new MyException("自定义异常");
```

`throws`

* 本方法没能力处理, 在方法名后面声明抛出的异常

```JAVA
class className {
	[public | protected | private ] [static] [final | abstract] [native] [synchronized]
	type methodName([paramList]) [throws exceptionList] {
	//方法体
	}
}
```



#### 自定义异常

* 继承Exception类或其子类
* 自定义异常一般需要提供两个构造函数,一个默认,一个字符串参数的构造函数

```JAVA

public class MyException extends Exception {

	public MyException() {
	
	}
	public MyException(String message) {  // getMessage()可获得message消息
		super(message)
	}
}

```



### 集合

常见的数据结构: 数组(array), 链表(list), 集合(set), 栈(stack), 队列(queue), 树(tree), 堆(heap), 字典(map)

#### 集合概述

`集合层次`

```JAVA
- Collection<E>: interface
	- List<E>: interface, ***
		- ArrayList<E>: class
    	- LinkedList<E>: class
	- Set<E>: interface, ***
		- HashSet<E>: class
    - Queue<E>: interface, **
- Map<K,V> : interface, ***
    - HashMap<K,V> : class
```

#### Collection

`常用方法`

```JAVA
boolean add(E e);
boolean remove(Object o);
void clear();

int size();	// 返回集合大小
boolean isEmpty();	 // 是否为空
boolean contains(Object o); // 判断是否包含指定元素

Iterator<E> iterator();

```



#### List

`特点`: 关心是否`有序`, 而不关心是否`可重复`

`具体实现类`: ArrayList, LinkedList

ArrayList(动态数组实现),LinkedList(链表)的区别(访问速度,插入删除速度)

`常用方法`: 

```JAVA
get(int index);  // 返回List集合中指定位置的元素
set(int index, Object elem); // 用指定元素替换List集合中指定位置的元素。
add(Object elem); // 在List集合的尾部添加指定的元素
add(int index, Object element); // 在List集合的指定位置插入指定元素
remove(int index); //移除List集合中指定位置的元素。
remove(Object element); // 如果List集合中存在指定元素,则从List集合中移除第一次出现的指定元素
clear(); // 从List集合中移除所有元素。

// 判断元素
boolean isEmpty(); // 是否为空
boolean contains(Object o); // 判断是否包含指定元素

// 查询元素
indexOf(Object o); // 从前往后查找List集合元素,返回第一次出现指定元素的索引,如果此列表不包含该元素,则返回-1
lastIndexOf(Object o); // 从后往前查找List集合元素,返回第一次出现指定元素的索引,如果此列表不包含该元素,则返回-1。

// 其他
iterator(); // 返回迭代器(Iterator)对象,迭代器对象用于遍历集合
size(); // 返回List集合中的元素数,返回值是int类型
subList(int fromIndex, int toIndex); // 返回List集合中指定的 fromIndex(包括 )和toIndex(不包括)之间的元素集合,返回值为List集合。
```

`遍历`:

```JAVA
// 1.for循环
for (int i = 0; i < list.size(); i++) {
	Object item = list.get(i);
}
// 2. for-each遍历
for (Object item: list) {
	//
}
// 3. 迭代器遍历, hasNext(), next()
Interator it = list.iterator();
while (it.hasNext) {
	Object item = it.next();
	// 
}
```



#### Set

`特点`: 关心`不可重复`, `无序`

`具体实现类`: HashSet(散列表)

`常用方法`:

```JAVA
void add(Object elem); // 在Set集合中添加指定元素\
void remove(Object element); // 如果Set集合中存在指定元素,则从Set集合中移除
void clear(); // 从List集合中移除所有元素。

// 判断元素
boolean isEmpty(); // 是否为空
boolean contains(Object o); // 判断是否包含指定元素

// 其他
Interator<E> iterator(); // 返回迭代器(Iterator)对象,迭代器对象用于遍历集合
int size(); // 返回Set集合中的元素数,返回值是int类型

```

`遍历`:

```
// 1.for-each
// 2.使用迭代器
```



#### Map

`特点`: 映射(键值对), 键(Set类型,不能有重复), 值(Collection类型,可重复)

`具体实现类`: HashMap

`常用方法`:

```JAVA
get(Object key); // 返回指定键所对应的值;如果Map集合中不包含该键值对,则返回null。
put(Object key, Object value); // 指定键值对添加到集合中,键已存在会替换
remove(Object key); // 移除键值对。
clear(); // 移除Map集合中所有键值对。

// 判断元素
isEmpty() // 判断Map集合中是否有键值对,没有返回true,有返回false。
containsKey(Object key); // 判断键集合中是否包含指定元素,包含返回true,不包含返回false。
containsValue(Object value); // 判断值集合中是否包含指定元素,包含返回true,不包含返回false。

// 查看集合
keySet(); // 返回Map中的所有键集合,返回值是Set类型。
values(); // 返回Map中的所有值集合,返回值是Collection类型。
size(); // 返回Map集合中键值对数。
```

`遍历`:

```JAVA
// 1. 遍历键
Set keys = map.keySet();
for (Object key : keys ) {
    Object val = map.get(key);
}
// 2. 遍历值
Collection values = map.values();
Iterator it = values.iterator();
while (it.hasNext()) {
    Object item = it.next();
}

```



#### Stack

`简介`: LIFO, extends Vector

`改进`: 用 Deque

`创建`:

```Java
Stack<E> stack = new Stack<E>();
```

`常用方法`: 

```Java
void push(E item)  # push an item onto the top of stack
E pop()		  # return the top item of stack, and remove it 
E peek()	  # return the top item of stack, without remove 
bool empty()  # Test if stack is empty
```

`应用实例`:

> 1. leetcode 20 Valid Parentheses



### Java常用类

#### Object

* java.lang.Object类，它是Java所有类的根类

* 如果没有覆盖toString()方法，默认的字符串是“类名@对象的十六进制哈希码 ”。

* String toString()  返回该对象的字符串表示。

  ```JAVA
  public class Person {
      
      private String name;
      private int age;
      
      public Person(String name, int age) {
          this.name = name;
          this.age = age;
      }
      
      @Override
      public String toString() {
      	return "Person [name=" + name + ", age=" + age + "]";
      }
      
      @Override
  	public boolean equals(Object otherObject) {
          
  		if (this == otherObject) 
  			return true;
  		if (otherObject == null)
  			return false;
  		if (!(otherObject instanceof Person))
  			return false;
  
  		Person otherPerson = (Person) otherObject;
  		if (this.age == otherPerson.age && Objects.equals(name, otherPerson.name)) {
  			return true;
  		} else 
  			return false;
  	}
      
  }
  // Person [name=Tony, age=18]
  // xxx.Person@15db9742
  ```

* boolean equals(Object obj)：指示其他某个对象是否与此对象“相等”。

  * 区别于==比较是否指向同一内存，equals()通常比较内容

#### Math类

* **静态导入**: import  **static** java.lang.Math.*; 

|||
|--|--|
|**常量**||
|Math.PI|圆周率PI|
|Math.E|自然对数的底数E|
|**舍入方法**||
| long **round**(double) | 四舍五入 |
| int **round**(float) | 四舍五入 |
| double **floor**(douule a) |返回小于或等于a最大整数。|
| double **ceil**(double a) |返回大于或等于a最小整数。|
| **最大值和最小值** ||
|int **min**(int a, int b)|取两个int整数中较小的一个整数。|
|int **min**(long a, long b)|取两个long整数中较小的一个整数。|
|int **min**(float a, float b)|取两个float浮点数中较小的一个浮点数。|
|int min(double a, double b)|取两个double浮点数中较小的一个浮点数。|
|**平方根**||
|double **sqrt**(double a)|返回a的正平方根|
|**幂运算**||
|double **pow**(double a, double a)|返回第一个参数的第二个参数次幂的值。|
|**绝对值**||
|int **abs**(int a)|取int整数a的绝对值。|
|long **abs**(long a)|取long整数a的绝对值。|
|float abs(float a)|取float浮点数a的绝对值。|
|double abs(double a)|取double浮点数a的绝对值|
|**三角函数：**||
|double sin(double a)|返回角a的三角正弦。|
|double cos(double a)|返回角a的三角余弦。|
|double tan(double a)|返回角a的三角正切。|
|double asin(double a)|返回a的反正弦。|
|double acos(double a)|返回a的反余弦。|
|double atan(double a)|返回a的反正切。|
|double **toDegrees**(double angrad)|将弧度转换为角度。|
|double **toRadians**(double angdeg)|将角度转换为弧度。|
|**指数：**||
|double **exp**(double a)||
|double **log**(double a)|返回a的自然对数。|
|double log10(double a)||
|**随机数**||
|double **random**()|返回大于等于 0.0 且小于 1.0随机数。|

#### BigInteger类

* 导入: import java.math.BigInteger;

* c++能重载运算符，java只能用add之类的函数名
|||
|--|--|
|**构造函数**||
|BigInteger(String val) | 将十进制字符串val转换为BigInteger对象 |
|BigInteger(String val, int radix) | 按照指定基数radix将字符串val转换为BigInteger对象 |
|BigInteger.**valueof**(long x) |返回等于x的BigInteger对象|
|**加减乘除**||
|BigInteger **add**(BigInteger val) | 加运算，当前对象数值加参数val。|
|BigInteger **subtract**(BigInteger val)|减运算，当前对象数值减参数val。|
|BigInteger **multiply**(BigInteger val)|乘运算，当前对象数值乘参数val。|
|BigInteger **divide**(BigInteger val)|除运算，当前对象数值除以参数val。|
|BigInteger **mod**(BigInteger val)||
|**比较**||
|int **compareTo**(BigInteger val) |将当前对象与参数val进行比较, =返回0，<负数，>正数|
|**Number的六个方法**||
|intValue||
|doubleValue||
|floatValue||
|longValue||
|shortValue||
|byteValue||

```java
import java.math.BigInteger;

public class Test {

	public static void main(String[] args) {
		//constructor
		BigInteger num1 = new BigInteger("1234567891321");
		BigInteger num2 = new BigInteger("12312312", 16);
		BigInteger num3 = BigInteger.valueOf(999999999);
		
		//+-*/%
		System.out.println(num1.add(num2));
		System.out.println(num1.subtract(num2));
		System.out.println(num1.multiply(num2));
		System.out.println(num1.divide(num2));
		System.out.println(num1.mod(num2));
		
		//
		System.out.println(num1.compareTo(num2));
		//
		System.out.println(num1.intValue());
	}

}

```



#### BigDecimal
* import java.math.BigDecimal;

* c++能重载运算符，java只能用add之类的函数名
|       |       |
| ------- | ------------------- |
| **构造函数**  |        |
|BigDecimal(String val)     | 将字符串val转换为BigDecimal对象  |
|BigDecimal(BigInteger val) | 将BigInteger对象val转换为BigDecimal对象。|
|BigDecimal(double val)|将double转换为BigDecimal对象，参数val是double类型的二进制浮点值准确的十进制表示形式|
|BigDecimal(int val)|将int转换为BigDecimal对象。|
|BigDecimal(long val)|将long转换为BigDecimal对象|
| BigDecimal.**valueof**(long x)  | 返回等于x的BigDecimal对象  |
| **加减乘除**  |              |
| BigDecimal **add**(BigDecimal val) | 加运算，当前对象数值加参数val。  |
| BigDecimal **subtract**(BigDecimal val) | 减运算，当前对象数值减参数val。 |
| BigDecimal **multiply**(BigDecimal val) | 乘运算，当前对象数值乘参数val。 |
| BigDecimal **divide**(BigDecimal val) | 除运算，当前对象数值除以参数val  |
|BigDecimal **divide**(BigDecimal val, int **roundingMode**)|除运算，当前对象数值除以参数val。roundingMode要应用的舍入模式|
| BigDecimal **mod**(BigDecimal val)  |  |
| **比较**      |        |
| int **compareTo**(BigDecimal val)  | 将当前对象与参数val进行比较, =返回0，<负数，>正数 |
| **Number的六个方法**    |    |
| intValue   |         |
| doubleValue    |              |
| floatValue   |          |
| longValue    |     |
| shortValue  |      |
| byteValue        |            |

```java
import java.math.BigDecimal;

public class Test {

	public static void main(String[] args) {
		// constructor
		BigDecimal num1 = new BigDecimal("99999999.99999999"); //str
		BigDecimal num2 = new BigDecimal(231321321321.3213213213); //double
		BigDecimal num3 = BigDecimal.valueOf(12312);
		BigDecimal num4 = BigDecimal.valueOf(12312.321321);
		
		//+-*/
		System.out.println(num1.add(num2));
		System.out.println(num1.subtract(num2));
		System.out.println(num1.multiply(num2));
		System.out.println(num1.divide(num2, BigDecimal.ROUND_HALF_EVEN));
		//
		System.out.println(num2.intValue());

	}

}
```



#### Random类

* import java.util.Random;
* Random()  构造一个新的随机数生成器
* int nextInt(int n)   返回一个 0 ~ n - 1之间的随机数



#### Date  时间

- 太老了，不看

- new Date()

- new Date(Long类型的)

- getTime() ,  equals() ,  setTime(),  compareTo()

  

#### LocalDate 不可变的日期对象 （jdk8.0才有）
* **不可变**
* **导入**:  import java.time.LocalDate;
* **没有提供构造器来构造** LocalDate 类的对象, 只提供了**静态工厂方法**
* **方法**
|||
|--|--|
|**静态工厂方法**||
|LocalDate **now**()|使用默认时区获得当前日期，返回LocalDate对象。|
|LocalDate **of**(int year, int month, int dayOfMonth)|按照指定的年、月和日获得一个LocalDate实例，日期中年、月和日必须有效，**否则将抛出异常****。|
|**获得年月日**||
|getYear() | |
| getMonthValue()||
|getDayOfMonth()||
|getDayOfWeek()|返回的是DayOfWeek， 可通过.getValue()获得1-7之间数字,getDayOfWeek().getValue() |
|getDayOfYear()||
|**生成当前日期之前minus和之后plus**||
|plusDays(int n)||
|plusMonths(int n)||
|plusWeeks(int n)||
|plusYears(int n)||
|**判断闰年**||
|isLeapYear()||
|**日期解析**||
|LocalDate **parse**(CharSequence text) | 使用默认格式，从一个文本字符串获取一个LocalDate实例，如2007-12-03|
|LocalDate **parse**(CharSequence text, DateTimeFormatter formatter)|使用指定格式化,从文本字符串获取LocalDate实例|

* **example**
```java
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;

public class Test {
	public static void main(String[] args) {
		//now
		LocalDate date1 = LocalDate.now();
		System.out.println(date1);
		//of
		LocalDate date2 = LocalDate.of(2018, 8, 18);
		System.out.println(date2);
		//get
		System.out.println(date1.getYear() + " " + 
				date1.getMonthValue() + " " + 
				date1.getDayOfWeek().getValue());
		//plus
		System.out.println(date1.plusDays(1));
		//minus
		System.out.println(date1.minusDays(2));
		//format
		DateTimeFormatter formatter = DateTimeFormatter.ofPattern("MM-dd-yyyy");
		String text = date1.format(formatter);
		System.out.println(text);
		//parse
		formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd");
		LocalDate parseDate = LocalDate.parse("2018-08-18", formatter);
		System.out.println(parseDate);
	}
}
```
* **常用的日期和时间格式**
|||
|--|--|
|y |年|
|M |年中的月份|
|D |年中的天数|
|d |月份中的天数|
|H |一天中的小时数（ 0 -23 ）|
|h |AM/PM 中的小时数（1-12）|
|a |AM/PM 标记|
|m |小时中的分钟数|
|s |**分钟中的秒数**|
|S |毫秒数|
|Z |时区|
#### LocalTime 不可变的时间对象（jdk8.0才有）

- **不可变**
- **导入**:  import java.time.LocalTime;
- **没有提供构造器来构造** LocalTime 类的对象, 只提供了**静态工厂方法**

|||
|--|--|
|**静态工厂方法**||
|LocalTime  now()|使用默认时区获得当前时间，返回LocalTime对象|
| LocalTime of(int hour, int minute, int second)|按照指定的小时、分钟和秒获取一个LocalTime实例。|

#### LocalDateTime 表示一个不可变的日期和时间（jdk8.0才有）

- 不可变**
- **导入**:  import java.time.LocalDateTime;
- **没有提供构造器来构造** LocalDateTime 类的对象, 只提供了**静态工厂方法**

|||
|--|--|
|**静态工厂方法**||
| LocalDateTime  now()|使用默认时区获得当前日期时间，返回LocalDateTime对象。|
|LocalDateTime of(int year, int month, int dayOfMonth, int hour, int minute, int second)|按照指定的年、月、日、小时、分钟和秒获得LocalDateTime实例，将纳秒设置为零。|

#### **ArrayList**

* **import java.util.ArrayList;**

* **声明**

  * ```java
    ArrayList<Employee> staff = new ArrayList<Employee>();
    //或者菱形语法：
    ArrayList<Employee> staff = new ArrayList<>();
    ```

* **a = b 表示a 和 b 引用同一个数组列表 。**

* **删除，插入效率很低，频繁增删选择链表**

* **利用toArray拷贝到数组中**

  * ```Java
    ArrayList<T> list = new ArrayList<>()；
    T[] a = new T[list.size()] ;
    list.toArray ( a ) ;
    
    ```

* **for-each 遍历**

  * ```java
    for (T e : list) 
    	do something with e 
    //等价
    for (int i = 0; i < list.size(); ++i) {
    	T e = list.get(i);
    	do something with e 
    }
    ```
|**常用方法**||
|--|--|
| **ArrayList<T>( )** | **构造一个空数组列表** |
| **ArrayList<T> (int initialCapacity)** | **用指定容量构造一个空数组列表** |
| **boolean add(T obj)** | **添加，在数组列表的尾端添加一个元素,永远返回 true** |
| **void add(int index, T obj)** |**添加，向后移动元素，以便插入元素**|
| **void set (int index， T obj)** |**更改，设置数组列表指定位置的元素值** |
| **T remove (int index)** | **删除,  删除指定位置的一个元素，并返回** |
| **T get(int index)** | **访问， 获得指定位置的元素值** |
| **int size()** | **返回存储在数组列表中的当前元素数量** |
| **void ensureCapacity (int capacity)** | **确保数组列表元素的最少数量** |
| **void trimToSiz( )** | **将数组列表的存储容量削减到当前尺寸** |
| **T[] toArray(T[] a)** | **返回T类型的数组** |
### **eclipse的操作**

* **恢复布局：window->perspective->reset perspective**

* **字体方法和缩小：ctrl shift + 放大，  ctrl - 缩小 ；或者 window->perference->Apparence->Color and Font->Basic->Text Font**
* **打开文件/项目所在的目录: 右键 property,点击打开**
* **更改项目编码：右键 propert 编码改成utf-8**
* **删除项目：勾和不勾的区别**
* **导入项目：File->import->General->Existing Project..->Browse->Copy project into Workspace**
* **块选择：alt + shift + a**
* **打开在线文档：shift + F2** 
* **快速补全：alt + / ,如 sysout, 然后按alt+/**
* **全局代理：window->perference->General->Network Connection->Manual->127.0.0.1, 8080(http,https), 1080(sock)**
* **alt + shift + S Source快捷键**
* **改名：右键 Refactor**
* **右键 Source  可快速创建构造函数和set/get**

* **快捷键**

|	|	|
| --------------------------- | ------------ |
|	|	|
| **Ctrl + Alt + Up(向上方向键)** | **复制到上一行** |
| **Ctrl + Alt + Down(向下方向键)** | **复制到下一行** |

****

### IDEA 使用

#### 快捷键

|                |               |      |
| -------------- | ------------- | ---- |
| 换行           | SHIFT + ENTER |      |
| 对提示快速补全 | ALT + ENTER   |      |
|                |               |      |
|                |               |      |
|                |               |      |
|                |               |      |
|                |               |      |
|                |               |      |
|                |               |      |

