# saf-logginginterceptor

[![@Tony沈哲 on weibo](https://img.shields.io/badge/weibo-%40Tony%E6%B2%88%E5%93%B2-blue.svg)](http://www.weibo.com/fengzhizi715)
[![Download](https://api.bintray.com/packages/fengzhizi715/maven/saf-logginginterceptor/images/download.svg)](https://bintray.com/fengzhizi715/maven/saf-logginginterceptor/_latestVersion)
[![License](https://img.shields.io/badge/license-Apache%202-lightgrey.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)
<a href="http://www.methodscount.com/?lib=com.safframework.log%3Asaf-logginginterceptor%3A1.0.4"><img src="https://img.shields.io/badge/Methods and size-core: 157 | deps: 25898 | 30 KB-e91e63.svg"/></a>

# 一. 特性

* 支持http request、response的数据格式化的输出。
* 当请求为Post时，支持Form表单的打印。
* 支持超长日志的打印，解决了Logcat 4K字符截断的问题。
* 支持格式化时去掉竖线边框显示日志。方便将网络请求复制到Postman之类的工具，方便将请求结果复制给服务端的同学。
* 支持日志级别

# 二. 下载安装
  Gradle:

```groovy
implementation 'com.safframework.log:saf-logginginterceptor:1.4.2'
```  


# 三. 使用方法
它是用于记录OKHttp网络请求的日志的拦截器，纯Kotlin编写

## 3.1 在Java中使用

```java
            OkHttpClient.Builder builder = new OkHttpClient.Builder();
            builder.writeTimeout(30 * 1000, TimeUnit.MILLISECONDS);
            builder.readTimeout(20 * 1000, TimeUnit.MILLISECONDS);
            builder.connectTimeout(15 * 1000, TimeUnit.MILLISECONDS);

            LoggingInterceptor loggingInterceptor = new LoggingInterceptor.Builder()
                    .loggable(true) // TODO: 发布到生产环境需要改成false
                    .request()
                    .requestTag("Request")
                    .response()
                    .responseTag("Response")
                    //.hideVerticalLine()// 隐藏竖线边框
                    .build();

            //设置拦截器
            builder.addInterceptor(loggingInterceptor);
```

## 3.2 在Kotlin中使用

```kotlin
        val builder = OkHttpClient.Builder()
        builder.writeTimeout((30 * 1000).toLong(), TimeUnit.MILLISECONDS)
        builder.readTimeout((20 * 1000).toLong(), TimeUnit.MILLISECONDS)
        builder.connectTimeout((15 * 1000).toLong(), TimeUnit.MILLISECONDS)

        val loggingInterceptor = LoggingInterceptor.Builder()
                .loggable(true) // TODO: 发布到生产环境需要改成false
                .request()
                .requestTag("Request")
                .response()
                .responseTag("Response")
                //.hideVerticalLine()// 隐藏竖线边框
                .build()

       //设置拦截器
       builder.addInterceptor(loggingInterceptor)
```

# 四. 效果显示

## 4.1 Get请求显示的效果：

![](images/Get请求.png)


## 4.2 返回Response的效果：

![](images/返回有边框的Response.png)


## 4.3 隐藏竖线边框，方便复制request、reqponse的内容：

![](images/隐藏边框的效果.png)


联系方式
===

Wechat：fengzhizi715

> Java与Android技术栈：每周更新推送原创技术文章，欢迎扫描下方的公众号二维码并关注，期待与您的共同成长和进步。

![](https://github.com/fengzhizi715/NetDiscovery/blob/master/images/gzh.jpeg)

License
-------

    Copyright (C) 2017 - present, Tony Shen.

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
