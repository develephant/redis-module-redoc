
# LibRMUtil

> __Preflight:__ Download the [RedisModulesSDK](https://github.com/RedisLabs/RedisModulesSDK).

A small library of utility functions and macros for module developers, including:

* Easier argument parsing for your commands.
* Testing utilities that allow you to wrap your module's tests as a redis command.
* `RedisModuleString` utility functions (formatting, comparison, etc)
* The entire `sds` string library, lifted from Redis itself.
* A generic scalable Vector library. Not redis specific but we found it useful.
* A few other helpful macros and functions.
* `alloc.h`, an include file that allows modules implementing data types to implicitly replace the `malloc()` function family with the Redis special allocation wrappers.

It can be found under the `rmutil` folder, and compiles into a static library you link your module against.

### An example Module

A minimal module implementing a few commands and demonstrating both the Redis Module API, and use of rmutils.

You can treat it as a template for your module, and extend its code and makefile.

**It includes 3 commands:**

* `EXAMPLE.PARSE` - demonstrating rmutil's argument helpers.
* `EXAMPLE.HGETSET` - an atomic HGET/HSET command, demonstrating the higher level Redis module API.
* `EXAMPLE.TEST` - a unit test of the above commands, demonstrating use of the testing utilities of rmutils.

### Documentation

[Read the LibRMUtil API Reference Documentation](RMUtil_API.md).

# Quick Start Guide

Here's what you need to do to build your first module:

0. Build Redis in a build supporting modules.
1. Build librmutil: `cd rmutil && make`
2. Build the example module: `cd example && make`
3. Run redis loading the module: `/path/to/redis-server --loadmodule ./example/module.so`

Now run `redis-cli` and try the commands:

```
127.0.0.1:9979> EXAMPLE.HGETSET foo bar baz
(nil)
127.0.0.1:9979> EXAMPLE.HGETSET foo bar vaz
"baz"
127.0.0.1:9979> EXAMPLE.PARSE SUM 5 2
(integer) 7
127.0.0.1:9979> EXAMPLE.PARSE PROD 5 2
(integer) 10
127.0.0.1:9979> EXAMPLE.TEST
PASS
```