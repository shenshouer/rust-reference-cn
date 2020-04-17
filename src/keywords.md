# 关键字(Keywords)

Rust将关键字分为3类:

* [强关键字(strict)](#strict-keywords)
* [保留关键字(reserved)](#reserved-keywords)
* [弱关键字(weak)](#weak-keywords)

## 强关键字(Strict keywords)

这些关键字仅用于他们正确的上下文中。不能用作以下项的名称:

* [Items]
* [Variables] 与函数参数
* 字段与 [variants] 
* [Type parameters] 类型参数
* 生命周期参数或 [loop labels]
* [Macros] 或 [attributes]
* [Macro placeholders]
* [Crates]

> **<sup>Lexer:<sup>**\
> KW_AS             : `as`\
> KW_BREAK          : `break`\
> KW_CONST          : `const`\
> KW_CONTINUE       : `continue`\
> KW_CRATE          : `crate`\
> KW_ELSE           : `else`\
> KW_ENUM           : `enum`\
> KW_EXTERN         : `extern`\
> KW_FALSE          : `false`\
> KW_FN             : `fn`\
> KW_FOR            : `for`\
> KW_IF             : `if`\
> KW_IMPL           : `impl`\
> KW_IN             : `in`\
> KW_LET            : `let`\
> KW_LOOP           : `loop`\
> KW_MATCH          : `match`\
> KW_MOD            : `mod`\
> KW_MOVE           : `move`\
> KW_MUT            : `mut`\
> KW_PUB            : `pub`\
> KW_REF            : `ref`\
> KW_RETURN         : `return`\
> KW_SELFVALUE      : `self`\
> KW_SELFTYPE       : `Self`\
> KW_STATIC         : `static`\
> KW_STRUCT         : `struct`\
> KW_SUPER          : `super`\
> KW_TRAIT          : `trait`\
> KW_TRUE           : `true`\
> KW_TYPE           : `type`\
> KW_UNSAFE         : `unsafe`\
> KW_USE            : `use`\
> KW_WHERE          : `where`\
> KW_WHILE          : `while`

以下关键字在2018版本中被添加。

> **<sup>Lexer 2018+</sup>**\
> KW_ASYNC          : `async`\
> KW_AWAIT          : `await`\
> KW_DYN            : `dyn`

## 保留关键字(Reserved keywords)

这些关键字当前暂未被使用，但保留为将来使用。这些关键字与强关键字限制一样。其背后的原因是，禁止当前程序使用这些关键字，从而使当前Rust程序与未来版本的保持向前兼容。

> **<sup>Lexer</sup>**\
> KW_ABSTRACT       : `abstract`\
> KW_BECOME         : `become`\
> KW_BOX            : `box`\
> KW_DO             : `do`\
> KW_FINAL          : `final`\
> KW_MACRO          : `macro`\
> KW_OVERRIDE       : `override`\
> KW_PRIV           : `priv`\
> KW_TYPEOF         : `typeof`\
> KW_UNSIZED        : `unsized`\
> KW_VIRTUAL        : `virtual`\
> KW_YIELD          : `yield`

以下关键字在2018版本中被设置为保留。

> **<sup>Lexer 2018+</sup>**\
> KW_TRY   : `try`

## 弱关键字（Weak keywords）

这些关键在仅在包含的上下文内具有特殊的含义。例如，有可能使用`union`作为名称来声明变量或方法。

* `union` 被用来声明一个 [union] 并且当在一个union声明时才是一个关键字。
* `'static` 是用来声明静态声明周期的，并且不能当做一般声明周期参数使用

  ```编译失败
  // error[E0262]: invalid lifetime parameter name: `'static`
  fn invalid_lifetime_parameter<'static>(s: &'static str) -> &'static str { s }
  ```
* 在2015版本中， [`dyn`] 是在类型路径中不以`::`开头位置中使用的关键字。

  从2018版本开始，`dyn` 已经被提示为强关键字。

> **<sup>Lexer</sup>**\
> KW_UNION          : `union`\
> KW_STATICLIFETIME : `'static`
>
> **<sup>Lexer 2015</sup>**\
> KW_DYN            : `dyn`

[items]: items.md
[Variables]: variables.md
[Type parameters]: types/parameters.md
[loop labels]: expressions/loop-expr.md#loop-labels
[Macros]: macros.md
[attributes]: attributes.md
[Macro placeholders]: macros-by-example.md
[Crates]: crates-and-source-files.md
[union]: items/unions.md
[variants]: items/enumerations.md
[`dyn`]: types/trait-object.md
