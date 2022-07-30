### 表达式的特殊形式

除了上述常见的表达式之外，还存在情况比较特殊的表达式，如 `define`、`cond` 和 `if` 等，这些表达式并不是按照统一的表达式规则运算，而是各有规则。

#### define

`define` 有主要有两种使用场景，绑定参数和定义程式，例如：

`(define size 3)`

是将 3 与 名为 size 变量或对象绑定，在同一环境中使用 size 时输出的结果就是 3，而定义程式的情况如下：

`(define (<name> <formal parameters>) <body>)` 

```scheme
(define (square x)
  (* x x))
```

通过 `define` 可以将一个名字与一个基本元素或一段表达式关联，这也是 Lisp 这门编程语言抽象能力的体现。

#### 条件表达式

`cond` 表达式的结构如下：

```scheme
(cond (<p1> <e1>)
	  (<p2> <e2>)
	  (<p3> <e3>))

(define (abs x)
  (cond ((> x 0) x)
        ((= x 0) 0)
        ((< x 0) (- x))))
```

p 表示逻辑判断的表达式，结果为 true 时会执行对应的 e，也就是结果表达式，并将计算结果返回，如果 p 的结果为 false，则按此规则执行下一条用例。如果用例只有两条时也可如下编写：

```scheme
(cond (<p1> <e1>)
	  (else <e2>))

(define (abs x)
  (cond ((< x 0) (- x))
        (else x)))
```

虽然 `cond` 不是表达式而是特殊形式，但 `else` 是表达式，因为 `else` 会应用所有操作数。上述结构也可以用 `if` 特殊形式改写：

```scheme
(if <predicate> <consequent> <alternative>)

(define (abs x)
  (if (< x 0)
      (- x)
      x))
```

除此之外还可以使用 `and` 、`or` 和 `not` 这些复合条件表达式，如下：

```scheme
(and <e1> <e2> ... <en>)
(or <e1> <e2> ... <en>)
(not <e>)
```

这几种条件表达式除了 `not` 外都是特殊形式，`and` 和 `or` 都符合开关原则，不过 `and` 所有表达式结果都为 true 时最终返回最后一个表达式的运算结果，而 `or` 在所有表达式都为 false 时最终只返回 false。