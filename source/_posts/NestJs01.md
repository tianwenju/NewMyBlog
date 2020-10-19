---
title: Nestjs-01
tags: [web-server]
categories: [NestJs]
date: 2020-04-09 10:30:15
top: 1
photos: [https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=1020128022,1175558782&fm=26&gp=0.jpg]
---
# NestJS-01
![Nest](https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=1020128022,1175558782&fm=26&gp=0.jpg)
## NestJS 介绍
* Nest 是一个渐进的 Node.js 框架，可以在 TypeScript 和 JavaScript (ES6、ES7、ES8)之上构 建高效、可伸缩的企业级服务器端应用程序。
* Nest 基于 TypeScript 编写并且结合了 OOP（面向对象编程），FP（函数式编程）和 FRP （函数式响应编程）的相关理念。在设计上的很多灵感来自于 Angular，Angular 的很多模 式又来自于 Java 中的 Spring 框架，依赖注入、面向切面编程等，所以我们也可以认为： Nest 是 Node.js 版的 Spring 框架。

* Nest 框架底层 HTTP 平台默认是基于 Express 实现的，所以无需担心第三方库的缺失。*Nest 旨在成为一个与平台无关的框架.*通过平台，可以创建可重用的逻辑部件，开发人员
可以利用这些部件来跨越多种不同类型的应用程序。 从技术上讲，Nest 可以在创建适配器 后使用任何 Node HTTP 框架。 有两个支持开箱即用的 HTTP 平台：express 和 fastify。 您 可以选择最适合您需求的产品。

* NestJS 的核心思想：*就是提供了一个层与层直接的耦合度极小,抽象化极高的一个架构体系*
## NestJS和Egg.js的简单对比
1. Egg.js 是和 Nest.js 都是为企业级框架和应用而生。 
2. Egg.js 和 Nest.js 都是非常优秀的 Nodejs 框架。Egg.js 基于 Koa，Nest.js 默认基于 Express，nest 也可以基于其他框架 
3. Egg.js 文档相比 NestJS 优秀很多 
4. Express、Koa 是 Node.js 社区广泛使用的框架，简单且扩展性强，非常适合做个 人项目。但框架本身缺少约定，标准的 MVC 模型会有各种千奇百怪的写法。Egg 和 NestJS 都是按照约定进行开发的。但是 Egg 相比 NestJS 约定更标准。 
5. 面向对象方面 NestJS 优于 Egg.js，NestJS 基于 TypeScript，如果你会 angular 或者 java 学习 NestJS 非常容易。
   
### Egg.js 的特性： 
* 提供基于 Egg 定制上层框架的能力
* 高度可扩展的插件机制 
* 内置多进程管理 
* 基于 Koa 开发，性能优异 
* 框架稳定，测试覆盖率高 
* 渐进式开发
### 必备基础
* Nodejs
* Typescript
* Express
### NestJS 的特性： 
* 依赖注入容器 
* 模块化封装 
* 可测试性 
* 内置支持 TypeScript 
* 可基于 Express 或者 fastify
### NestJS环境搭建及运行

***
* 官网：https://nestjs.com/ 
* 中文网站：https://docs.nestjs.cn/ 
* GitHub: https://github.com/nestjs/nest
