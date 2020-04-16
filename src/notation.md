# 符号(Notation)

## 语法

以下符号被*Lexer(词法分析器)*与*Syntax*语法片段使用:

| 符号          | 实例                      | 含义                                   |
|-------------------|-------------------------------|-------------------------------------------|
| CAPITAL           | KW_IF, INTEGER_LITERAL        | 词法分析器生成的令牌             |
| _ItalicCamelCase_ | _LetStatement_, _Item_        | 句法产物                  |
| `string`          | `x`, `while`, `*`             | 确切的字符                    |
| \\x               | \\n, \\r, \\t, \\0            | 此转义所表示的字符  |
| x<sup>?</sup>     | `pub`<sup>?</sup>             | 可选项目                          |
| x<sup>\*</sup>    | _OuterAttribute_<sup>\*</sup> | 0 或多于x                           |
| x<sup>+</sup>     |  _MacroMatch_<sup>+</sup>     | 1 或多于x                            |
| x<sup>a..b</sup>  | HEX_DIGIT<sup>1..6</sup>      | x 代表a到b                   |
| \|                | `u8` \| `u16`, Block \| Item  | 一个或另一个                     |
| [ ]               | [`b` `B`]                     | 在列表中的任何字符              |
| [ - ]             | [`a`-`z`]                     | 在范围内的任何字符        |
| ~[ ]              | ~[`b` `B`]                    | 除了列出的任何字符       |
| ~`string`         | ~`\n`, ~`*/`                  | 除了这个序列外的任何字符      |
| ( )               | (`,` _Parameter_)<sup>?</sup> | 分组项                              |

## 字符串表生成

语法中的一些规则 &mdash; 尤其是一元运算符([unary operators]) ，二进制运算符([binary
operators])和关键字([keywords]) &mdash; 以简化形式给出：作为可打印字符串的列表。这些情况构成了有关令牌[token][tokens]规则的规则的子集，并被假定为词法分析阶段的结果，该阶段向解析器提供了由<abbr title="Deterministic Finite
Automaton">DFA</abbr>驱动的解析器，该解析器对所有此类字符串表项进行了分离。

当这种等宽(`monospace`)字体的字符串出现在语法内部时，它是对这种字符串表产生的单个成员的隐式引用。有关更多信息，请参见令牌[tokens]。

[binary operators]: expressions/operator-expr.md#arithmetic-and-logical-binary-operators
[keywords]: keywords.md
[tokens]: tokens.md
[unary operators]: expressions/operator-expr.md#borrow-operators
