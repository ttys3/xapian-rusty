# xapian-rs

[![crates.io](https://badgen.net/crates/v/xapian)](https://crates.io/crates/xapian)
[![docs](https://badgen.net/static/docs/passing/green?icon=github)](https://ttys3.github.io/xapian-rs/xapian/)
![downloads](https://badgen.net/crates/d/xapian)
![latest version downloads](https://badgen.net/crates/dl/xapian)

xapian bind for rust

## honey backend status

> The remaining blockers for this are:

* adding update support to the new honey backend (to replace glass)
* adding support for RAM storage to honey (to replace inmemory)
* moving some remote client and server code out of libxapian (or
  replacing it)

## crate maintainers docs

xapian github repo: https://github.com/xapian/xapian

User guide online: Getting Started with Xapian https://getting-started-with-xapian.readthedocs.io/

the Xapian developer guide https://xapian-developer-guide.readthedocs.io/

https://xapian.org/docs/

new version news: https://lists.xapian.org/pipermail/xapian-discuss/2023-March/009961.html

xapian api docs: https://xapian.org/docs/apidoc/

## rust binding

cxx tuts https://cxx.rs/tutorial.html

autocxx book https://google.github.io/autocxx/

## performance

32bit docid

```
doc count: 31944, index doc took: 6251ms
```

## troubleshooting

```
terminate called without an active exception

Process finished with exit code 134 (interrupted by signal 6: SIGABRT)
```

solution:

do not use  `Error e` in `rust::behavior::trycatch` C++ code, use `const Xapian::Error& e` instead.

reason:

`Error` is defined in generated `target/cxxbridge/rust/cxx.h` file under `rust` namespace.

use `Xapian::Error` will fix the problem.

## xapian debug

HACKING: `XAPIAN_DEBUG_LOG=-` send output to stderr, not stdout.

`XAPIAN_DEBUG_FLAGS`