---
author: "slow-motion"
date: 2022-02-25
linktitle: Rust Data Types
title: Rust Data Types
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

There are two data types subsets in Rust: Scalar Types and Compound Types

TBD.

{{< mermaid class="text-center">}}
graph LR
    root[Rust Primitive Data Types] 
    root --> 11[Integer Types]
    root --> 12[Floating Point Types]
    root --> 13[Boolean Types]
    root --> 14[Character Types]
    root --> 21[Array Types]
    root --> 22[Tuple Types]

    subgraph Scalar Types
        11 & 12 & 13 & 14
    end

    subgraph Compound Types
        21 & 22
    end

    click 11 "./#integer-types"
    click 12 "./#floating-point-types"
    click 13 "./#boolean-types"
    click 14 "./#character-types"
    click 21 "./#array-types"
    click 22 "./#tuple-types"
    

{{< /mermaid >}}

# Rust Primitive Data Types
## Scalar Types
### Integer Types

<!-- [integer overflow](https://en.wikipedia.org/wiki/Integer_overflow)
[Unrecoverable Errors with panic!](#) -->

<table>
<tr>
<td rowspan=2>Size  <td colspan=2>Type Specifier (Range)
<tr>
<td colspan=1>Signed <td colspan=1>Unsigned
<tr>
<td colspan=1>8-bit <td colspan=1>i8   ($-2^{7}$~$2^{7}-1$) <td colspan=1>u8   ($0$~$2^{8}-1$)
<tr>
<td colspan=1>16-bit <td colspan=1>i16   ($-2^{15}$~$2^{15}-1$) <td colspan=1>u16   ($0$~$2^{16}-1$)
<tr>
<td colspan=1>32-bit <td colspan=1>i32   ($-2^{31}$~$2^{31}-1$)  <td colspan=1>u32   ($0$~$2^{32}-1$)
<tr>
<td colspan=1>64-bit <td colspan=1>i64   ($-2^{63}$~$2^{63}-1$) <td colspan=1>u64   ($0$~$2^{64}-1$)
<tr>
<td colspan=1>128-bit <td colspan=1>i128   ($-2^{127}$~$2^{127}-1$)<td colspan=1>u128   ($0$~$2^{128}-1$)
<tr>
<td colspan=1>arch <td colspan=1>isize    (depending on the target architecture) <td colspan=1>usize   (depending on the target architecture)
</table>

As shown in the table above, there are 5 integer types. Depending on the representation of the negative and positive numbers, each integer type has **signdness** property; **signed** and **unsigned**. The signed integer with the data length $n$ can store numbers in the range $-2^{n-1}$~$-2^{n-1}-1$, and the range of the unsigned integer type has data range $0$~$2^{n}-1$. When developing, the range of the integer type must be carefully taken into account due to the [**integer overflow**](https://en.wikipedia.org/wiki/Integer_overflow). Rust operates integer with [**two's complement**](https://en.wikipedia.org/wiki/Two%27s_complement) and integer overflow in Rust behaves defined by two's complement.

The last type **arch** has a special property. This is not the type that has the deterministic range. The sizes of the **isize** and **usize** depend on the target architecture. For instance, if the target architecture of the program written with Rust is 64-bit architecture, the ranges of the isize and usize are the same with those of i64 and u64 respectively.

If a integer literal is not constrained, **i32** is the default type.

### Floating-Point Types

There are two types of floating-point numbers: f32 and f64. The range of those two types is defined by the [IEEE 753-2208](https://en.wikipedia.org/wiki/IEEE_754#Basic_and_interchange_formats)

| Size   | Type specifier | 
|-------:|:---------------|
| 32-bit | f32            |
| 64-bit | f64            |

Rust's default floating-pointer type is f64 since modern computer architecture can handle 64-bit floating-pointer numbers as fast as 32-bit floating-numbers are operated. Floating-point arithmatic operation is not free from [overflow](https://en.wikipedia.org/wiki/Floating-point_arithmetic). Therefore, implicit type-casting between the floating-point type variables must be carefully considered.

### Boolean Types

As other programming language, Rust's boolean types has two values: **true** and **false**. If the true and false is casted to integer values, the values will become $1$ and $0$ with i32 integer type.  
### Character Types
Rust's character type is 4 bytes unlike ohter language that uses character type variable for ASCII. Rust can represents a [Unicode Scalar Value](https://en.wikipedia.org/wiki/List_of_Unicode_characters) using character type variable, such as accented letters with [diacritic](https://en.wikipedia.org/wiki/Diacritic), character of Asian lanaguages (Korean, Japanese, and Chinese), emoji, and [zero-width spaces](https://en.wikipedia.org/wiki/Zero-width_space). Unfortunately, alongside of the benefit of the various representation of the Rust's character type variable, a drawback co-exists.

#### Storing UTF-8 Encoded Text with Strings
In computer science, the character type variable is not originally designed to handle such various data as Rust's character type variable can do.\
TBC.
## Compound Types
### Array Types
**Array** is a way to collect multiple values. An array is comprised of elements that have the same type. Unlike other programming languages, Rust's array cannot be resized. Vector type is provided for the developer who wants to use a contiguous growable array type. The difference between the array and the vector types in Rust is not just the ability to be resized. The data of array type variables is allocated on the stack, and that of vector type variable uses heap.
Below is the code example of array value. The array type variable, ai32Arr, has 7 integer type variables as its elements.

```go {linenos=table,hl_lines=[8,"15-17"],linenostart=0}
fn main() 
{
    let ai32Arr = [1, 2, 3, 4, 5, 6, 7];
    let strArr = ["alice", "atlas", "lhc-b"];
}
```

Two arrays above example do not explicitly represent the type of the element, but rather a developer recognizes that intuitively. 
Rust provides an explicit way to specify the variable type of the elements and the size of the array as below.

```go {linenos=table,hl_lines=[8,"15-17"],linenostart=0}
fn main() 
{
    let ai32_arr: [i32; 7] = [1, 2, 3, 4, 5, 6, 7];
    let str_arr: [String; 3];
    str_arr = ["alice".to_string(), "atlas".to_string(), "lhc-b".to_string()];
}
```
Next to the name of the two variables are follows; colon and square brackets with semi-colon inside. As shown in the second example, strArr, array type variables can be defined after the declaration of the variable.


If the elements of the array are the same, the array can be defined in concise way as below:
```go {linenos=table,hl_lines=[8,"15-17"],linenostart=0}
fn main() 
{
    let ai32_arr: [i32; 7] = [3;7]; // = [3, 3, 3, 3, 3, 3, 3]
}
```
In the above example, ai32_array contains 7 elements and all the elements are set to 3. 

#### Array Element Indexing
Array is a block of memory with one or more elements and allocated on the stack. The array element can be accessed as below example:

```go {linenos=table,hl_lines=[8,"15-17"],linenostart=0}
fn main() 
{
    let ai32_arr: [i32; 7] = [1, 2, 3, 4, 5, 6, 7];
    let str_arr: [String; 3];
    str_arr = ["alice".to_string(), "atlas".to_string(), "lhc-b".to_string()];

    let ai32_arr_3 = ai32_arr[3];
    let str_arr_0 = str_arr[0].clone();

    println!("The third element of ai32_arr is: {}", ai32_arr_3);
    println!("The first element of str_arr is: {}", str_arr_0);
}
```
{{< expand "Output">}}
Compiling data-types v0.1.0 (.../rust/data-types)\
Finished dev [unoptimized + debuginfo] target(s) in 0.12s\
Running `target/debug/data-types`\
The first element of ai32_arr is: 4\
The first element of str_arr is: alice
{{< /expand >}}

As shown, the array indexing is the same as other programming languages, and the index of the first element is 0.
In the case of a source code building with an incorrect array indexing will display error message like below:

```go {linenos=table,hl_lines=[8,"15-17"],linenostart=0}
fn main() 
{
    let ai32_arr: [i32; 7] = [1, 2, 3, 4, 5, 6, 7];
    let str_arr: [String; 3];
    str_arr = ["alice".to_string(), "atlas".to_string(), "lhc-b".to_string()];

    let str_arr_4 = str_arr[4].clone(); // incorrect array indexing
}
```

{{< expand "Output">}}
Compiling data-types v0.1.0 (.../rust/data-types)\
warning: unused variable: `str_arr_4`\
 --> src/main.rs:6:6\
  |\
6 |     let str_arr_4 = str_arr[4].clone();\
  |         ^^^^^^^^^ help: if this is intentional, prefix it with an underscore: `_str_arr_4`\
  |\
  = note: `#[warn(unused_variables)]` on by default\
\
error: this operation will panic at runtime\
 --> src/main.rs:6:21\
  |
6 |     let str_arr_4 = str_arr[4].clone();\
  |                     ^^^^^^^^^^ index out of bounds: the length is 3 but the index is 4\
  |
  = note: `#[deny(unconditional_panic)]` on by default\
  \
warning: `data-types` (bin "data-types") generated 1 warning\
error: could not compile `data-types` due to previous error; 1 warning emitted
{{< /expand >}}


### Tuple Types
Unlike arrays, tuples are compound types that group values with different data types. A tuple must be declared with a fixed length and the size cannot be modified.
As arrays, data types of the tuple values can be both implicitly and explicitly specified.
The first example shows the implicit way. As shown below, tuples use parentheses, instaed of squre brackets as arrays. In the line 2, two seperate variables, x and _y takes, the two values of short_tup. The way is called **destructing** since values of a tuple is divided into several parts.

```go {linenos=table,hl_lines=[8,"15-17"],linenostart=0}
fn main() 
{
    let short_tup = (100, 1.1);
    let (x, _y) = short_tup;    // recommended that unused variables have prefix _
    let long_tup = (1u8, -2i16, 0.1f32, 'c', true);
    let tuple_of_tuples = (('a', 'b', 'c'), (1u8, 2u8), (0.1f32));

    println!("short_tup: {:?}", short_tup); // {:?} is used to print all the values of a tuple
    println!("the first value of short_tup: {}", short_tup.0);
    println!("the second value of short_tup: {}", short_tup.1);
    println!("long_tup: {:?}", long_tup);
    println!("tuple_of_tuples: {:?}", tuple_of_tuples);
    println!("x: {}", x);
}
```
{{< expand "Output">}}
short_tup: (100, 1.1)\
the first value of short_tup: 100\
the second value of short_tup: 1.1\
long_tup: (1, -2, 0.1, 'c', true)\
tuple_of_tuples: (('a', 'b', 'c'), (1, 2), 0.1)\
x: 100
{{< /expand >}}

Below example shows the explicit way to specify tuple value types.

```go {linenos=table,hl_lines=[8,"15-17"],linenostart=0}
fn main() 
{
    let short_tup: (i32,f64) = (100, 1.1);
    println!("the first value of short_tup: {}", short_tup.0);
    println!("the sencond value of short_tup: {}", short_tup.1);
}
```
{{< expand "Output">}}
the first value of short_tup: 100\
the second value of short_tup: 1.1
{{< /expand >}}

As shown two tuple type examples, the index of the tuple has the same manner with that of arrays; the index of the first value is 0. However, tuples do not use square brackets for indexing; rather it uses period (.) followed by the index of the value.
