# Neutrino

A lightweight, zero-abstraction runtime for desktop applications.

Neutrino consists of a default set of C libraries and Javascript bindings for them so developers can write applications using Javascript and/or C. The following libraries are planned:

* [x] [GLFW](https://www.glfw.org) (Desktop OpenGL support)
  * [ ] bindings via [duk-glfw](https://github.com/lzubiaur/duk-glfw)
* [ ] [Nuklear](https://github.com/vurtun/nuklear) (GUI)
  * [ ] bindings
* [ ] [libcurl](https://curl.haxx.se/libcurl/) (http/s, network support)
  * [ ] bindings via [dukcurl](https://github.com/creationix/dukcurl)
* [ ] [SQLite](https://sqlite.org/index.html) (client-side database)
  * [ ] bindings (previous work: [sqlite-js](https://github.com/abiliojr/sqlite-js), [duklite](https://github.com/fasterthanlime/duklite))
* [ ] [stb_image](https://github.com/nothings/stb) (image loading)
  * [ ] bindings
* [ ] [GLFM](https://github.com/brackeen/glfm) (Mobile OpenGL support)

## Duktape Javascript Engine

Neutrino embeds the [duktape](https://duktape.org) javascript engine because it is easier to compile and easier to integrate with than complex engines like v8, yet it has robust support for ECMAScript 5 and partial support for ECMAScript 6+. We intentionally opted for a simpler non-JIT engine because we believe that the overall performance and maintainability of the application stack is better when performance-critical routines are written in C and when application developers understand the performance characteristics and tradeoffs of low-level code.

## Library Goals

Users should be able to easily:

* remove libraries they don't want (by not including the DLL? or not setting compile macro flags?)
* add alternative libraries (alternative GUI, DB, etc) by dropping in a C library and writing duktape bindings
* update libraries by dropping in an updated version of the dynamic library (to patch bugs and security vulnerabilities)
