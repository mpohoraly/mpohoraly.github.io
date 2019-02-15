---
layout: post
title: Java External Properties File
tags: Java 
---

When loading properties file in Java one would mostly do something like this:
```java
public class ConfigHandler {
    
    public ConfigHandler() {
        try {
            Properties prop = new Properties();
            prop.load(ConfigHandler.class.getClassLoader().getResourceAsStream("application.properties"));
```
It loads properties file located in *classes* folder, but if you need to load properties file located in folder specified by classpath argument of JVM:
```sh
$ java -cp "/jar-folder/config-test-1.0-SNAPSHOT.jar:/properties-folder/" ConfigRun
```
You have to use top class loader accessible by *ClassLoader.getSystemClassLoader()* which is only class loader able to access resoucres specified by classpath (*syn.* cp):
```java
public class ConfigHandler {

    public ConfigHandler() {
        try {
            Properties prop = new Properties();
            prop.load(ClassLoader.getSystemClassLoader().getResourceAsStream("application.properties"));
```
