---

layout: col-sidebar
title: OWASP aegis4j
tags: java security java-agent devsecops
level: 2
type: code
pitch: A Java agent that disables platform features you don't use, before an attacker uses them against you.

---

Avoid the NEXT Log4Shell vulnerability!

The Java platform has accrued a number of features over the years. Some of these features are no longer commonly used,
but their existence remains a security liability, providing attackers with a diverse toolkit to leverage against
Java-based systems.

It is possible to eliminate some of this attack surface area by creating custom JVM images with
[jlink](https://docs.oracle.com/en/java/javase/17/docs/specs/man/jlink.html), but this is not always feasible or desired.
Another option is to use the [--limit-modules](https://docs.oracle.com/en/java/javase/17/docs/specs/man/java.html) command
line parameter when running your application, but this is a relatively coarse tool that cannot be used to disable
individual features like serialization or native process execution.

A third option is aegis4j, a Java agent which can patch key system classes to completely disable a number of standard
Java features:

- `jndi`: all JNDI functionality (`javax.naming.*`)
- `rmi`: all RMI functionality (`java.rmi.*`)
- `process`: all process execution functionality (`Runtime.exec()`, `ProcessBuilder`)
- `httpserver`: all use of the JDK HTTP server (`com.sun.net.httpserver.*`)
- `serialization`: all Java serialization (`ObjectInputStream`, `ObjectOutputStream`)
- `unsafe`: all use of `sun.misc.Unsafe`
- `scripting`: all JSR 223 scripting (`javax.script.*`)
- `jshell`: all use of the Java Shell API (`jdk.jshell.*`)

For more information, see the [GitHub repository](https://github.com/gredler/aegis4j).
