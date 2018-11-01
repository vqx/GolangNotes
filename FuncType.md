# init func type 

```
type Func fun(int)int
func main(){
    f := Func(Demo)
    fmt.Print(f(10))
}
fun Demo(n int) int{
    return n+n
}
```
