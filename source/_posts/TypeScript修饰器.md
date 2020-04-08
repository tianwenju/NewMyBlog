---
title: TypeScript修饰器
tags: [修饰器]
categories: [Typescript]
date: 2020-04-08 13:32:24
---
## 类装饰器
>* 无参数
>    * 类装饰器表达式在运行时作为函数被调用时候,类的构造函数作为其唯一的参数
>    * 如果类的装饰器返回一个值，它会使用提供的构造函数来替换类的声明
```
     function logClasss(target:any){
            console.log(target);  // 构造函数
            return class extends target{
                apiUrl:any='我是修改后的数据';
                getData(){
                    this.apiUrl=this.apiUrl+'----';
                    console.log(this.apiUrl);
                }
            }
        }
        
    @logClasss
    class HttpClient{
        
    }
```
>* 有参数
>   * 参数是 传入的参数
>   * 返回的参数 target 是类的构造函数
```
    function logClass(params:string){
            return function(target:any){
                console.log("xxx",params);  
                console.log("xxx",target);
                     
                
            }
        }
```
## 属性装饰器
> * params 传入的参数
> * target 对于静态成员来说是类的构造函数，对于实例成员是类的原型对象
> * attr 是对象属性

```
        function logProperty(params:any){
            return function(target:any,attr:any){
                console.log("000",params)
                console.log("000",target);
                console.log("000",attr);
                target[attr]=params;
            }
        }
        
      
        class HttpClient111{
            @logProperty('http://itying.com')
            public url:any |undefined;
         
            getData(){
                console.log(this.url);
            }
        }
```
## 方法装饰器
>  它会被应用到方法的 属性描述符上，可以用来监视，修改或者替换方法定义。
> 方法装饰会在运行时传入下列3个参数：
> * 对于静态成员来说是类的构造函数，对于实例成员是类的原型对象。
> * 成员的名字。
> * 成员的属性描述符（value就是方法）。
```
        function get(params:any){
            return function(target:any,methodName:any,desc:any){
                console.log(target);
                console.log(methodName);
                console.log(desc.value);  // value就是当前方法     
                
                //修改装饰器的方法  把装饰器方法里面传入的所有参数改为string类型

                //1、保存当前的方法

                var oMethod=desc.value;
                desc.value=function(...args:any[]){                
                    args=args.map((value)=>{
                        return String(value);
                    })
                    oMethod.apply(this,args);
                }

            }
        }
```
## 方法属性修饰器
>     参数装饰器表达式会在运行时当作函数被调用，可以使用参数装饰器为类的原型增加一些元素数据 ，传入下列3个参数：
>    * 对于静态成员来说是类的构造函数，对于实例成员是类的原型对象。
>    * 方法的名字。
>    * 参数在函数参数列表中的索引。
```
 function logParams(params:any){

     return function(target:any,methodName:any,paramsIndex:any){

         console.log(params);

         console.log(target);

         console.log(methodName);

         console.log(paramsIndex);


         target.apiUrl=params;

    } 
```
## 装饰器执行顺序

> 
> 属性》方法》方法参数》类
> 
> 如果有多个同样的装饰器，它会先执行后面的

