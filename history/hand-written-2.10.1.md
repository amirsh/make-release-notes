We are very happy to announce the final release of Scala 2.10.1!

The Scala team and contributors [fixed 166 issues since 2.10.0](https://issues.scala-lang.org/secure/IssueNavigator.jspa?mode=hide&requestId=12114)!

In total, [242 RC1 pull requests](https://github.com/scala/scala/issues?milestone=5&page=1&state=closed), [7 RC2 pull requests](https://github.com/scala/scala/issues?milestone=13&page=1&state=closed), and [4 RC3 pull requests](https://github.com/scala/scala/issues?milestone=14&page=1&state=closed) were opened on [GitHub](https://github.com/scala/scala), of which 94.5% were merged after having been [tested](https://github.com/typesafehub/ghpullrequest-validator) and reviewed.

<!--break-->

### Known Issues
Before reporting a bug, please have a look at these [known issues](https://issues.scala-lang.org/secure/IssueNavigator.jspa?mode=hide&requestId=12113).

### Scala IDE for Eclipse
The Scala IDE with Scala 2.10.1-RC3 built right in is available through one of the following update-sites:

* [for Eclipse 3.7 (Indigo)](http://download.scala-ide.org/sdk/e37/scala210/dev/site/)
* [for Eclipse 3.8/4.2 (Juno)](http://download.scala-ide.org/sdk/e38/scala210/dev/site/) (Support for this version is experimental.)

Have a look at the [getting started guide](http://scala-ide.org/docs/user/gettingstarted.html) for more info.

### New features in the 2.10 series
Since 2.10.1 is strictly a bug-fix release, here's an overview of the most prominent new features and improvements as introduced in 2.10.0:

* Value Classes
    * A class may now extend `AnyVal` to make it behave like a struct type (restrictions apply).
    * [http://docs.scala-lang.org/overviews/core/value-classes.html](http://docs.scala-lang.org/overviews/core/value-classes.html)
* Implicit Classes
    * The implicit modifier now also applies to class definitions to reduce the boilerplate of implicit wrappers.
    * [http://docs.scala-lang.org/sips/pending/implicit-classes.html](http://docs.scala-lang.org/sips/pending/implicit-classes.html)
* String Interpolation
    * `val what = "awesome"; println(s"string interpolation is ${what.toUpperCase}!")`
    * [http://docs.scala-lang.org/overviews/core/string-interpolation.html](http://docs.scala-lang.org/overviews/core/string-interpolation.html)
* Futures and Promises
    * Asynchronously get some JSON: `for (req <- WS.url(restApiUrl).get()) yield (req.json \ "users").as[List[User]]` (uses play!)
    * [http://docs.scala-lang.org/overviews/core/futures.html](http://docs.scala-lang.org/overviews/core/futures.html)
* Dynamic and applyDynamic
    * `x.foo` becomes `x.applyDynamic("foo")` if `x`'s type does not define a `foo`, but is a subtype of `Dynamic`
    * [http://docs.scala-lang.org/sips/pending/type-dynamic.html](http://docs.scala-lang.org/sips/pending/type-dynamic.html)
* Dependent method types:
    * `def identity(x: AnyRef): x.type = x` // the return type says we return exactly what we got
* New ByteCode emitter based on ASM
    * Can target JDK 1.5, 1.6 and 1.7
    * Emits 1.6 bytecode by default
    * Old 1.5 backend is deprecated
* A new Pattern Matcher
    * rewritten from scratch to generate more robust code (no more [exponential blow-up](https://issues.scala-lang.org/browse/SI-1133)!)
    * code generation and analyses are now independent (the latter can be turned off with `-Xno-patmat-analysis`)
* Scaladoc Improvements
    * Implicits (-implicits flag)
    * Diagrams (-diagrams flag, requires graphviz)
    * Groups (-groups)
* Modularized Language features
    * Get on top of the advanced Scala features used in your codebase by explicitly importing them.
    * [http://docs.scala-lang.org/sips/pending/modularizing-language-features.html](http://docs.scala-lang.org/sips/pending/modularizing-language-features.html)
* Parallel Collections are now configurable with custom thread pools
    * [http://docs.scala-lang.org/overviews/parallel-collections/overview.html](http://docs.scala-lang.org/overviews/parallel-collections/overview.html)
* Akka Actors now part of the distribution
    * scala.actors have been deprecated and the akka implementation is now included in the distribution.
    * See the [actors migration project](http://docs.scala-lang.org/actors-migration/) for more information.
* Performance Improvements
    * Faster inliner
    * `Range#sum` is now O(1)
    * Update of ForkJoin library
    * Fixes in immutable `TreeSet`/`TreeMap`
    * Improvements to PartialFunctions
* Addition of `???` and `NotImplementedError`
* Addition of `IsTraversableOnce` + `IsTraversableLike` type classes for extension methods
* Deprecations and cleanup
    * Floating point and octal literal syntax deprecation
    * Removed scala.dbc

### Experimental features

* Scala Reflection
    * [http://docs.scala-lang.org/overviews/reflection/overview.html](http://docs.scala-lang.org/overviews/reflection/overview.html)
* Macros
    * [http://docs.scala-lang.org/overviews/macros/overview.html](http://docs.scala-lang.org/overviews/macros/overview.html)

The API is subject to (possibly major) changes in the 2.11.x series, but don't let that stop you from experimenting with them!
A lot of developers have already come up with very cool applications for them.
Some examples can be seen at [http://scalamacros.org/news/2012/11/05/status-update.html](http://scalamacros.org/news/2012/11/05/status-update.html).