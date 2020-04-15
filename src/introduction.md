# 介绍

这本书是Rust编程语言的主要参考资料。它提供三方面的资料:

  - 章节非正式地描述每种语言结构及其使用.
  - 章节非正式地描述了内存模型，并发模型，运行时服务，链接模型(linkage model)，与调试设施。
  - 附录章节提供了语言的基本原理和影响了设计的参考。
    

<div class="warning">
警告：本书还未完成。编写需要一段时间。查看[GitHub issues]获悉什么为编写到本书。

</div>

## 语言参考不是什么

本书不是为介绍语言而服务的，不是语言的入门书。 背景假设读者熟悉了语言。.另外还有一本书可以帮助你熟悉这些背景知识。

本书同样不是为包含在语言发版中的标准库参考而服务的。标准库文档是通过源码中文档注释而单独记录的。 人们可能期望成为语言特性的许多特性是库Rust库的特征，所以你要找的可能是那里，而不是这里。

同样，本书不是`rustc`工具或Cargo。 `rustc` 有自己的[书][rustc book]介绍. Cargo有一本
包含[参考][cargo reference]的[书][cargo book]。 有几个像[链接(linkage)]这样的页面在描述rustc的工作原理。

本书仅作为Rust稳定版的语言参考。有关正在处理的非稳定特性，请参阅[非稳定的书(Unstable Book)]。

最后，本书并不规范。它可能包括`rustc`本身的具体细节，不应被视为Rust语言的规范。我们打算某一天制作这样一份文件，这是我们现在做这个的原因。

## 怎样使用本书

这本书并不假定你是按顺序读。每个章节通常可以单独阅读，但会交叉链接到其他与之关联的章节，这不再讨论。

有两个主要方法来阅读这个文档。

首先回答一个明确的问题。如果你知道哪个章节有这个问题的答案，你可以直接跳到这个章节阅读相关内容。否则，您可以按s或单击顶部栏上的放大镜来搜索与您的问题相关的关键字。例如，假设你想知道何时将删除在let语句中创建的临时值。 如果您还不知道【表达式章节(expressions chapter)】中定义了【临时对象的生存期(lifetime of temporaries)】，您可以搜索“temporary let”，第一个搜索结果将带您进入该部分。

第二是提高你对语言某一方面的知识。在这种情况下，只需浏览目录，直到看到想了解更多，就开始阅读吧。如果一个链接看起来很有趣，单击它，然后阅读该部分。

也就是说，读本书没有错误的方法。用你感觉最好的方式来阅读本书。

### 约定(Conventions)

与所有技术书籍一样，本书在显示信息上有一些约定。这里记录了这些约定。

* 定义术语的语句以斜体包含该术语。 每当那个该术语在该章之外使用，通常是指向该部分的链接有这个定义。
  
* 编译“crate”时所用语言的不同之处在于在一个以**粗体字**"版本差异"(**Edition Differences**:)开头的引文中。
  
> **版本差异**: 在2015年版中，此语法有效，自2018年版起不允许使用
  
* 注意：包含有关书籍状态的有用信息或指出有用，但大多超出了范围的信息以方块字开头用粗体写着“注意：”一词。
  
  > **注意**: 这是一个示例注意。

* 警告用语言表现出不健康的行为或可能使人困惑语言特性的交互在一个特殊的警告框中。
  
<div class="warning">
  
警告: 这是一个示例警告。
  
</div>
  
* 在文本中的代码片段都在`<code>`标签中。长代码示例在语法高亮的块中，可以通过右上角控制进行复制、执行，并且显示隐藏行。

  Longer code examples are in a syntax highlighted box that has controls for
  copying, executing, and showing hidden lines in the top right corner.

  ```rust
  # // 这是一个隐藏行.
  fn main() {
      println!("This is a code example");
  }
  ```

* 语法和词法结构用带“Lexer”或“Syntax”在（粗体上标） <sup>**bold superscript**</sup> 中作为第一行。
  
> **<sup>Syntax</sup>**\
  > _ExampleGrammar_:\
  > &nbsp;&nbsp; &nbsp;&nbsp; `~` [_Expression_]\
  > &nbsp;&nbsp; | `box` [_Expression_]
  
详见【符号(Notation)】

## 捐献

我们欢迎各式各样的贡献。

你可以通过打开issue或发送PR到 [Rust语言参考仓库]。如果本书没有你问题的答案，并且你想在这书本范围内添加答案， 请毫不犹豫地提交issue或在上的`#docs`频道中询问[Discord]。了解人们对这本书的使用情况有助于指导我们注意让这些部分尽可能的完美。

[book]: ../book/index.html
[github issues]: https://github.com/rust-lang/reference/issues
[标准库]: ../std/index.html
[Rust语言参考仓库]: https://github.com/rust-lang/reference/
[非稳定版本书籍Unstable Book]: https://doc.rust-lang.org/nightly/unstable-book/
[_表达式_]: expressions.md
[cargo 书籍]: ../cargo/index.html
[cargo 参考]: ../cargo/reference/index.html
[表达式章节]: expressions.md
[临时对象的生存期(lifetime of temporaries)]: expressions.md#temporary-lifetimes
[链接设施(linkage)]: linkage.md
[rustc 书籍]: ../rustc/index.html
[符号(Notation)]: notation.md
[Discord]: https://discord.gg/rust-lang
