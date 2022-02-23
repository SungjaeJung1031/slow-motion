---
author: "slow-motion"
date: 2022-02-22
linktitle: Rust Hello World
title: Rust Hello World
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

1. Create hello-world.rs file and enter the code in the below code block.

```go {linenos=table,hl_lines=[8,"15-17"],linenostart=0}
fn main()
{
    println!("Hello, world!");
}
```

2. Save the file and run the file
```
> rustc hello-world.rs
> ./hello-world
```

{{< expand "Output">}}
Hello, world!
{{< /expand >}}

{{< hint info >}}
**Source Code**

Source code in this post is provided in the [link](https://github.com/SungjaeJung1031/rust/blob/main/rust-hello-world/hello-world.rs).
{{< /hint >}}