[Go at Google: Language Design in the Service of Software Engineering](https://talks.golang.org/2012/splash.article)

>  The computing landscape today is almost unrelated to the environment in which the languages being used, mostly C++, Java, and Python, had been created. The problems introduced by multicore processors, networked systems, massive computation clusters, and the web programming model were being worked around rather than addressed head-on. 

large scale software development pain points.

* slow builds
* uncontrolled dependencies
* each programmer using a different subset of the language
* poor program understanding (code hard to read, poorly documented, and so on)
* duplication of effort
* cost of updates
* version skew
* difficulty of writing automatic tools
* cross-language builds

> Sidenote: Dependencies in C and C++
> Outside of Plan 9, though, the "guarded" approach is accepted practice for C and C++. In fact, C++ exacerbates the problem by using the same approach at finer granularity. By convention, C++ programs are usually structured with one header file per class, or perhaps small set of related classes, a grouping much smaller than, say, <stdio.h>. The dependency tree is therefore much more intricate, reflecting not library dependencies but the full type hierarchy. Moreover, C++ header files usually contain real code—type, method, and template declarations—not just the simple constants and function signatures typical of a C header file. Thus not only does C++ push more to the compiler, what it pushes is harder to compile, and each invocation of the compiler must reprocess this information. When building a large C++ binary, the compiler might be taught thousands of times how to represent a string by processing the header file <string>. (For the record, around 1984 Tom Cargill observed that the use of the C preprocessor for dependency management would be a long-term liability for C++ and should be addressed.)
> 
> The construction of a single C++ binary at Google can open and read hundreds of individual header files tens of thousands of times. In 2007, build engineers at Google instrumented the compilation of a major Google binary. The file contained about two thousand files that, if simply concatenated together, totaled 4.2 megabytes. By the time the #includes had been expanded, over 8 gigabytes were being delivered to the input of the compiler, a blow-up of 2000 bytes for every C++ source byte.

Go embodies a variant of CSP with first-class channels.

> Don't communicate by sharing memory, share memory by communicating.

Go was designed to address a set of software engineering issues that we had been exposed to in the construction of large server software. Offhand, that might make Go sound rather dull and industrial, but in fact the focus on clarity, simplicity and composability throughout the design instead resulted in a productive, fun language that many programmers find expressive and powerful.

The properties that led to that include:

* Clear dependencies
* Clear syntax
* Clear semantics
* Composition over inheritance
* Simplicity provided by the programming model (garbage collection, concurrency)
* Easy tooling (the go tool, gofmt, godoc, gofix)

[Go interfaces](http://research.swtch.com/interfaces)
