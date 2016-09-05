# **Recovery**
A crash recovery framework!

----

[ ![Download](https://api.bintray.com/packages/sunzxyong/maven/Recovery/images/download.svg) ](https://bintray.com/sunzxyong/maven/Recovery/_latestVersion)

[英文文档](https://github.com/Sunzxyong/Recovery/blob/master/README.md)

# **Introduce**

“Recovery”帮助你自动处理程序在运行时的Crash，它含有以下几点功能

* 自动恢复Activity Stack和数据
* 支持只恢复栈顶Activity
* Crash信息的显示与保存
* 应用重启或者清空缓存
* 一分钟内两次恢复失败不再恢复而进行重启应用

# **Art**
![Recovery](http://7xswxf.com2.z0.glb.qiniucdn.com/blog/Recovery.png)

# **Usage**
## **Reference**
**Gradle**

```
		compile 'com.zxy.android:recovery:0.0.2'
```

**Maven**

```
		<dependency>
  			<groupId>com.zxy.android</groupId>
  			<artifactId>recovery</artifactId>
  			<version>0.0.2</version>
  			<type>pom</type>
		</dependency>
```
## **Init**
在你自定义的Application中初始化

```java
        Recovery.getInstance()
                .debug(true)
                .recoverInBackground(false)
                .recoverStack(true)
                .mainPage(MainActivity.class)
                .callback(new MyCrashCallback())
                .init(this);
```

## **Arguments**

| Argument | Type | Function |
| :-: | :-: | :-: |
| debug | boolean | 是否开启debug模式 |
| recoverInBackgroud | boolean | 当应用在后台时发生Crash，是否需要进行恢复  |
| recoverStack | boolean | 是否恢复整个Activity Stack，否则将恢复栈顶Activity |
| mainPage | Class<? extends Activity> | 回退的界面 |
| callback | RecoveryCallback | 发生Crash时的回调 |

## **Callback**

```
public interface RecoveryCallback {

    void stackTrace(String stackTrace);

    void cause(String cause);

    void exception(String throwExceptionType, String throwClassName, String throwMethodName, int throwLineNumber);
}
```

## **Custom Theme**

自定义RecoveryActivity的主题，需重写以下styles属性：

```
    <color name="recoveryColorPrimary">#F44336</color>
    <color name="recoveryColorPrimaryDark">#D32F2F</color>
    <color name="recoveryColorAccent">#BDBDBD</color>
    <color name="recoveryTextColor">#FFFFFF</color>
```
## **Crash File Path**
> {SDCard Dir}/Android/data/{packageName}/files/recovery_crash/

# **LICENSE**

```
   Copyright 2016 zhengxiaoyong

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```
