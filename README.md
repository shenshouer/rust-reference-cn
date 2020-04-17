# Rust语言参考

本文档是Rust编程语言的主要参考资料。

本文件不规范。它可能包括`rustc`本身的具体细节，不应被视为Rust语言的规范。我们打算某一天制作这样一份文件，这是我们现在做这个的原因。

- [稳定版英文原版](https://doc.rust-lang.org/stable/reference/)
- [非稳定版英文原版](https://doc.rust-lang.org/nightly/reference/)

## 依赖(Dependencies)

- rustc (Rust语言的编译器).
- mdbook (使用命令 `cargo install mdbook` 进行安装).

## 构建步骤

首先，进入到仓库(repository)目录并通过测试代码 片段来捕获编译错误:

```bash
cd reference
mdbook test
```

然后生成书本:

```bash
mdbook build
```

生成的HTML文件将会放置在`docs` 目录。
