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
```java