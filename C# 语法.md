# C# 6 新增语法

##   1.自动只读属性

~~~c#
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;//单行才能用goes to 箭头
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this,
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
~~~

##   2.静态导入 using static

~~~C#
using static System.Math;

using static System.Console;
using static Test;

Show();
WriteLine(Sqrt(3*3+4*4))
    
public Class Test
{
    public static void Show();
}
~~~

##   3.Null  条件 运算符

##   4.字符串内插

##   5.异常筛选器

##    6.nameof表达式

##   7.使用索引器初始化关联集合

---



# C#7新增语法 

1. out变量
2. 元组
3. 弃元 
4. 模式匹配
5. ref局部变量和返回结果
6. 本地函数
7. 更多的expression-bodie成员 
8. throw表达式
9. 通用的异步返回类型
10. 数字文本语法改进

---



# *C#8 新增语法*

1. readonly 成员 
2. 默认接口方法
3. 模式匹配增加功能
4. using声明
5. 静态本地函数 
6. 可处置的ref结构
7. 可为空应用类型
8. 异步流
9. 异步可释放
10. 索引和范围
11. Null合并赋值

---



# **C#9 新增语法**



~~~C#
public static void Show()
{
    Console.WriteLine("test");
}
~~~

[百度](http://www.baidu.com)



数学公式

$$回车





