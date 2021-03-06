#

```block
类型转换
String()
Number()
Boolean() 返回原始类型

new String() 返回对象
```

```block
Object

对象属性排序
整数属性会被进行排序，其他属性则按照创建的顺序显示

拷贝
Object.assign(dest, [src1, src2, src3...])
```

```block
?.
?.()
?.[]
```

```block
Symbol("id")
Symbol.for("id")
Symbol.keyFor(sym)
```

```block
对象到原始值的转换，是由许多期望以原始值作为值的内建函数和运算符自动调用的。

这里有三种类型（hint）：

"string"（对于 alert 和其他需要字符串的操作）
"number"（对于数学运算）
"default"（少数运算符，通常对象以和 "number" 相同的方式实现 "default" 转换）
规范明确描述了哪个运算符使用哪个 hint。

转换算法是：

调用 obj[Symbol.toPrimitive](hint) 如果这个方法存在，
否则，如果 hint 是 "string"
尝试调用 obj.toString() 或 obj.valueOf()，无论哪个存在。
否则，如果 hint 是 "number" 或者 "default"
尝试调用 obj.valueOf() 或 obj.toString()，无论哪个存在。
所有这些方法都必须返回一个原始值才能工作（如果已定义）。

在实际使用中，通常只实现 obj.toString() 作为字符串转换的“全能”方法就足够了，该方法应该返回对象的“人类可读”表示，用于日志记录或调试。
```
