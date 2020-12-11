### My blog

## On the evolution of programming languages

The first programming language I've learnt, as a teenager in the late '80s, was C, meaning the first programming paradigm I met was Structured Programming. I think Structured Programming was the first real abstraction from the level of CPU instructions that directly address memory locations: now you were supposed to create data structures, and write functions that manipulated them, and the compiler translated these into actual CPU instructions referring to actual memory locations.

Later on, C++ became the programming language I used most, and the evolution of C++ has always provided lot of food for thought about thinking about the kind of decisions language designers face:

* What level of compatibility do I want to maintain with existing stuff? A real trade-off between the freedom of design and the immediate availability of existing tools. I think Stroustrup's decision to remain compatible with C has been throughly discussed. Unfortunately, not I'm the only one who thinks that C++ has become a language that, as one of my colleagues put it, "I can no longer write down more than 5 lines of C++ code without having to consult the reference book."
* Do you want to enforce a certain paradigm to the developers leading to a very clear, easy-to-learn but somehow inflexible syntax (Haskell, Smalltalk), or are you rather paradigm-neutral leading to a sometimes confusingly rich (hence more difficult-to-learn) but more flexible syntax (C++)?
* What is the main objective of your langauge? What does the new language provide that its predecessors haven't? I think C++'s principles were always very clear on that front:
  * Allow and give tools for new paradigms, such as OOP, for which C provided no support, whereas:
  * Don't sacrify possible performance optimisitions done by the compiler for the sake of comfort or even safety. That's why indexing arrays, vectors, etc. is not bound-check, that's why virtual is not the default, even though you want it virtual most of the time, and also that's why the langague leaves a lot of edge cases as undefined behaviours, giving the compiler developers more freedom to optimize.

Recently, I've been trying to catch up a bit and learn about new paradigms, and to understand how programming languages evolve according to these new paradigms. I also tried to find motives, patterns behind them. What follows is my current take.

I think the vast majority of development in programming languages during the last decade can be categorized as follows:
* Compactness.  OOP clearly brought some level of verboseness to the lives of programmers, and we often find ourselves having to type dozens of lines of boilerplate for very simple things. I think languages try to become more compact in a combination of the following ways:
  * Syntactic sugar for common boilerplate patterns (C#'s null-check operator (a?.b)).
  * Types: for a while it was a real trade-off, you either had a compact or a safe language. (And we always promised that you won't use Perl for more than 100 LOC, and we always broke our rules. Real code always evolve, it's so rare that we drop a prototype and start the "real" one from scratch. I'm aware of a .sln with ~100 projects in it (with 3M+ LOC) called &lt;Something&gt;Lite.sln...) Nowadays, type inference is getting more and more advanced and widespred, so languages can get more compact without sacrifying type safety.
  * Emulate the very compact and brain-friendly unix pipe approach (C#'s LINQ, Java Stream API).
  * Replace good old / boring for-loops with the extensive use of higher-order functions (map, reduce, etc.) borrowed from functional languages.
  * Moving away from OOP -- but towards where? I think we learnt in throughout the last 2-3 decades since OOP is the major paradigm that some of its assumptions, e.g. inherence don't really fit into real world problems. Maybe it's only me, but I've never seen a clear inherence-based, polymorf solution to any real world problem, even for those cases where inherence and polymorphism seemed so natural. The problem is that clarity suffers seriously when you have to make your first special case (e.g. for performance optimisation) and you start to downcast... On the other hand, using OOP to phrase your API as interfaces seem completely ok. So what is the paradigm that will eventually replace OOP? I think we don't see a clear contenter here, only mixed approaches.
* Give language-level support to concurrency. TODO
* Support two-level programming. TODO
* Support the developers to formulate correctness-related constraints in many dimensions. TODO

It's also interesting to think about what needs the (major) programming languages didn't try to address.

When the first real programming languages (FORTRAN, COBOL, LISP, PL/1)  were designed, computers were typically operated in batches, for which a procecural approach fits very nicely. Now everything is GUI-based, event-driven rather than procedural, more real time rather than batch mode. This requires completely different paradigms, and paradigms (e.g. MVC, reactive programming) did evolve; however it's kind of amazing to me that I think these new paradigms never really got real language support (I don't cosider C#'s delegates whole-hearted language support). If you think about it, Javascript, almost exclusively used in GUI has a quite C-ish base syntax. A don't really know the reason behind this. (Obiviously it's quite possible that it's me who's simply ignorant and don't recognize these lanagauge elements.) My guess is that it's somehow related to the failure of giving a really good language support to concurrency.

