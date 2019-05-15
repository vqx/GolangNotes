#go 组合   
这个官方文档的说明资料很少    
```
//一般字段
type TypeB struct{
 A typeA
}
//组合
type TypeB struct{
 typeA
}
```
会把两个对象当成一个对象来使用   
有点像继承，但是不完全是  

#go 指令 
e.g.:  golang版本 1.11.6   
time.Sleep的实现   
time/sleep.go:9 //这个只是声明    
真正实现代码位置  
runtime/time.go:84  
```
//go:linkname timeSleep time.Sleep
func timeSleep(ns int64) {
``` 
还有一些其他的指令   
可以参考这篇[帖子](https://segmentfault.com/a/1190000018719140)  
但是你自己写time/sleep.go:9这种声明又会报错  
所以按道理还有其他规则   
比如配置  
或者build命令  

#go 一个不好的写法  
一个type的类型为另外一个type   
会把原来的type的方法&字段全部丢弃掉   
e.g.:   
```
type TypeA struct{}
func(a TypeA)Fun1(){
    fmt.Println("a fun1")
}

type NewTypeA TypeA

func main(){
    a := NewTypeA{}
    a.Fun1()//这个会报错
}
```
