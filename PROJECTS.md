
## Table of Contents

- [C++]()
  - [Abstracted virtual machine calls for JIT compiler operations]()
  - [CacheIR support for String + Boolean ]()
  - [Collapse ICCacheIR_UpdatedStub into ICUpdatedStub ]()
  - [Optionally flush CacheIR spew more frequently ]()
- [JavaScript]()
  - [Weed site Google Maps API integration]()
  - [cacheIR_analyzer (when finished with patch)]()
  - [Network tab protocol column shows "HTTP/2.0+h2" when individual requests are selected ]()
- [Rust]()
  - [Cranelift: Unifying `wasm` and `compiler` subcommand output]()
  - [Cranelift: Verifier issue]()
- [Python]()
  - [Endpoint API project]()
- [HTML/CSS/React/other front end]()
  - [Edit and Resend should use proper styling for input fields ]()
  - [The Old Try front end changes]()
  - [Debugger svg change]()
  - [Unfinished debugger accessibility issue]()

## C++

### [Abstracted virtual machine calls for JIT compiler operations]()

Some operations shared between stubs of the Just-In-Time (JIT) compilers of 
SpiderMonkey, IonMonkey and Baseline, only differed in their implementions of
entering and leaving their respective stub frames. This project created a wrapper
class in the base class JIT stub compiler that unified IonMonkey and Baseline compiler
methods implementing these operations. 

### [CacheIR support for String + Boolean]()

[CacheIR]() is a bytecode that creates Inline Cache (IC) stubs that SpiderMonkey
uses to optimize certain operations. This project added support for String plus Boolean
binary arithmetic as defined by EMCAScript 6 to the CacheIR.

### [Collapse ICCacheIR_UpdatedStub into ICUpdatedStub]()
### [Optionally flush CacheIR spew more frequently ]()

## JavaScript
### [Weed site Google Maps API integration]()
### [cacheIR_analyzer (when finished with patch)]()
### [Network tab protocol column shows "HTTP/2.0+h2" when individual requests are selected ]()

## Rust
### [Cranelift: Unifying `wasm` and `compiler` subcommand output]()
### [Cranelift: Verifier issue]()

## Python
### [Endpoint API project]()


## HTML/CSS/React/other front end
### [Edit and Resend should use proper styling for input fields ]()
### [The Old Try front end changes]()
### [Debugger svg change]()
### [Unfinished debugger accessibility issue]()

