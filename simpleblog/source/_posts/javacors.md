---
title: 前后端分离,跨域CorsFilter和CorsRegistry选择
date: 2020-04-14 10:58:20
tags:
- javaweb
- 跨域
- 框架
category:
- 代码和我
- java
---
{% asset_img code.jpg This is code %}
### 前言
在前后端分离项目中,配置javaweb框架,跨域是首要解决的问题之一.
### 跨域详解
一、同源策略
同源策略（Sameoriginpolicy）是一种约定，它是浏览器最核心也最基本的安全功能，如果缺少了同源策略，则浏览器的正常功能可能都会受到影响。可以说Web是构建在同源策略基础之上的，浏览器只是针对同源策略的一种实现。同源策略会阻止一个域的javascript脚本和另外一个域的内容进行交互。所谓同源（即指在同一个域）就是两个页面具有相同的协议（protocol），主机（host）和端口号（port）
二、如何产生跨域
当一个请求url的协议(http/https)、域名、端口三者之间任意一个与当前页面url不同即为跨域
三、非同源限制
1.无法读取非同源网页的 Cookie、LocalStorage 和 IndexedDB
2.无法接触非同源网页的 DOM
3.无法向非同源地址发送 AJAX 请求
### CorsRegistry解决
{% asset_img corsregistry.png This is code %}
### CorsFilter解决
{% asset_img corsfilter.png This is code %}
### CorsRegistry和CorsFilter区别
首先CorsRegistry拦截器,再我们自定义的拦截器之后
而用户请求,先经过CorsFilter,到达servlet,再经过拦截器处理