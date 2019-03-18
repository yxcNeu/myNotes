# apply和with的区别
两者是Kotlin标准库中的函数，是带接收者的lambda：在lambda函数体内可以调用一个不用对象的方法，而且无须借助任何额外的限定符  
可以查看下面的例子

```Kotlin
fun alphabet(): String {
    val result = StringBuilder()
    for (letter in 'A'..'Z') {
        result.append(letter)
    }
    result.append("\nNow I know the alphabet!")
    return result.toString()
}
```

使用with重构

```Kotlin
fun alphabetWit() = with(StringBuilder()) {
    for (letter in 'A'..'Z') {
        append(letter)
    }
    append("\nNow I know the alphabet!")
    toString()
}
```

使用apply重构

```Kotlin
fun alphabetApply() = StringBuilder().apply {
    for (letter in 'A'..'Z') {
        append(letter)
    }
    append("\nNow I know the alphabet!")
}.toString()
```

## 两者的区别

两者几乎一模一样，唯一的区别就是apply始终返回作为实参传递给它的对象（即接受者对象）