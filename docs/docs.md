
# Hello World
```Go
fn main() {
    prtn('hello world')
}
```

# Functions
```go
fn main() {
    prtn(sub(11, 33))
    prtn(add(100, 10)) // type deduction, 110
    prtn(add("1", "2")) // "12"
}

fn sub(x int, y int) <int, int> {
    ret x - y, x + y
}

fn add(x, y T) T { // generics
    ret x + y
}

fn errHand(x i32, y str) i32? {
    ret x + i32<y>?
}
```
