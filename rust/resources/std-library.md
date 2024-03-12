# Crate [std](https://doc.rust-lang.org/std/index.html#)

1.0.0 · [source](https://doc.rust-lang.org/src/std/lib.rs.html#1-729) ·

## [The Rust Standard Library](https://doc.rust-lang.org/std/index.html#the-rust-standard-library)

The Rust Standard Library is the foundation of portable Rust software, a set of minimal and battle-tested shared abstractions for the [broader Rust ecosystem](https://crates.io). It offers core types, like [`Vec<T>`](https://doc.rust-lang.org/std/vec/struct.Vec.html "struct std::vec::Vec") and [`Option<T>`](https://doc.rust-lang.org/std/option/enum.Option.html "enum std::option::Option"), library-defined [operations on language primitives](https://doc.rust-lang.org/std/index.html#primitives), [standard macros](https://doc.rust-lang.org/std/index.html#macros), [I/O](https://doc.rust-lang.org/std/io/index.html "mod std::io") and [multithreading](https://doc.rust-lang.org/std/thread/index.html "mod std::thread"), among [many other things](https://doc.rust-lang.org/std/index.html#what-is-in-the-standard-library-documentation).

`std` is available to all Rust crates by default. Therefore, the standard library can be accessed in [`use`](https://doc.rust-lang.org/book/ch07-02-defining-modules-to-control-scope-and-privacy.html) statements through the path `std`, as in [`use std::env`](https://doc.rust-lang.org/std/env/index.html).

## [How to read this documentation](https://doc.rust-lang.org/std/index.html#how-to-read-this-documentation)

If you already know the name of what you are looking for, the fastest way to find it is to use the [search bar](https://doc.rust-lang.org/std/index.html#) at the top of the page.

Otherwise, you may want to jump to one of these useful sections:

- [`std::*` modules](https://doc.rust-lang.org/std/index.html#modules)
- [Primitive types](https://doc.rust-lang.org/std/index.html#primitives)
- [Standard macros](https://doc.rust-lang.org/std/index.html#macros)
- [The Rust Prelude](https://doc.rust-lang.org/std/prelude/index.html "mod std::prelude")

If this is your first time, the documentation for the standard library is written to be casually perused. Clicking on interesting things should generally lead you to interesting places. Still, there are important bits you don’t want to miss, so read on for a tour of the standard library and its documentation!

Once you are familiar with the contents of the standard library you may begin to find the verbosity of the prose distracting. At this stage in your development you may want to press the `[-]` button near the top of the page to collapse it into a more skimmable view.

While you are looking at that `[-]` button also notice the `source` link. Rust’s API documentation comes with the source code and you are encouraged to read it. The standard library source is generally high quality and a peek behind the curtains is often enlightening.

## [What is in the standard library documentation?](https://doc.rust-lang.org/std/index.html#what-is-in-the-standard-library-documentation)

First of all, The Rust Standard Library is divided into a number of focused modules, [all listed further down this page](https://doc.rust-lang.org/std/index.html#modules). These modules are the bedrock upon which all of Rust is forged, and they have mighty names like [`std::slice`](https://doc.rust-lang.org/std/slice/index.html "mod std::slice") and [`std::cmp`](https://doc.rust-lang.org/std/cmp/index.html "mod std::cmp"). Modules’ documentation typically includes an overview of the module along with examples, and are a smart place to start familiarizing yourself with the library.

Second, implicit methods on [primitive types](https://doc.rust-lang.org/book/ch03-02-data-types.html) are documented here. This can be a source of confusion for two reasons:

1. While primitives are implemented by the compiler, the standard library implements methods directly on the primitive types (and it is the only library that does so), which are [documented in the section on primitives](https://doc.rust-lang.org/std/index.html#primitives).
2. The standard library exports many modules _with the same name as primitive types_. These define additional items related to the primitive type, but not the all-important methods.

So for example there is a [page for the primitive type `i32`](https://doc.rust-lang.org/std/primitive.i32.html "primitive i32") that lists all the methods that can be called on 32-bit integers (very useful), and there is a [page for the module `std::i32`](https://doc.rust-lang.org/std/i32/index.html "mod std::i32") that documents the constant values [`MIN`](https://doc.rust-lang.org/std/i32/constant.MIN.html "constant std::i32::MIN") and [`MAX`](https://doc.rust-lang.org/std/i32/constant.MAX.html "constant std::i32::MAX") (rarely useful).

Note the documentation for the primitives [`str`](https://doc.rust-lang.org/std/primitive.str.html "primitive str") and [`[T]`](https://doc.rust-lang.org/std/primitive.slice.html "primitive slice") (also called ‘slice’). Many method calls on [`String`](https://doc.rust-lang.org/std/string/struct.String.html "struct std::string::String") and [`Vec<T>`](https://doc.rust-lang.org/std/vec/struct.Vec.html "struct std::vec::Vec") are actually calls to methods on [`str`](https://doc.rust-lang.org/std/primitive.str.html "primitive str") and [`[T]`](https://doc.rust-lang.org/std/primitive.slice.html "primitive slice") respectively, via [deref coercions](https://doc.rust-lang.org/book/ch15-02-deref.html#implicit-deref-coercions-with-functions-and-methods).

Third, the standard library defines [The Rust Prelude](https://doc.rust-lang.org/std/prelude/index.html "mod std::prelude"), a small collection of items - mostly traits - that are imported into every module of every crate. The traits in the prelude are pervasive, making the prelude documentation a good entry point to learning about the library.

And finally, the standard library exports a number of standard macros, and [lists them on this page](https://doc.rust-lang.org/std/index.html#macros) (technically, not all of the standard macros are defined by the standard library - some are defined by the compiler - but they are documented here the same). Like the prelude, the standard macros are imported by default into all crates.

## [Contributing changes to the documentation](https://doc.rust-lang.org/std/index.html#contributing-changes-to-the-documentation)

Check out the rust contribution guidelines [here](https://rustc-dev-guide.rust-lang.org/contributing.html#writing-documentation). The source for this documentation can be found on [GitHub](https://github.com/rust-lang/rust). To contribute changes, make sure you read the guidelines first, then submit pull-requests for your suggested changes.

Contributions are appreciated! If you see a part of the docs that can be improved, submit a PR, or chat with us first on [Discord](https://discord.gg/rust-lang) #docs.

## [A Tour of The Rust Standard Library](https://doc.rust-lang.org/std/index.html#a-tour-of-the-rust-standard-library)

The rest of this crate documentation is dedicated to pointing out notable features of The Rust Standard Library.

### [Containers and collections](https://doc.rust-lang.org/std/index.html#containers-and-collections)

The [`option`](https://doc.rust-lang.org/std/option/index.html "mod std::option") and [`result`](https://doc.rust-lang.org/std/result/index.html "mod std::result") modules define optional and error-handling types, [`Option<T>`](https://doc.rust-lang.org/std/option/enum.Option.html "enum std::option::Option") and [`Result<T, E>`](https://doc.rust-lang.org/std/result/enum.Result.html "enum std::result::Result"). The [`iter`](https://doc.rust-lang.org/std/iter/index.html "mod std::iter") module defines Rust’s iterator trait, [`Iterator`](https://doc.rust-lang.org/std/iter/trait.Iterator.html "trait std::iter::Iterator"), which works with the [`for`](https://doc.rust-lang.org/book/ch03-05-control-flow.html#looping-through-a-collection-with-for) loop to access collections.

The standard library exposes three common ways to deal with contiguous regions of memory:

- [`Vec<T>`](https://doc.rust-lang.org/std/vec/struct.Vec.html "struct std::vec::Vec") - A heap-allocated _vector_ that is resizable at runtime.
- [`[T; N]`](https://doc.rust-lang.org/std/primitive.array.html "primitive array") - An inline _array_ with a fixed size at compile time.
- [`[T]`](https://doc.rust-lang.org/std/primitive.slice.html "primitive slice") - A dynamically sized _slice_ into any other kind of contiguous storage, whether heap-allocated or not.

Slices can only be handled through some kind of _pointer_, and as such come in many flavors such as:

- `&[T]` - _shared slice_
- `&mut [T]` - _mutable slice_
- [`Box<[T]>`](https://doc.rust-lang.org/std/boxed/index.html "mod std::boxed") - _owned slice_

[`str`](https://doc.rust-lang.org/std/primitive.str.html "primitive str"), a UTF-8 string slice, is a primitive type, and the standard library defines many methods for it. Rust [`str`](https://doc.rust-lang.org/std/primitive.str.html "primitive str")s are typically accessed as immutable references: `&str`. Use the owned [`String`](https://doc.rust-lang.org/std/string/struct.String.html "struct std::string::String") for building and mutating strings.

For converting to strings use the [`format!`](https://doc.rust-lang.org/std/macro.format.html "macro std::format") macro, and for converting from strings use the [`FromStr`](https://doc.rust-lang.org/std/str/trait.FromStr.html "trait std::str::FromStr") trait.

Data may be shared by placing it in a reference-counted box or the [`Rc`](https://doc.rust-lang.org/std/rc/struct.Rc.html "struct std::rc::Rc") type, and if further contained in a [`Cell`](https://doc.rust-lang.org/std/cell/struct.Cell.html "struct std::cell::Cell") or [`RefCell`](https://doc.rust-lang.org/std/cell/struct.RefCell.html "struct std::cell::RefCell"), may be mutated as well as shared. Likewise, in a concurrent setting it is common to pair an atomically-reference-counted box, [`Arc`](https://doc.rust-lang.org/std/sync/struct.Arc.html "struct std::sync::Arc"), with a [`Mutex`](https://doc.rust-lang.org/std/sync/struct.Mutex.html "struct std::sync::Mutex") to get the same effect.

The [`collections`](https://doc.rust-lang.org/std/collections/index.html "mod std::collections") module defines maps, sets, linked lists and other typical collection types, including the common [`HashMap<K, V>`](https://doc.rust-lang.org/std/collections/hash_map/struct.HashMap.html "struct std::collections::hash_map::HashMap").

### [Platform abstractions and I/O](https://doc.rust-lang.org/std/index.html#platform-abstractions-and-io)

Besides basic data types, the standard library is largely concerned with abstracting over differences in common platforms, most notably Windows and Unix derivatives.

Common types of I/O, including [files](https://doc.rust-lang.org/std/fs/struct.File.html "struct std::fs::File"), [TCP](https://doc.rust-lang.org/std/net/struct.TcpStream.html "struct std::net::TcpStream"), and [UDP](https://doc.rust-lang.org/std/net/struct.UdpSocket.html "struct std::net::UdpSocket"), are defined in the [`io`](https://doc.rust-lang.org/std/io/index.html "mod std::io"), [`fs`](https://doc.rust-lang.org/std/fs/index.html "mod std::fs"), and [`net`](https://doc.rust-lang.org/std/net/index.html "mod std::net") modules.

The [`thread`](https://doc.rust-lang.org/std/thread/index.html "mod std::thread") module contains Rust’s threading abstractions. [`sync`](https://doc.rust-lang.org/std/sync/index.html "mod std::sync") contains further primitive shared memory types, including [`atomic`](https://doc.rust-lang.org/std/sync/atomic/index.html "mod std::sync::atomic") and [`mpsc`](https://doc.rust-lang.org/std/sync/mpsc/index.html "mod std::sync::mpsc"), which contains the channel types for message passing.

## [Use before and after `main()`](https://doc.rust-lang.org/std/index.html#use-before-and-after-main)

Many parts of the standard library are expected to work before and after `main()`; but this is not guaranteed or ensured by tests. It is recommended that you write your own tests and run them on each platform you wish to support. This means that use of `std` before/after main, especially of features that interact with the OS or global state, is exempted from stability and portability guarantees and instead only provided on a best-effort basis. Nevertheless bug reports are appreciated.

On the other hand `core` and `alloc` are most likely to work in such environments with the caveat that any hookable behavior such as panics, oom handling or allocators will also depend on the compatibility of the hooks.

Some features may also behave differently outside main, e.g. stdio could become unbuffered, some panics might turn into aborts, backtraces might not get symbolicated or similar.

Non-exhaustive list of known limitations:

- after-main use of thread-locals, which also affects additional features:
    - [`thread::current()`](https://doc.rust-lang.org/std/thread/fn.current.html "fn std::thread::current")
    - [`thread::scope()`](https://doc.rust-lang.org/std/thread/fn.scope.html "fn std::thread::scope")
    - [`sync::mpsc`](https://doc.rust-lang.org/std/sync/mpsc/index.html "mod std::sync::mpsc")
- before-main stdio file descriptors are not guaranteed to be open on unix platforms

## [Primitive Types](https://doc.rust-lang.org/std/index.html#primitives)

- [array](https://doc.rust-lang.org/std/primitive.array.html "primitive std::array")
    
    A fixed-size array, denoted `[T; N]`, for the element type, `T`, and the non-negative compile-time constant size, `N`.
    
- [bool](https://doc.rust-lang.org/std/primitive.bool.html "primitive std::bool")
    
    The boolean type.
    
- [char](https://doc.rust-lang.org/std/primitive.char.html "primitive std::char")
    
    A character type.
    
- [f32](https://doc.rust-lang.org/std/primitive.f32.html "primitive std::f32")
    
    A 32-bit floating point type (specifically, the “binary32” type defined in IEEE 754-2008).
    
- [f64](https://doc.rust-lang.org/std/primitive.f64.html "primitive std::f64")
    
    A 64-bit floating point type (specifically, the “binary64” type defined in IEEE 754-2008).
    
- [fn](https://doc.rust-lang.org/std/primitive.fn.html "primitive std::fn")
    
    Function pointers, like `fn(usize) -> bool`.
    
- [i8](https://doc.rust-lang.org/std/primitive.i8.html "primitive std::i8")
    
    The 8-bit signed integer type.
    
- [i16](https://doc.rust-lang.org/std/primitive.i16.html "primitive std::i16")
    
    The 16-bit signed integer type.
    
- [i32](https://doc.rust-lang.org/std/primitive.i32.html "primitive std::i32")
    
    The 32-bit signed integer type.
    
- [i64](https://doc.rust-lang.org/std/primitive.i64.html "primitive std::i64")
    
    The 64-bit signed integer type.
    
- [i128](https://doc.rust-lang.org/std/primitive.i128.html "primitive std::i128")
    
    The 128-bit signed integer type.
    
- [isize](https://doc.rust-lang.org/std/primitive.isize.html "primitive std::isize")
    
    The pointer-sized signed integer type.
    
- [pointer](https://doc.rust-lang.org/std/primitive.pointer.html "primitive std::pointer")
    
    Raw, unsafe pointers, `*const T`, and `*mut T`.
    
- [reference](https://doc.rust-lang.org/std/primitive.reference.html "primitive std::reference")
    
    References, `&T` and `&mut T`.
    
- [slice](https://doc.rust-lang.org/std/primitive.slice.html "primitive std::slice")
    
    A dynamically-sized view into a contiguous sequence, `[T]`. Contiguous here means that elements are laid out so that every element is the same distance from its neighbors.
    
- [str](https://doc.rust-lang.org/std/primitive.str.html "primitive std::str")
    
    String slices.
    
- [tuple](https://doc.rust-lang.org/std/primitive.tuple.html "primitive std::tuple")
    
    A finite heterogeneous sequence, `(T, U, ..)`.
    
- [u8](https://doc.rust-lang.org/std/primitive.u8.html "primitive std::u8")
    
    The 8-bit unsigned integer type.
    
- [u16](https://doc.rust-lang.org/std/primitive.u16.html "primitive std::u16")
    
    The 16-bit unsigned integer type.
    
- [u32](https://doc.rust-lang.org/std/primitive.u32.html "primitive std::u32")
    
    The 32-bit unsigned integer type.
    
- [u64](https://doc.rust-lang.org/std/primitive.u64.html "primitive std::u64")
    
    The 64-bit unsigned integer type.
    
- [u128](https://doc.rust-lang.org/std/primitive.u128.html "primitive std::u128")
    
    The 128-bit unsigned integer type.
    
- [unit](https://doc.rust-lang.org/std/primitive.unit.html "primitive std::unit")
    
    The `()` type, also called “unit”.
    
- [usize](https://doc.rust-lang.org/std/primitive.usize.html "primitive std::usize")
    
    The pointer-sized unsigned integer type.
    
- [never](https://doc.rust-lang.org/std/primitive.never.html "primitive std::never")Experimental
    
    The `!` type, also called “never”.
    

## [Modules](https://doc.rust-lang.org/std/index.html#modules)

- [alloc](https://doc.rust-lang.org/std/alloc/index.html "mod std::alloc")
    
    Memory allocation APIs.
    
- [any](https://doc.rust-lang.org/std/any/index.html "mod std::any")
    
    Utilities for dynamic typing or type reflection.
    
- [arch](https://doc.rust-lang.org/std/arch/index.html "mod std::arch")
    
    SIMD and vendor intrinsics module.
    
- [array](https://doc.rust-lang.org/std/array/index.html "mod std::array")
    
    Utilities for the array primitive type.
    
- [ascii](https://doc.rust-lang.org/std/ascii/index.html "mod std::ascii")
    
    Operations on ASCII strings and characters.
    
- [backtrace](https://doc.rust-lang.org/std/backtrace/index.html "mod std::backtrace")
    
    Support for capturing a stack backtrace of an OS thread
    
- [borrow](https://doc.rust-lang.org/std/borrow/index.html "mod std::borrow")
    
    A module for working with borrowed data.
    
- [boxed](https://doc.rust-lang.org/std/boxed/index.html "mod std::boxed")
    
    The `Box<T>` type for heap allocation.
    
- [cell](https://doc.rust-lang.org/std/cell/index.html "mod std::cell")
    
    Shareable mutable containers.
    
- [char](https://doc.rust-lang.org/std/char/index.html "mod std::char")
    
    Utilities for the `char` primitive type.
    
- [clone](https://doc.rust-lang.org/std/clone/index.html "mod std::clone")
    
    The `Clone` trait for types that cannot be ‘implicitly copied’.
    
- [cmp](https://doc.rust-lang.org/std/cmp/index.html "mod std::cmp")
    
    Utilities for comparing and ordering values.
    
- [collections](https://doc.rust-lang.org/std/collections/index.html "mod std::collections")
    
    Collection types.
    
- [convert](https://doc.rust-lang.org/std/convert/index.html "mod std::convert")
    
    Traits for conversions between types.
    
- [default](https://doc.rust-lang.org/std/default/index.html "mod std::default")
    
    The `Default` trait for types with a default value.
    
- [env](https://doc.rust-lang.org/std/env/index.html "mod std::env")
    
    Inspection and manipulation of the process’s environment.
    
- [error](https://doc.rust-lang.org/std/error/index.html "mod std::error")
    
    Interfaces for working with Errors.
    
- [f32](https://doc.rust-lang.org/std/f32/index.html "mod std::f32")
    
    Constants for the `f32` single-precision floating point type.
    
- [f64](https://doc.rust-lang.org/std/f64/index.html "mod std::f64")
    
    Constants for the `f64` double-precision floating point type.
    
- [ffi](https://doc.rust-lang.org/std/ffi/index.html "mod std::ffi")
    
    Utilities related to FFI bindings.
    
- [fmt](https://doc.rust-lang.org/std/fmt/index.html "mod std::fmt")
    
    Utilities for formatting and printing `String`s.
    
- [fs](https://doc.rust-lang.org/std/fs/index.html "mod std::fs")
    
    Filesystem manipulation operations.
    
- [future](https://doc.rust-lang.org/std/future/index.html "mod std::future")
    
    Asynchronous basic functionality.
    
- [hash](https://doc.rust-lang.org/std/hash/index.html "mod std::hash")
    
    Generic hashing support.
    
- [hint](https://doc.rust-lang.org/std/hint/index.html "mod std::hint")
    
    Hints to compiler that affects how code should be emitted or optimized. Hints may be compile time or runtime.
    
- [i8](https://doc.rust-lang.org/std/i8/index.html "mod std::i8")Deprecation planned
    
    Redundant constants module for the [`i8` primitive type](https://doc.rust-lang.org/std/primitive.i8.html "primitive i8").
    
- [i16](https://doc.rust-lang.org/std/i16/index.html "mod std::i16")Deprecation planned
    
    Redundant constants module for the [`i16` primitive type](https://doc.rust-lang.org/std/primitive.i16.html "primitive i16").
    
- [i32](https://doc.rust-lang.org/std/i32/index.html "mod std::i32")Deprecation planned
    
    Redundant constants module for the [`i32` primitive type](https://doc.rust-lang.org/std/primitive.i32.html "primitive i32").
    
- [i64](https://doc.rust-lang.org/std/i64/index.html "mod std::i64")Deprecation planned
    
    Redundant constants module for the [`i64` primitive type](https://doc.rust-lang.org/std/primitive.i64.html "primitive i64").
    
- [i128](https://doc.rust-lang.org/std/i128/index.html "mod std::i128")Deprecation planned
    
    Redundant constants module for the [`i128` primitive type](https://doc.rust-lang.org/std/primitive.i128.html "primitive i128").
    
- [io](https://doc.rust-lang.org/std/io/index.html "mod std::io")
    
    Traits, helpers, and type definitions for core I/O functionality.
    
- [isize](https://doc.rust-lang.org/std/isize/index.html "mod std::isize")Deprecation planned
    
    Redundant constants module for the [`isize` primitive type](https://doc.rust-lang.org/std/primitive.isize.html "primitive isize").
    
- [iter](https://doc.rust-lang.org/std/iter/index.html "mod std::iter")
    
    Composable external iteration.
    
- [marker](https://doc.rust-lang.org/std/marker/index.html "mod std::marker")
    
    Primitive traits and types representing basic properties of types.
    
- [mem](https://doc.rust-lang.org/std/mem/index.html "mod std::mem")
    
    Basic functions for dealing with memory.
    
- [net](https://doc.rust-lang.org/std/net/index.html "mod std::net")
    
    Networking primitives for TCP/UDP communication.
    
- [num](https://doc.rust-lang.org/std/num/index.html "mod std::num")
    
    Additional functionality for numerics.
    
- [ops](https://doc.rust-lang.org/std/ops/index.html "mod std::ops")
    
    Overloadable operators.
    
- [option](https://doc.rust-lang.org/std/option/index.html "mod std::option")
    
    Optional values.
    
- [os](https://doc.rust-lang.org/std/os/index.html "mod std::os")
    
    OS-specific functionality.
    
- [panic](https://doc.rust-lang.org/std/panic/index.html "mod std::panic")
    
    Panic support in the standard library.
    
- [path](https://doc.rust-lang.org/std/path/index.html "mod std::path")
    
    Cross-platform path manipulation.
    
- [pin](https://doc.rust-lang.org/std/pin/index.html "mod std::pin")
    
    Types that pin data to its location in memory.
    
- [prelude](https://doc.rust-lang.org/std/prelude/index.html "mod std::prelude")
    
    The Rust Prelude
    
- [primitive](https://doc.rust-lang.org/std/primitive/index.html "mod std::primitive")
    
    This module reexports the primitive types to allow usage that is not possibly shadowed by other declared types.
    
- [process](https://doc.rust-lang.org/std/process/index.html "mod std::process")
    
    A module for working with processes.
    
- [ptr](https://doc.rust-lang.org/std/ptr/index.html "mod std::ptr")
    
    Manually manage memory through raw pointers.
    
- [rc](https://doc.rust-lang.org/std/rc/index.html "mod std::rc")
    
    Single-threaded reference-counting pointers. ‘Rc’ stands for ‘Reference Counted’.
    
- [result](https://doc.rust-lang.org/std/result/index.html "mod std::result")
    
    Error handling with the `Result` type.
    
- [slice](https://doc.rust-lang.org/std/slice/index.html "mod std::slice")
    
    Utilities for the slice primitive type.
    
- [str](https://doc.rust-lang.org/std/str/index.html "mod std::str")
    
    Utilities for the `str` primitive type.
    
- [string](https://doc.rust-lang.org/std/string/index.html "mod std::string")
    
    A UTF-8–encoded, growable string.
    
- [sync](https://doc.rust-lang.org/std/sync/index.html "mod std::sync")
    
    Useful synchronization primitives.
    
- [task](https://doc.rust-lang.org/std/task/index.html "mod std::task")
    
    Types and Traits for working with asynchronous tasks.
    
- [thread](https://doc.rust-lang.org/std/thread/index.html "mod std::thread")
    
    Native threads.
    
- [time](https://doc.rust-lang.org/std/time/index.html "mod std::time")
    
    Temporal quantification.
    
- [u8](https://doc.rust-lang.org/std/u8/index.html "mod std::u8")Deprecation planned
    
    Redundant constants module for the [`u8` primitive type](https://doc.rust-lang.org/std/primitive.u8.html "primitive u8").
    
- [u16](https://doc.rust-lang.org/std/u16/index.html "mod std::u16")Deprecation planned
    
    Redundant constants module for the [`u16` primitive type](https://doc.rust-lang.org/std/primitive.u16.html "primitive u16").
    
- [u32](https://doc.rust-lang.org/std/u32/index.html "mod std::u32")Deprecation planned
    
    Redundant constants module for the [`u32` primitive type](https://doc.rust-lang.org/std/primitive.u32.html "primitive u32").
    
- [u64](https://doc.rust-lang.org/std/u64/index.html "mod std::u64")Deprecation planned
    
    Redundant constants module for the [`u64` primitive type](https://doc.rust-lang.org/std/primitive.u64.html "primitive u64").
    
- [u128](https://doc.rust-lang.org/std/u128/index.html "mod std::u128")Deprecation planned
    
    Redundant constants module for the [`u128` primitive type](https://doc.rust-lang.org/std/primitive.u128.html "primitive u128").
    
- [usize](https://doc.rust-lang.org/std/usize/index.html "mod std::usize")Deprecation planned
    
    Redundant constants module for the [`usize` primitive type](https://doc.rust-lang.org/std/primitive.usize.html "primitive usize").
    
- [vec](https://doc.rust-lang.org/std/vec/index.html "mod std::vec")
    
    A contiguous growable array type with heap-allocated contents, written `Vec<T>`.
    
- [assert_matches](https://doc.rust-lang.org/std/assert_matches/index.html "mod std::assert_matches")Experimental
    
    Unstable module containing the unstable `assert_matches` macro.
    
- [async_iter](https://doc.rust-lang.org/std/async_iter/index.html "mod std::async_iter")Experimental
    
    Composable asynchronous iteration.
    
- [intrinsics](https://doc.rust-lang.org/std/intrinsics/index.html "mod std::intrinsics")Experimental
    
    Compiler intrinsics.
    
- [simd](https://doc.rust-lang.org/std/simd/index.html "mod std::simd")Experimental
    
    Portable SIMD module.
    

## [Macros](https://doc.rust-lang.org/std/index.html#macros)

- [assert](https://doc.rust-lang.org/std/macro.assert.html "macro std::assert")
    
    Asserts that a boolean expression is `true` at runtime.
    
- [assert_eq](https://doc.rust-lang.org/std/macro.assert_eq.html "macro std::assert_eq")
    
    Asserts that two expressions are equal to each other (using [`PartialEq`](https://doc.rust-lang.org/std/cmp/trait.PartialEq.html "trait std::cmp::PartialEq")).
    
- [assert_ne](https://doc.rust-lang.org/std/macro.assert_ne.html "macro std::assert_ne")
    
    Asserts that two expressions are not equal to each other (using [`PartialEq`](https://doc.rust-lang.org/std/cmp/trait.PartialEq.html "trait std::cmp::PartialEq")).
    
- [cfg](https://doc.rust-lang.org/std/macro.cfg.html "macro std::cfg")
    
    Evaluates boolean combinations of configuration flags at compile-time.
    
- [column](https://doc.rust-lang.org/std/macro.column.html "macro std::column")
    
    Expands to the column number at which it was invoked.
    
- [compile_error](https://doc.rust-lang.org/std/macro.compile_error.html "macro std::compile_error")
    
    Causes compilation to fail with the given error message when encountered.
    
- [concat](https://doc.rust-lang.org/std/macro.concat.html "macro std::concat")
    
    Concatenates literals into a static string slice.
    
- [dbg](https://doc.rust-lang.org/std/macro.dbg.html "macro std::dbg")
    
    Prints and returns the value of a given expression for quick and dirty debugging.
    
- [debug_assert](https://doc.rust-lang.org/std/macro.debug_assert.html "macro std::debug_assert")
    
    Asserts that a boolean expression is `true` at runtime.
    
- [debug_assert_eq](https://doc.rust-lang.org/std/macro.debug_assert_eq.html "macro std::debug_assert_eq")
    
    Asserts that two expressions are equal to each other.
    
- [debug_assert_ne](https://doc.rust-lang.org/std/macro.debug_assert_ne.html "macro std::debug_assert_ne")
    
    Asserts that two expressions are not equal to each other.
    
- [env](https://doc.rust-lang.org/std/macro.env.html "macro std::env")
    
    Inspects an environment variable at compile time.
    
- [eprint](https://doc.rust-lang.org/std/macro.eprint.html "macro std::eprint")
    
    Prints to the standard error.
    
- [eprintln](https://doc.rust-lang.org/std/macro.eprintln.html "macro std::eprintln")
    
    Prints to the standard error, with a newline.
    
- [file](https://doc.rust-lang.org/std/macro.file.html "macro std::file")
    
    Expands to the file name in which it was invoked.
    
- [format](https://doc.rust-lang.org/std/macro.format.html "macro std::format")
    
    Creates a `String` using interpolation of runtime expressions.
    
- [format_args](https://doc.rust-lang.org/std/macro.format_args.html "macro std::format_args")
    
    Constructs parameters for the other string-formatting macros.
    
- [include](https://doc.rust-lang.org/std/macro.include.html "macro std::include")
    
    Parses a file as an expression or an item according to the context.
    
- [include_bytes](https://doc.rust-lang.org/std/macro.include_bytes.html "macro std::include_bytes")
    
    Includes a file as a reference to a byte array.
    
- [include_str](https://doc.rust-lang.org/std/macro.include_str.html "macro std::include_str")
    
    Includes a UTF-8 encoded file as a string.
    
- [is_x86_feature_detected](https://doc.rust-lang.org/std/macro.is_x86_feature_detected.html "macro std::is_x86_feature_detected")x86 or x86-64
    
    A macro to test at _runtime_ whether a CPU feature is available on x86/x86-64 platforms.
    
- [line](https://doc.rust-lang.org/std/macro.line.html "macro std::line")
    
    Expands to the line number on which it was invoked.
    
- [matches](https://doc.rust-lang.org/std/macro.matches.html "macro std::matches")
    
    Returns whether the given expression matches any of the given patterns.
    
- [module_path](https://doc.rust-lang.org/std/macro.module_path.html "macro std::module_path")
    
    Expands to a string that represents the current module path.
    
- [option_env](https://doc.rust-lang.org/std/macro.option_env.html "macro std::option_env")
    
    Optionally inspects an environment variable at compile time.
    
- [panic](https://doc.rust-lang.org/std/macro.panic.html "macro std::panic")
    
    Panics the current thread.
    
- [print](https://doc.rust-lang.org/std/macro.print.html "macro std::print")
    
    Prints to the standard output.
    
- [println](https://doc.rust-lang.org/std/macro.println.html "macro std::println")
    
    Prints to the standard output, with a newline.
    
- [stringify](https://doc.rust-lang.org/std/macro.stringify.html "macro std::stringify")
    
    Stringifies its arguments.
    
- [thread_local](https://doc.rust-lang.org/std/macro.thread_local.html "macro std::thread_local")
    
    Declare a new thread local storage key of type [`std::thread::LocalKey`](https://doc.rust-lang.org/std/thread/struct.LocalKey.html "struct std::thread::LocalKey").
    
- [todo](https://doc.rust-lang.org/std/macro.todo.html "macro std::todo")
    
    Indicates unfinished code.
    
- [try](https://doc.rust-lang.org/std/macro.try.html "macro std::try")Deprecated
    
    Unwraps a result or propagates its error.
    
- [unimplemented](https://doc.rust-lang.org/std/macro.unimplemented.html "macro std::unimplemented")
    
    Indicates unimplemented code by panicking with a message of “not implemented”.
    
- [unreachable](https://doc.rust-lang.org/std/macro.unreachable.html "macro std::unreachable")
    
    Indicates unreachable code.
    
- [vec](https://doc.rust-lang.org/std/macro.vec.html "macro std::vec")
    
    Creates a [`Vec`](https://doc.rust-lang.org/std/vec/struct.Vec.html "struct std::vec::Vec") containing the arguments.
    
- [write](https://doc.rust-lang.org/std/macro.write.html "macro std::write")
    
    Writes formatted data into a buffer.
    
- [writeln](https://doc.rust-lang.org/std/macro.writeln.html "macro std::writeln")
    
    Write formatted data into a buffer, with a newline appended.
    
- [cfg_match](https://doc.rust-lang.org/std/macro.cfg_match.html "macro std::cfg_match")Experimental
    
    A macro for defining `#[cfg]` match-like statements.
    
- [concat_bytes](https://doc.rust-lang.org/std/macro.concat_bytes.html "macro std::concat_bytes")Experimental
    
    Concatenates literals into a byte slice.
    
- [concat_idents](https://doc.rust-lang.org/std/macro.concat_idents.html "macro std::concat_idents")Experimental
    
    Concatenates identifiers into one identifier.
    
- [const_format_args](https://doc.rust-lang.org/std/macro.const_format_args.html "macro std::const_format_args")Experimental
    
    Same as [`format_args`](https://doc.rust-lang.org/std/macro.format_args.html "macro std::format_args"), but can be used in some const contexts.
    
- [format_args_nl](https://doc.rust-lang.org/std/macro.format_args_nl.html "macro std::format_args_nl")Experimental
    
    Same as [`format_args`](https://doc.rust-lang.org/std/macro.format_args.html "macro std::format_args"), but adds a newline in the end.
    
- [log_syntax](https://doc.rust-lang.org/std/macro.log_syntax.html "macro std::log_syntax")Experimental
    
    Prints passed tokens into the standard output.
    
- [trace_macros](https://doc.rust-lang.org/std/macro.trace_macros.html "macro std::trace_macros")Experimental
    
    Enables or disables tracing functionality used for debugging other macros.
    

## [Keywords](https://doc.rust-lang.org/std/index.html#keywords)

- [SelfTy](https://doc.rust-lang.org/std/keyword.SelfTy.html "keyword std::SelfTy")
    
    The implementing type within a [`trait`](https://doc.rust-lang.org/std/keyword.trait.html) or [`impl`](https://doc.rust-lang.org/std/keyword.impl.html) block, or the current type within a type definition.
    
- [as](https://doc.rust-lang.org/std/keyword.as.html "keyword std::as")
    
    Cast between types, or rename an import.
    
- [async](https://doc.rust-lang.org/std/keyword.async.html "keyword std::async")
    
    Return a [`Future`](https://doc.rust-lang.org/std/future/trait.Future.html "trait std::future::Future") instead of blocking the current thread.
    
- [await](https://doc.rust-lang.org/std/keyword.await.html "keyword std::await")
    
    Suspend execution until the result of a [`Future`](https://doc.rust-lang.org/std/future/trait.Future.html "trait std::future::Future") is ready.
    
- [break](https://doc.rust-lang.org/std/keyword.break.html "keyword std::break")
    
    Exit early from a loop.
    
- [const](https://doc.rust-lang.org/std/keyword.const.html "keyword std::const")
    
    Compile-time constants, compile-time evaluable functions, and raw pointers.
    
- [continue](https://doc.rust-lang.org/std/keyword.continue.html "keyword std::continue")
    
    Skip to the next iteration of a loop.
    
- [crate](https://doc.rust-lang.org/std/keyword.crate.html "keyword std::crate")
    
    A Rust binary or library.
    
- [dyn](https://doc.rust-lang.org/std/keyword.dyn.html "keyword std::dyn")
    
    `dyn` is a prefix of a [trait object](https://doc.rust-lang.org/book/ch17-02-trait-objects.html)’s type.
    
- [else](https://doc.rust-lang.org/std/keyword.else.html "keyword std::else")
    
    What expression to evaluate when an [`if`](https://doc.rust-lang.org/std/keyword.if.html) condition evaluates to [`false`](https://doc.rust-lang.org/std/keyword.false.html).
    
- [enum](https://doc.rust-lang.org/std/keyword.enum.html "keyword std::enum")
    
    A type that can be any one of several variants.
    
- [extern](https://doc.rust-lang.org/std/keyword.extern.html "keyword std::extern")
    
    Link to or import external code.
    
- [false](https://doc.rust-lang.org/std/keyword.false.html "keyword std::false")
    
    A value of type [`bool`](https://doc.rust-lang.org/std/primitive.bool.html "primitive bool") representing logical **false**.
    
- [fn](https://doc.rust-lang.org/std/keyword.fn.html "keyword std::fn")
    
    A function or function pointer.
    
- [for](https://doc.rust-lang.org/std/keyword.for.html "keyword std::for")
    
    Iteration with [`in`](https://doc.rust-lang.org/std/keyword.in.html), trait implementation with [`impl`](https://doc.rust-lang.org/std/keyword.impl.html), or [higher-ranked trait bounds](https://doc.rust-lang.org/reference/trait-bounds.html#higher-ranked-trait-bounds) (`for<'a>`).
    
- [if](https://doc.rust-lang.org/std/keyword.if.html "keyword std::if")
    
    Evaluate a block if a condition holds.
    
- [impl](https://doc.rust-lang.org/std/keyword.impl.html "keyword std::impl")
    
    Implement some functionality for a type.
    
- [in](https://doc.rust-lang.org/std/keyword.in.html "keyword std::in")
    
    Iterate over a series of values with [`for`](https://doc.rust-lang.org/std/keyword.for.html).
    
- [let](https://doc.rust-lang.org/std/keyword.let.html "keyword std::let")
    
    Bind a value to a variable.
    
- [loop](https://doc.rust-lang.org/std/keyword.loop.html "keyword std::loop")
    
    Loop indefinitely.
    
- [match](https://doc.rust-lang.org/std/keyword.match.html "keyword std::match")
    
    Control flow based on pattern matching.
    
- [mod](https://doc.rust-lang.org/std/keyword.mod.html "keyword std::mod")
    
    Organize code into [modules](https://doc.rust-lang.org/reference/items/modules.html).
    
- [move](https://doc.rust-lang.org/std/keyword.move.html "keyword std::move")
    
    Capture a [closure](https://doc.rust-lang.org/book/ch13-01-closures.html)’s environment by value.
    
- [mut](https://doc.rust-lang.org/std/keyword.mut.html "keyword std::mut")
    
    A mutable variable, reference, or pointer.
    
- [pub](https://doc.rust-lang.org/std/keyword.pub.html "keyword std::pub")
    
    Make an item visible to others.
    
- [ref](https://doc.rust-lang.org/std/keyword.ref.html "keyword std::ref")
    
    Bind by reference during pattern matching.
    
- [return](https://doc.rust-lang.org/std/keyword.return.html "keyword std::return")
    
    Return a value from a function.
    
- [self](https://doc.rust-lang.org/std/keyword.self.html "keyword std::self")
    
    The receiver of a method, or the current module.
    
- [static](https://doc.rust-lang.org/std/keyword.static.html "keyword std::static")
    
    A static item is a value which is valid for the entire duration of your program (a `'static` lifetime).
    
- [struct](https://doc.rust-lang.org/std/keyword.struct.html "keyword std::struct")
    
    A type that is composed of other types.
    
- [super](https://doc.rust-lang.org/std/keyword.super.html "keyword std::super")
    
    The parent of the current [module](https://doc.rust-lang.org/reference/items/modules.html).
    
- [trait](https://doc.rust-lang.org/std/keyword.trait.html "keyword std::trait")
    
    A common interface for a group of types.
    
- [true](https://doc.rust-lang.org/std/keyword.true.html "keyword std::true")
    
    A value of type [`bool`](https://doc.rust-lang.org/std/primitive.bool.html "primitive bool") representing logical **true**.
    
- [type](https://doc.rust-lang.org/std/keyword.type.html "keyword std::type")
    
    Define an [alias](https://doc.rust-lang.org/reference/items/type-aliases.html) for an existing type.
    
- [union](https://doc.rust-lang.org/std/keyword.union.html "keyword std::union")
    
    The [Rust equivalent of a C-style union](https://doc.rust-lang.org/reference/items/unions.html).
    
- [unsafe](https://doc.rust-lang.org/std/keyword.unsafe.html "keyword std::unsafe")
    
    Code or interfaces whose [memory safety](https://doc.rust-lang.org/book/ch19-01-unsafe-rust.html) cannot be verified by the type system.
    
- [use](https://doc.rust-lang.org/std/keyword.use.html "keyword std::use")
    
    Import or rename items from other crates or modules.
    
- [where](https://doc.rust-lang.org/std/keyword.where.html "keyword std::where")
    
    Add constraints that must be upheld to use an item.
    
- [while](https://doc.rust-lang.org/std/keyword.while.html "keyword std::while")
    
    Loop while a condition is upheld.