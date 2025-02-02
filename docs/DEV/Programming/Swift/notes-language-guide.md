---
title: Swift笔记 ｜ Language Guide
---

# Swift笔记 ｜ Language Guide

> 阅读 `The Swift Programming Language (5.6)` 的笔记

## A Swift Tour

### 小知识点

- 显式类型转换: Swift不支持隐式类型转换 有表达式的话 手动转一下 比如 `Double(x)`
- 空字典 `[:]`
- `if` `while` 这些后面写Bool表达式不用加括号
- `repeat { ... } while ...`
- 枚举可以用数字索引 如 `response.1`
- 函数可以是变量
- 枚举可以有函数 这样就不用纠结枚举的类型了
- 枚举可以每个case都用一个类型

### 函数编程

```swift
case let x where x.hasSuffix("pepper"):
    print("Is it a spicy \(x)?")
```

### nested functions

```swift
func returnFifteen() -> Int {
    var y = 10
    func add() {
        y += 5
    }
    add()
    return y
}
returnFifteen()
```

### map函数

完整

```swift
numbers.map({ (number: Int) -> Int in
    let result = 3 * number
    return result
})
```

简化

```swift
numbers.map({ number in 3 * number })
```

```swift
numbers.map({ 3 * $0 })
```

### 枚举类型

```swift
enum Response<DataType> {
    case succeed(data: DataType, message: String)
    case failure(error: String)
}
```

### Optional实现

```swift
enum OptionalValue<Wrapped> {
    case none
    case some(Wrapped)
}
```

---

> Language Guide

## The Basics 44

Swift is a *type-safe* language, which means the language helps you to be clear about the types of values your code can work with.


```swift
var x = 0.0, y = 0.0, z = 0.0
```

```swift
let minValue = UInt8.min
let maxValue = UInt8.max
```

`Int`在32bit和64bit的操作系统上分别为`Int32`和`Int64`

推荐日常使用`Int`、`Double`

二进制：`0b`
八进制：`0o`
十六进制：`0x`

`1.25e2` `0xFp-2` p表示十六进制的指数

`_`可以作为数字的分隔符

`typealias AudioSample = UInt16`

`let a = (code: 200, description: "OK")`

`assert()` `precondition()` 早期开发可以用`fatalErros("Unimplemented")`

## Basic Operators 104

主动溢出`a &+ b`

`-9 % 4 = 1`

可以使用`+=`

元组的比较按照元组的先后顺序来挨个比较

可以使用` ? : `表达式

`a != nil ? a! : b` -> `a ?? b`

`...` `..<` `[2...]` `[...2]`

## Strings and Characters 132



## Collection Types 177



## Control Flow 215



## Functions



## Closures



## Enumerations

```swift
enum Planet {
    case mercury, venus, earth, mars, jupiter, saturn, uranus, neptune
}

print(Planet.allCases)
```

```swift
enum Barcode {
    case upc(Int, Int, Int, Int)
    case qrCode(String)
}
```

recursive enumerations: `indirect enum` 示例：算术表达式计算
```swift
indirect enum ArithmeticExpression {
    case number(Int)
    case addition(ArithmeticExpression, ArithmeticExpression)
    case multiplication(ArithmeticExpression, ArithmeticExpression)
}
```

## Structures and Classes

其中的东西叫properties和methods

由于structure和class在Swift里面差不多，实例化得到的对象object被称作instance

class有而structure没有：继承、casting类型转换、析构、引用instance

“As a general guideline, prefer structures because they’re easier to reason about, and use classes when they’re appropriate or necessary. In practice, this means most of the custom data types you define will be structures and enumerations. For a more detailed comparison, see [Choosing Between Structures and Classes](https://developer.apple.com/documentation/swift/choosing_between_structures_and_classes).”
Consider the following recommendations to help choose which option makes sense when adding a new data type to your app.
* Use structures by default.
* Use classes when you need Objective-C interoperability.
* Use classes when you need to control the identity of the data you're modeling.
* Use structures along with protocols to adopt behavior by sharing implementations.
由于类的实例可以引用，所以如果要在App中的多个地方修改一个东西，那么这个东西就可以用类来描述

“All structures and enumerations are value types in Swift. This means that any structure and enumeration instances you create—and any value types they have as properties—are always copied when they’re passed around in your code.” 注意数组字符串字典这些都是拷贝
class为reference type

Swift一般不用指针，除非你想手动管理内存

## Properties



## Methods



## Subscripts



## Inheritance - Class



## Initialization



## Deinitialization - Class



## Optional Chaining



## Error Handling



## Concurrency



## Type Casting - Class



## Nested Types



## Extensions



## Protocols



## Generics



## Opaque Types


## Automatic Reference Counting - Class


## Memory Safety


## Access Control


## Advanced Operators