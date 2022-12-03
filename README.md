# Rust项目初始化模板

## 如何使用该项目模板
1. clone该项目到本地

2. 本地新建项目demo文件夹
 mkdir demo
 cd demo

3. 新建项目文件
 touch Cargo.toml
 touch README.md

4. 从模板项目copy文件
 cp -r ../rust-project-template/deny.toml .
 cp -r ../rust-project-template/.github .
 cp -r ../rust-project-template/.pre-commit-config.yaml .
 cp -r ../rust-project-template/.pre-commit-config.yaml .
 cp -r ../rust-project-template/_typos.toml .

 5. 初始化项目，版本控制
 git init

 6. 设置git提交用户信息，多账户隔离
 cd ./.git
 git config user.name "your name"
 git config user.email "your email address"

 7. 项目根目录执行命令安装pre-commit
 cd ..
》pre-commit install
pre-commit installed at .git/hooks/pre-commit

8. 提交代码
》git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        .github/
        .pre-commit-config.yaml
        Cargo.toml
        README.md
        _typos.toml
        deny.toml

nothing added to commit but untracked files present (use "git add" to track)

9. 构建项目目录
cargo new abi --lib
所有protocol buffer和gRPC自动生成的代码都放到一个crate中，然后为其中的代码生成trait，然后再在别的项目中使用

cargo new my-project-name --lib

新建可执行的项目
cargo new my-project-service

10. 修改my-project-name项目文件中Cargo.toml中name，方便提交到crate.io,避免冲突

11. 配置workspace
demo目录下Cargo.toml，添加
[workspace]
members = [
    "abi",
    "my-project-name",
    "my-project-service",
]

12. 构建项目
cargo build

Compiling my-project-service v0.1.0 (/Users/uh/Documents/sourcecode/github/rust-project-template/my-project-service)
Compiling my-project-name v0.1.0 (/Users/uh/Documents/sourcecode/github/rust-project-template/my-project-name)
Compiling abi v0.1.0 (/Users/uh/Documents/sourcecode/github/rust-project-template/abi)
Finished dev [unoptimized + debuginfo] target(s) in 1.54s
