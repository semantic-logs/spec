# Semantic Logs

## Summary 

Today, there are many log encodings. This creates O(nm) cost and complexity parsing and processing log files. Every log encoding (n) multiplied by the number of log processing product (m).

To manage this we introduce two concepts. Firstly, **structured logs** allows parsing of logs into general key-value entries. That allows both humans and machines to understand the **syntax** of log entries. Then a specialization of structured logs we call **semantic logs** gives clear meaning to key-values pairs that allows both humans and machine to perform unambiguous analysis and processing of generalised log entries. 

By standardising, it becomes orders of magnitude easier to build tools for common use cases:

* Log viewing
* Log analytics
* Distributed tracing
* Security analysis

Structured logs are logs where each entry has context free syntax. A counter example would be a CSV file. Fields within records within a CSV file can only be understood within the context of the headers. Conversely, JSON object values can be understood by examining the keys. 

Logs entries are events, but events are not entries. 

## Structured, Patterned, Free-Text Logs

Today, you'll commonly see three types of logs:

* **Structured** each entry is made up of key-value pairs, e.g. `foo=true bar=1 baz="qux"`, also know as  `logfmt`. These logs can be parsed into structure only knowing they're structured.
* **Patterned** each entry is a formatted line of text, e.g. `[true] [1] qux`. These logs cannot be parsed into structure without knowing (a) they are patterned and (b) the pattern. Some patterned logs cannot be parsed into structure.
* **Free-text** arbitrary text. These logs cannot be parsed into structure.

## Log Context

Logs are always created by a process and therefore never created without context, e.g.

* The hostname of the process.
* The PID.
* The process name.
* The process namespace.

