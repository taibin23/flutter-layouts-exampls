---
description: Kotlin 介绍
---

# Kotlin开始

### 学习网站

官网 [https://kotlinlang.org/docs/reference/](https://kotlinlang.org/docs/reference/)

中文网站：[http://www.kotlincn.net/docs/reference/](http://www.kotlincn.net/docs/reference/)

练写 [https://www.tutorialspoint.com/kotlin/index.htm](https://www.tutorialspoint.com/kotlin/index.htm)

## 安装

安装之前，需要已经安装android相关的一些配置，JDK,SDK

1.在工程build.gradle 中配置

```text
buildscript {
    ext.kotlin_version='1.3.10'
    repositories {
        google()
        jcenter()
        
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.3.2'
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"

        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}
```

2. 在model的build.gradle中配置

```text
apply plugin: "kotlin-android"
apply plugin: 'kotlin-android-extensions'//非必须
```

3.安装插件kotlin

配置完成后，需要同步工程，然后就可以使用kotlin了

4. Hello world

activity\_main.xml

```markup
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

  <Button
      android:id="@+id/btn_toast"
      android:layout_width="wrap_content"
      android:layout_height="wrap_content" 
      android:text="Click me"/>

</LinearLayout>
```

MainActivity

```kotlin
package com.nb.demo0313

import android.app.Activity
import android.os.Bundle
import kotlinx.android.synthetic.main.activity_main.*

/**
 * Created by NieBin on 2019/3/26
 * Github: https://github.com/nb312
 * Email: niebin312@gmail.com
 */
class  MainActivity: Activity(){
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        btn_toast.setOnClickListener {
            println("You have clicked me.")
        }
    }
}
```







