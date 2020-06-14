---
title: 使用ProGuard混淆你的JAVA代码
copyright: true
date: 2020-06-14 18:08:11
tags:
categories:
comments:
password:
---

在Maven项目中使用Proguard十分简单 只要在pom文件的<plugins>标签内添加如下代码即可
```

            <!-- ProGuard混淆插件-->
            <plugin>

                <groupId>com.github.wvengen</groupId>
                <artifactId>proguard-maven-plugin</artifactId>
                <version>2.1.0</version>
                <executions>
                    <execution>
                        <!-- 混淆时刻，这里是打包的时候混淆-->
                        <phase>package</phase>
                        <goals>
                            <!-- 使用插件的什么功能，当然是混淆-->
                            <goal>proguard</goal>
                        </goals>
                    </execution>
                </executions>
                <configuration>
                    <!-- 是否将生成的PG文件安装部署-->
                    <attach>true</attach>
                    <!-- 是否混淆-->
                    <obfuscate>true</obfuscate>
                    <!-- 指定生成文件分类 -->
                    <attachArtifactClassifier>pg</attachArtifactClassifier>
                    <options>
                        <!-- JDK目标版本1.8-->
                        <option>-target 1.8</option>
                        <!-- 不做收缩（删除注释、未被引用代码）-->
                        <option>-dontshrink</option>
                        <!-- 不做优化（变更代码实现逻辑）-->
                        <option>-dontoptimize</option>
                        <!-- 不路过非公用类文件及成员-->
                        <option>-dontskipnonpubliclibraryclasses</option>
                        <option>-dontskipnonpubliclibraryclassmembers</option>
                        <!--不用大小写混合类名机制-->
                        <option>-dontusemixedcaseclassnames</option>

                        <!-- 优化时允许访问并修改有修饰符的类和类的成员 -->
                        <option>-allowaccessmodification</option>
                        <!-- 确定统一的混淆类的成员名称来增加混淆-->
                        <option>-useuniqueclassmembernames</option>
                        <!-- 不混淆所有包名-->
                        <option>-keeppackagenames</option>

                        <!-- 需要保持的属性：异常，注解等-->
                        <option>-keepattributes Exceptions,InnerClasses,Signature,Deprecated,SourceFile,*Annotation*,Synthetic,EnclosingMethod</option>
                        <!-- 不混淆所有的set/get方法 -->
                        <option>-keepclassmembers public class * {void set*(***);*** get*();}</option>
 						<!-- 不混淆所有的services.dao.ChargeDAO类内的所有方法方法 -->
                        <option>-keep class services.dao.ChargeDAO { *; }</option>


                    </options>
                    <!--class 混淆后输出的jar包-->
                    <outjar>hx.jar</outjar>
                    <!-- 添加依赖，这里你可以按你的需要修改，这里测试只需要一个JRE的Runtime包就行了 -->
                    <libs>
                        <lib>${java.home}/lib/rt.jar</lib>
                        <lib>${java.home}/lib/jce.jar</lib>
                    </libs>
                    <!-- 对什么东西进行加载，这里仅有classes成功，毕竟你也不可能对配置文件及JSP混淆吧-->
                    <injar>classes</injar>
                    <!-- 输出目录-->
                    <outputDirectory>${project.build.directory}</outputDirectory>
                </configuration>

            </plugin>


```
