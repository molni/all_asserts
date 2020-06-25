# all_asserts [![Build Status](https://travis-ci.org/ohsayan/all_asserts.svg?branch=master)](https://travis-ci.org/ohsayan/all_asserts) [![all_asserts crate](https://img.shields.io/crates/v/all_asserts.svg?style=flat-square)](https://crates.io/crates/all_asserts) [![Crates.io](https://img.shields.io/crates/d/all_asserts.svg?color=%234527A0)](https://crates.io/crates/all_asserts) [![license](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](./LICENSE)
### A crate for multiple types of asserts that don't exist in the standard library
# Rationale
There are several kinds of problems that I had faced while writing tests, especially when writing comparator tests.
The output from the existing macros, were providing _vague_ outputs while debugging which made me write this crate.
I had created an RFC, but neverthless it was rejected as there were not enough use cases. I am not too sure about others, but I find myself writing multiple tests that make use of these asserts.

# Importing and using
Add these lines to your rust application:
```rust
#[macro_use]
use all_asserts;
```
And now you can use the asserts wherever you like!

An example using `assert_range!`:
```
use all_asserts::assert_range;
fn main() {
    assert_range!((10..20), 20);
}
```
This outputs something like:
```
thread 'main' panicked at 'assertion failed: 
`20 is not in range of 10..20` : it should have been in this range
```

An example using `assert_lt!`:
```
thread 'main' panicked at 'assertion failed: `(left < right) but here (left >= right)`
  left: `100`,
 right: `200`', src/main.rs:79:5
```
Isn't that much better than what the current macros provide? Well, I'll leave you to decide!

# Usage of the macros
The name of the assert pretty much tells you everything:
- `assert_gt!(a, b)` -> Will panic if a is not greater than b
- `assert_ge!(a, b)` -> Will panic if a is not greater than or equal to b
- `assert_lt!(a, b)` -> Will panic if a is not less than b
- `assert_le!(a, b)` -> Will panic if a is not greater than or equal to b
- `assert_range((x..y), b)` -> Will panic if b is not within the range [x, y)
- `assert_nrange((x..y), b)` -> Will panic if b is within the range [x, y)

# Building

Simply run:
```shell
$ git clone https://github.com/ohsayan/all_asserts.git
$ cd all_asserts
$ cargo build
```
And for testing:
```shell
$ cargo test
```

# Contributing
Your welcome to! 
> "No man is an island!"

And I always stick to that belief! Please help me out in better formatting the output to make debugging easier. If you find an issue, go ahead a create one! (All doubts, questions and ideas are welcome)

# License
This project is licensed under the Apache-2.0 License.