
## Table of Contents

- [C++](#C++)
  - [Abstracted virtual machine calls for JIT compiler operations](#abstracted-virtual-machine-calls-for-jit-compiler-operations)
  - [CacheIR support for String + Boolean](#cacheir-support-for-string-+-boolean)
  - [Collapse ICCacheIR_UpdatedStub into ICUpdatedStub](#Collapse-ICCacheIR_UpdatedStub-into-ICUpdatedStub)
  - [Optionally flush CacheIR spew more frequently](#Optionally-flush-CacheIR-spew-more-frequently)
- [JavaScript](#JavaScript)
  - [Weed site Google Maps API integration](#Weed-site-Google-Maps-API-integration)
  - [cacheIR_analyzer when finished with patch](#cacheIR_analyzer-when-finished-with-patch)
  - [Network tab protocol column shows "HTTP/2.0+h2" when individual requests are selected ](#Network-tab-protocol-column-shows-"HTTP/2.0+h2"-when-individual-requests-are-selected)
- [Rust](#Rust)
  - [Cranelift: Unifying `wasm` and `compiler` subcommand output](#Cranelift:-Unifying-`wasm`-and-`compiler`-subcommand-output)
  - [Cranelift: Verifier issue](#Cranelift:-Verifier-issue)
- [Python](#Python)
  - [Endpoint API project](#Endpoint-API-project)
- [HTML/CSS/React/other front end](#HTML/CSS/React/other-front-end)
  - [Edit and Resend should use proper styling for input fields ](#Edit-and-Resend-should-use-proper-styling-for-input-fields)
  - [The Old Try front end changes](#The-Old-Try-front-end-changes)
  - [Debugger svg change](#Debugger-svg-change)
  - [Unfinished debugger accessibility issue](#Unfinished-debugger-accessibility-issue)

## C++

### [Abstracted virtual machine calls for JIT compiler operations](https://bugzilla.mozilla.org/show_bug.cgi?id=1467191)

Some operations shared between stubs of the Just-In-Time (JIT) compilers of
SpiderMonkey, IonMonkey and Baseline, only differed in their implementions of
entering and leaving their respective stub frames. This project created a wrapper
class in the base class JIT stub compiler that unified IonMonkey and Baseline compiler
methods implementing these operations.

### [CacheIR support for String + Boolean](https://bugzilla.mozilla.org/show_bug.cgi?id=1492995)

[CacheIR](https://jandemooij.nl/blog/2017/01/25/cacheir/) is a bytecode that creates Inline Cache (IC) stubs that SpiderMonkey
uses to optimize certain operations. This project added support for String plus Boolean
binary arithmetic as defined by EMCAScript 6 to the CacheIR.

### [Collapse ICCacheIR_UpdatedStub into ICUpdatedStub](https://bugzilla.mozilla.org/show_bug.cgi?id=1493189)

A CacheIR version of a stub kind class had completely subsumed the base class.
In this project, I collapsed the two together to address the redundant distincion
in classes. This project involved integrating changes seamlessly in the larger
SpiderMonkey ecosystem. Careful attention was paid to packing the member fields
of the resulting class based on alignment in memory in order to optimize memory
usage.

### [Optionally flush CacheIR spew more frequently](https://bugzilla.mozilla.org/show_bug.cgi?id=1451591)

CacheIR logs of IC stubs can be emitted as JSON for debugging purposes by setting an environment
variable. Crashes during log emitting caused the logs to be truncated, making
troubleshooting difficult. For this project, I altered the flushing behavior of the logs,
so that in the event of a crash the logs are not truncated. Additionally, I implemented
a feature whereby frequency of log emission can be controlled with an environment variable,
enabling a developer to alter log emission frequency as needed.

## JavaScript
### [Embedded Google Map and Maps API integration]()

Retrieved data from Google Sheets document as JSON, and used this data to form an array of objects
that is used to populate a Google Maps Map with markers.

Used Google Maps Geocoder API and Autocomplete API to implement a location search. The user
enters an address and a search radius, and the map pans to the user's given location. If there
are locations from the array made above within the provided search radius, the map will resize
it's bounds to show the locations that are within the radius.

### [cacheIR_analyzer when finished with patch]()

This is a patch for a JQuery script written by a SpiderMonkey developer. The script analyzes
JSON of CacheIR IC logs, and injects data into an HTML page. CacheIR instruction sequence bytecode
was added to the creation of CacheIR IC logs after the creation of this script. My patch adds
support for CacheIR instruction sequence bytecode to the script.

### [Network tab protocol column shows "HTTP/2.0+h2" when individual requests are selected ](https://bugzilla.mozilla.org/show_bug.cgi?id=1501357)

In the Network tab of FireFox's Devtools, HTTP protocol values were erroneously being displayed with
the `x-firefox-spdy` prodocol values appended, e.g. `HTTP/2.0+h2` when the appropriate protocol value
would be `HTTP/2.0`. I altered the JavaScript which determined the rendering of HTTP protocol values
so that matching `x-firefox-spdy` values would not be displayed, and added a test for this change
to the testing framework used for Devtools' JavaScript.

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

