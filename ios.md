---
description: 一些基础特性
---

# 特性

## 判断为空

在java中我们为了防止空指针，都会判断变量是否为空，但是在kotlin中，我们只要简单的问号就可以避免这样的问题

```kotlin
var age:Int?=0
val large=age?.compareTo(2)//这样age不用判断空就可以安全调用了   
```

## 方法

除了前面说的带默认值外，kotlin已经把方法玩出了花

1. **方法内部还可以定义方法**

这是比较好的，当某个小模块重复被调用，逻辑还有点复杂的时候，你就需要在他的内部定义这样一个小方法

```kotlin
    fun ronStart(a:Int,b:Int){
        fun max():Int{
            return  if(a>b) a else b
        }
        val max= max()
        if(max>=0){
            println("This variable is right.")
        }else{
            println("This variable is minus.")
        }
    }
```

#### 2. 扩展方法/扩展属性

这个是kotlin的神器，使用它可以极大地方便代码的调用，方便不是一点的两点，但是也要注意不要滥用，滥用会导致程序的可读性性降低

简单运用

```kotlin
open class A(var a: Int) {

    open fun printA() {
        println("a = $a")
    }

    fun printB() {
        println("a = $a")
    }
}

fun A.printC() {
    printA()
    printA()
}
```

简单的封装

[https://github.com/nb312/Kotlin-Extension](https://github.com/nb312/Kotlin-Extension)

#### 3. 方法作为参数

方法可以作为方法的参数或者返回值

```kotlin
fun ambd(name: String, max: (a: Int, b: Int) -> Int) {

    var max = max(11, 21)
    println("my name is $name and the max is $max")

}
fun test() {
    
    var m = { a: Int, b: Int ->
        if (a > b) a else b
    }
    ambd("Nie Bin", m)

}
```



## Parcelable & Data Class 

简化数据类的书写

```kotlin
@Parcelize
class User(val firstName: String,
           val lastName: String,
           val age: Int) : Parcelable
```

```kotlin
data class Person(var name: String = "niebin")
```

java中的实现

```java
public class Banana implements Parcelable {
    private String name;

    protected Banana(Parcel in) {
        name = in.readString();
    }

    public static final Creator<Banana> CREATOR = new Creator<Banana>() {
        @Override
        public Banana createFromParcel(Parcel in) {
            return new Banana(in);
        }

        @Override
        public Banana[] newArray(int size) {
            return new Banana[size];
        }
    };

    @Override
    public int describeContents() {
        return 0;
    }

    @Override
    public void writeToParcel(Parcel dest, int flags) {
        dest.writeString(name);
    }
}
```

























