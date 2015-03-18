The Co-dfns compiler continues to evolve at a rapid pace, with significant components rewritten often as new techniques and solutions present themselves. The following projects give an idea of the roadmap for Co-dfns moving forward and especially for the near term improvements planned for the compiler.

We are working closely with industry partners through Dyalog, Ltd. to develop benchmarks and implementations of end-user code directly from the code bases of current Dyalog APL customers. This will allow us to not only examine Co-dfns from the perspective of traditional micro-benchmarks, but also give us a host of ready-to-use real life applications, which often diverge from micro-benchmarks in interesting ways.

We actively examine new programming methods and approaches for constructing the compiler. In particular, the next version will be using a Functional Relational Programming model which maps nicely onto the data-parallel infrastructure of the compiler. The use of this model provides a number of interesting optimizations at a very low cost to us. It remains to be seen whether it will provide enhancements to the general structure and clarity of the code base.

Work by Lenore Mullin [citation] provides a firm base from which to develop a hybrid verification/type system on top of APL. A number of type systems have been created in industry [citation] and academia [citation] to type APL code of various forms. Our audience for such a type system is the information experts themselves, coupled with the tuning expert, which presents interesting challenges in its design. We have preliminary models of such a type system, but no working implementation as yet.

The construction of programs in the branchless, recursion-less style of the compiler exposes a side-benefit that will be integrated into the compiler at a later date. Namely, with the simple control flow and well understood primitives, it is possible to automatically derive a worst-case performance model from the code without complex analysis. This allows us to obtain worst-case performance metrics about the runtime complexity of the compiler as well as memory usage automatically. We plan to integrate this feature into the compiler itself, so that the information expert can receive an automatic analysis of the runtime complexity of any program run through the compiler without requiring hand-working the solution. 

The next optimizations which have revealed themselves as vitally important to improved imperformance are traditional constant propagation and folding. The compiler right now introduces overheads for each constant value in scalar computations which should not be there, sometimes interacting poorly with the vectorization engines of the underlying C compiler. Constant propagation and folding fixes this issue nicely.

Finally, it is possible for us to almost completely eliminate runtime type checking of most of the variables in code like Black Scholes through type inference, allowing us to dispatch early on the argument types and greatly reducing the generated C code both in size and complexity. This of course has obvious benefits to the runtime performance, but especially in terms of compile times and compiled object size.