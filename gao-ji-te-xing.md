# 高级特性

## findViewById

在java解决findViewById的方式有butterKnife 和DataBinding,但是在kotlin更方便了,只要通过简单的配置就可以引用xml文件中的view，

1. 在model 级的 gradle 文件添加插件并同步，只做一次就行

```kotlin
apply plugin: 'kotlin-android-extensions'
```

2. 在自己的activity或其他和布局相关的类，直接调用由id生存的view.例子如下

```markup
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/btn_test"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:text="Hello" />
</LinearLayout>
```

在代码中直接btn\_test 并安装快捷键引入包就可以使用此view,这个代表button的变量是自动生成的，所以不用自己定义，不用自己初始化

```kotlin
  btn_test.setOnClickListener {
            println("Hello world")
  }
```

## 扩展 

{% embed url="https://juejin.im/post/5a1be4cc51882512a86108f8" %}

{% embed url="https://blog.csdn.net/ljd2038/article/details/79576091" %}



## 委托

{% embed url="https://blog.csdn.net/zxc123e/article/details/73836013" %}





