# Commands and Scripts of ImageJ/SciJava

## ImageJ's Architecture

Scijava is the fundmendation of ImageJ. ImageJ's functionality was divided into several services, including:

- plugin
- module
- log
- status
- menu
- …...

## Modules: Commands and Scripts

`Script` is kind of plugin written in any available SciJava Scripting Language. For now, the supportted script language includes: Groovy, ImageJ Macro, Python (JPython), JavaScript, Ruby (JRuby), Lisp (Clojure), R (Renjin), Java, MATLAB, BeanShell, Scala (experimental). For more details, please see [this page](https://imagej.net/Scripting).

Whereas, a `command` is plugin written in Java (now in ImageJ2 Kotlin was supported). Compare to a script, a command is more verbose, but there also has its own advantages: higher performance, typed, IDE supports, etc. **Now with Kotlin landed**, writting a command for ImageJ2 become more easier than before.

We will discuss about implementing ImageJ2 commands with Kotlin later.