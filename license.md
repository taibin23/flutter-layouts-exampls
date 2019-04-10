---
description: 一些基础使用
---

# 基础

## 变量 

```kotlin
var a:Int=0 // kotlin不需要分号结束，类型在后，变量在前
var b = 0
var c:Int?    
```

```java
int a = 0;// java 类型在前，变量在后
```

## 方法

```kotlin
  fun sayHello(name:String="NieBin",content:String="Hello world"):String{
        return "$name speak $content"
  }//可以带默认参数
  调用时直接 
  sayHello()
  sayHello(name = "张三")
  sayHello("李四","你好")
```

```java
public String sayHello(String name,String content){
    return name+" speak "+content;
}
调用时只有一种形式，并且不支持默认值
```

## 类/对象

1. 定义时和java类似，但是构造函数有较大的不同，kotlin分主构造函数和次构造函数，主构造函数只有一个，次构造函数可有多个，但是次构造函数必须调用主构造函数
2. 当需要继承某个类时，需要在前面添加open关键字，而想要让某个函数可重写，也需要加open关键字
3. 如果此方法是在接口中，则不需要添加open关键字

```kotlin
open class A(var a: Int) {
    constructor(a: Int, b: Int) : this(a) {
        println("a=$a b=$b")
    }
    open fun printA(){
        println("a = $a")
    }
    fun printB(){
        println("a = $a")
    }
}
class B(a:Int):A(a){
    init {
        println("a = ${this.a}")
    }
    
    constructor(a:Int, b:Int):this(a){
        
    }

    override fun printA() {
        super.printA()
    }
}
```

## 控制语句

1. 和java一样，支持if,while,for  但是不支持switch语句，改为了when语句，

    2. if,when语句带有返回值

    3. 不支持for each

```kotlin
    fun control(a: Int, arr: MutableList<Int>) {
        var b = if (a == 1) {
            println("")
            10 //必须是最后一行
        } else {
            20//必须是else的最后一行
        }

        while (b > 0) {
            b--
            println("while b = $b")

        }
        var c = when (b) {
            10 -> "a"
            20 -> "b"
            else -> "c"

        }
        println("c = $c")
        for((index,value) in arr.withIndex()){
            println("index = $index, value= $value")
        }
    }
```

## 文件

在JAVA中一个java文件一般对于一个类，方法及变量是不能独立于类而存在。但是在kotlin中一个文件可以包含变量，方法，类，接口，比较随意

```kotlin
var height: Int = 100
fun speakName() {
    println("The height of the room is $height")
}

class Room {
    var name: String = "ShangHai"
    var w: Int = 0
    var h: Int = 0
}

interface ISell {
    fun onSelling()
}
```

## 静态实现

关键词，在java中我们经常会用到工具类调用一些静态方法或者是变量，但是在kotlin中没有静态的概念，但是可以利用关键词object达到相应的效果，本质上这是一个单例，而不同于

```kotlin
object CommonUtil {
    var name: String = "niebin"
    fun getAge(): Int {
        return 18
    }
}
fun test() {
    println("name is ${CommonUtil.name} and age is ${CommonUtil.getAge()}")
}
```

如果是类，则可以使用  `companion object` 

```kotlin
class Room {
    var name: String = "ShangHai"
    var w: Int = 0
    var h: Int = 0

    companion object {
        var address: String = "China"
        //这里还可以定义方法，属性
    }
}

fun test() {
    println("The address of your room is ${Room.address}")
}
```







