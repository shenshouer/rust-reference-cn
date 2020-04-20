# 注释(Comments)

> **<sup>Lexer</sup>**\
> LINE_COMMENT :\
> &nbsp;&nbsp; &nbsp;&nbsp; `//` (~[`/` `!`] | `//`) ~`\n`<sup>\*</sup>\
> &nbsp;&nbsp; | `//`
>
> BLOCK_COMMENT :\
> &nbsp;&nbsp; &nbsp;&nbsp; `/*` (~[`*` `!`] | `**` | _BlockCommentOrDoc_)
>      (_BlockCommentOrDoc_ | ~`*/`)<sup>\*</sup> `*/`\
> &nbsp;&nbsp; | `/**/`\
> &nbsp;&nbsp; | `/***/`
>
> INNER_LINE_DOC :\
> &nbsp;&nbsp; `//!` ~[`\n` _IsolatedCR_]<sup>\*</sup>
>
> INNER_BLOCK_DOC :\
> &nbsp;&nbsp; `/*!` ( _BlockCommentOrDoc_ | ~[`*/` _IsolatedCR_] )<sup>\*</sup> `*/`
>
> OUTER_LINE_DOC :\
> &nbsp;&nbsp; `///` (~`/` ~[`\n` _IsolatedCR_]<sup>\*</sup>)<sup>?</sup>
>
> OUTER_BLOCK_DOC :\
> &nbsp;&nbsp; `/**` (~`*` | _BlockCommentOrDoc_ )
>              (_BlockCommentOrDoc_ | ~[`*/` _IsolatedCR_])<sup>\*</sup> `*/`
>
> _BlockCommentOrDoc_ :\
> &nbsp;&nbsp; &nbsp;&nbsp; BLOCK_COMMENT\
> &nbsp;&nbsp; | OUTER_BLOCK_DOC\
> &nbsp;&nbsp; | INNER_BLOCK_DOC
>
> _IsolatedCR_ :\
> &nbsp;&nbsp; _A `\r` not followed by a `\n`_

## 非文档注释(Non-doc comments)

Rust中注释与C++类似，行注释(`//`)与块注释(`/* ... */`)。支持嵌套块注释

非文档注释被解释为空白形式。

## 文档注释(Doc comments)

行文档注释以三个斜杠开头(`///`),块文档注释(`/** ... */`), 两个内部文档注释都被解释为文档属性([`doc` attributes])的特殊语法。 也就是说，它们等同于在注释的主体周围写`#[doc="..."]` ，如, `/// Foo` 变成`#[doc="Foo"]` 和 `/** Bar */` 变成 `#[doc="Bar"]`。

行文档注释以`//!`开始，块文档是`/*! ... */`都是适用于注释父项的doc注释，而不是其后的项目。也就是说，这等同于在注释主题周五写`#![doc="..."]` 。`//!`注释通常用于记录占用源文件的模块。

在文档注释中不允许使用单独的CR(`\r`)，即后跟LF(`\n`)。

## 示例

```rust
//! 适用于此库的隐式匿名模块的文档注释

pub mod outer_module {

    //!  - 内部单行注释
    //!! - 仍然是内部行文档注释(但带有特别提示的开头)(but with a bang at the beginning)

    /*!  - 内块文档 */
    /*!! - 仍然是内部块文档注释(但带有特别提示的开头)(but with a bang at the beginning) */

    //   - 仅仅是注释
    ///  - 外部行文档注释，需要三个斜杠
    //// - 仅仅是注释

    /*   - 仅仅是注释 */
    /**  - 外部块文档注释，需要两个星号 */
    /*** - 仅仅是注释 */

    pub mod inner_module {}

    pub mod nested_comments {
        /* 在Rust /* 我们可以 /* 嵌套注释 */ */ */

        // 所有的这三种块注释都可以包含其他的:

        /*   /* */  /** */  /*! */  */
        /*!  /* */  /** */  /*! */  */
        /**  /* */  /** */  /*! */  */
        pub mod dummy_item {}
    }

    pub mod degenerate_cases {
        // 空的内部行注释
        //!

        // 空的内部块文档
        /*!*/

        // 空的行注释
        //

        // 空的外部行文档
        ///

        // 空的块注释
        /**/

        pub mod dummy_item {}

        // 空的两星块不是文档块，是块注释
        /***/

    }

    /* 下一个是不允许的，因为外部文档注释需要一个可以用来接受文档的 */

    /// 接受项在哪里呢?
#   mod boo {}
}
```

[`doc` attributes]: ../rustdoc/the-doc-attribute.html
