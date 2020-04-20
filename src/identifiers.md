# 标识符(Identifiers)

> **<sup>Lexer:<sup>**\
> IDENTIFIER_OR_KEYWORD :\
> &nbsp;&nbsp; &nbsp;&nbsp; [`a`-`z` `A`-`Z`]&nbsp;[`a`-`z` `A`-`Z` `0`-`9` `_`]<sup>\*</sup>\
> &nbsp;&nbsp; | `_` [`a`-`z` `A`-`Z` `0`-`9` `_`]<sup>+</sup>
>
> RAW_IDENTIFIER : `r#` IDENTIFIER_OR_KEYWORD <sub>*Except `crate`, `self`, `super`, `Self`*</sub>
>
> NON_KEYWORD_IDENTIFIER : IDENTIFIER_OR_KEYWORD <sub>*Except a [strict] or [reserved] keyword*</sub>
>
> IDENTIFIER :\
> NON_KEYWORD_IDENTIFIER | RAW_IDENTIFIER

标识符是以下格式的任何非空ASCII字符串:

要么

* 首字符是一个字母。
* 其余字符为字母数字或`_`.

或者

* 首字符是 `_`.
* 标识符超过一个字符。 `_`本身不是标识符。
* 其余字符为字母数字或`_`.

原始标识符类似于普通标识符，但以`r#`为前缀。 (请注意，`r#`前缀不包含在实际标识符中。)与普通标识符不同，原始标识符可以是任何严格或保留的关键字，但上面列出的`RAW_IDENTIFIER`除外。

[strict]: keywords.md#strict-keywords
[reserved]: keywords.md#reserved-keywords
