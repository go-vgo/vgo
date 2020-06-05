
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

# Variables
```go
let i i32
mut v f64

s := 'string'
age := 20
num := i64<9999999999>
v = 9.99

prtn(s)
prtn(age)
prtn(num, v)
```

# Primitive types
```go
bool

str   // string

i8    i16  int  i64      i128  bint
byte  u16  u32  u64      u128

rune 

f32 f64

any // similar Go's interface{}
...
```

# Imports
```go
imp (
    os
    log
)

fn main() {
    s := os.Getenv("GOPATH")
    log.Prtn('Hello, $s!')
    prtn<"Hello, $s">
}
```

# Generics
```go
typ tp = i32?i64?int

typ wrap stru {
    s T
    cmp fn(T, T) bool
}

fn (s wrap) Len() int { 
    ret len(s.s) 
}
fn (s wrap) Less(i, j int) bool { 
    ret s.cmp(s.s[i], s.s[j]) 
}
fn (s wrap) Swap(i, j int) { 
    s.s[i], s.s[j] = s.s[j], s.s[i] 
}

fn Sort(s T, cmp fn(T, T) bool) {
    sort.Sort(wrap{s, cmp})
}

typ Repo stru {
    Test T
}

fn new(s, s1 T) T? {
    if s1#str {
        ret s + i32<s1>?
    }

    ret s + s1
}

fn main() {
    i := new(1, "1")? {
        prtn<err>
    }

    prtn(i)
}

```

# Option types and error handling
```go
fn sub(i i32, s str) i32? {
    ret i + i32<s>?
}

fn main() {
    i := sub(1, "3")? {
        prtn(err) // nil
    }

    prtn(i)
}
```

# back-end (The second step, add the independent back-end compiler.)

## Memory management

The compiler cleans everything up during compilation.  