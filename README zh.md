# num-traits

[![crate](https://img.shields.io/crates/v/num-traits.svg)](https://crates.io/crates/num-traits)
[![documentation](https://docs.rs/num-traits/badge.svg)](https://docs.rs/num-traits)
[![minimum rustc 1.8](https://img.shields.io/badge/rustc-1.8+-red.svg)](https://rust-lang.github.io/rfcs/2495-min-rust-version.html)
[![build status](https://github.com/rust-num/num-traits/workflows/master/badge.svg)](https://github.com/rust-num/num-traits/actions)

## 引入背景
Num-traits在rust中提供了数字计算等数学方法的三方库，包括Rust中通用数学的数字特性。

## 使用指导
### 使用Openharmony编译框架
在你的"BUILD.gn"中使用deps字段添加对num-traits crate的依赖，例如：

```BUILD.gn
ohos_rust_shared_library("foo") {
  source = [ "src/lib.rs" ]
  deps = [ "//third_party/rust/crates/num-traits:lib" ]
}
```

### 使用Cargo
在你的 "Cargo.toml "中添加：

``toml
[dependencies]
num-traits = "0.2"
```

## 特性

这个板块可以在没有标准库的情况下使用(`#![no_std]`)，通过禁用
默认的 "std "功能。在`Cargo.toml'中使用这个功能：

```toml
[dependencies.num-traits]
version = "0.2"
default-features = false
# features = ["libm"]    # <--- Uncomment if you wish to use `Float` and `Real` without `std`
```

`Float`和`Real`特性只有在启用`std`或`libm`时才可用。 
`libm`特性仅在Rust 1.31及以后版本中可用（[见PR #99](https://github.com/rust-num/num-traits/pull/99)）。

`FloatCore`特性始终可用。 用于`f32`的`MulAdd`和`MulAddAssign`也需要`f64`的`MulAddAssign`。
和`f64`也需要`std`或`libm`，就像`Pow`中的有符号和浮点指数的实现。
指数的实现也需要`pow'。

`i128`和`u128`的实现只在Rust 1.26及以后的版本中可用。
以后的版本。 构建脚本会自动检测到这一点，但你可以通过启用 "i128 "和 "u128 "来使它成为
但你可以通过启用`i128'板块功能使其成为强制性的。

## 发布

发行说明可在[RELEASES.md](RELEASES.md)中找到。

## 兼容性

`num-traits`板块已在rustc 1.8及以上版本中测试。

## 许可证

使用以下任何一种许可证

 * [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0)
 * [MIT许可证](http://opensource.org/licenses/MIT)

## 开发者贡献

在使用该工具的过程中有任何问题欢迎开发者在社区issue中反馈。

<br>
