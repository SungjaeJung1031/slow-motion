---
author: "slow-motion"
date: 2022-02-22
linktitle: Rust Hello Cargo
title: Rust Hello Cargo
weight: 10

tags: [
    "Programming Language",
    "Rust",
]
categories: [
    "Programming Language",
    "Rust",
]
---
<!--more-->
{{< katex display >}}

**Cargo** plays a role as build system and package manager of Rust. The simplest Rust programs like [hello-world](rust-hello-world.md) do not have any depedencies on libraries and other files. However, the complex Rust programs has dependecies. In this case, Cargo helps Rustaceans to download, compile, distribute, and upload Rust packages for handling complicated dependencies. Cargo is a built-in pakage manager that comes with Rust installation. Below command will help you check the installation status and the Cargo version.

```
> cargo --version
```
{{< expand "Output">}}
cargo 1.58.0
{{< /expand >}}

## Create a Project using Cargo
On any operating system, a Project can be created with Cargo.
```
> cargo new [project name]
```

If you create a project, named hello-cargo, you could check below output and find that 'hello-cargo' directory is created.
```
> cargo new hello-cargo
```
{{< expand "Output">}}
Created binary (application) `hello-cargo` package
{{< /expand >}}

{{< mermaid class="text-center">}}
graph LR
    root[hello-cargo] --> 1[Cargo.toml]
    root --> 2[src]
    subgraph 2g[All project source files]
      2 --> 21[main.rs]
    end
    subgraph 1g[Cargo manifest file]
      1
    end

    click root "https://github.com/SungjaeJung1031/rust/tree/main/rust-hello-cargo/hello-cargo"
    click 1 "https://github.com/SungjaeJung1031/rust/blob/main/rust-hello-world/hello-world.rs"
    click 2 "https://github.com/SungjaeJung1031/rust/tree/main/rust-hello-cargo/hello-cargo/src"
    click 21 "https://github.com/SungjaeJung1031/rust/blob/main/rust-hello-cargo/hello-cargo/src/main.rs"
linkStyle 0 stroke-width:1px;

style 1g fill:transparent,stroke:#E5E5E5,stroke-width:1px,stroke-dasharray:5;
style 2g fill:transparent,stroke:#323232,stroke-width:1px,stroke-dasharray:5;

{{< /mermaid >}}

{{< hint info >}}
**Guide**  
Click the items in above diagram to check the code example
{{< /hint >}}

The **Cargo.[toml](https://toml.io/en/)** is the [manifest file](https://en.wikipedia.org/wiki/Manifest_file#:~:text=A%20manifest%20file%20in%20computing,constituent%20files%20of%20the%20program.) for Cargo. 

```go {linenos=table,hl_lines=[8,"15-17"],linenostart=0}
[package]
name = "hello-cargo"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```

Cargo.toml look similar to the above code. Carog.toml is comparised of section with square brackets and key value pair (e.g. name = "hello-cargo"). [package] section is configuration of a package, and [depedencies] section describes the list of a project's dependecies. Additional TOML documentation can be found on [TOML website](https://toml.io/en/)


Then, how we could build the project using Cargo? For that lets first enter code in main.rs since the file is empty for the first time.

```go {linenos=table,hl_lines=[8,"15-17"],linenostart=0}
fn main()
{
    println!("Hello, cargo!");
}
```

After saving main.rs, enter the following command in the project's root directory to build the Cargo project.

```
> cargo build
```
{{< expand "Output">}}
Compiling hello-cargo v0.1.0 (/Users/sungjaejung1031/dev/rust/rust-hello-cargo/hello-cargo)
Finished dev [unoptimized + debuginfo] target(s) in 0.46s
{{< /expand >}}

Then **Cargo.lock** file and **target** directory will be created in the root directory.

**TBC...**

{{< hint info >}}
**Source Code**

Source code in this post is provided in the [link](https://github.com/SungjaeJung1031/rust/tree/main/rust-hello-cargo).
{{< /hint >}}