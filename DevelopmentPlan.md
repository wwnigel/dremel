The page describes top-level development plan for the project. It consists from milestones. As project progresses at milestones are achieved new milestones will be set. The ultimate goal of the project is to provide completely free and truly open-source system that implements Google's BigQuery service taking into account all information that will be published by Google starting from Dremel paper.

  1. **Metaxa** - functionally complete implementation of all published BigQuery features and according to Dremel paper. The performance goal is **1MB/sec** on average desktop machine. The accent is to be made on producing a validated and well tested functional implementation rather than premature-optimization. It may be a single java application running in single JVM, albeit heavily multi-threaded to model parallelism. Also special effort must be made to make the code as clear and as readable as possible. _Metaxa_ will be used later as functional prototype for future performance-obsessed versions. _Metaxa_ consists of following components:
    1. Front-end: Console java application including simple ANTLR-based parser for BQL language.
    1. Execution-engine: an interpreter for query semantic model (BQL is parsed and turned into object-graph called semantic model).
    1. Data converter from hierarchal model to Dremel columnar model and back. For hierarchal model we use Avro.
    1. comprehensive test suite is an important component.
  1. **Glenmorangie** - performance efficient _Metaxa_. The goal is to get **1GB/sec** user data throughput on modern powerful desktop machine for average query. Following changes will be made to _Metaxa_ to achieve stated performance goal:
    1. Switch from interpretation to compilation and subsequent execution of it in massively parallel manner.
    1. Selection of the intermediate language. One of following: Simplified Java (without memory allocations in the inner loop), C with LLVM, portable assembly with LLVM
    1. If proven necessary multi-JVM approach must be used to exploit all the available parallelism on hardware, especially multi-socket servers.
    1. Performance aside, additional or improved functional features will be introduced. For example following BigQuery site update or some information regarding it or publishing of new academic papers on the topic.
  1. **Drambuie** - distributed/clustered version. Performance goal of **10GB/sec** on small cluster of commodity servers.
    1. The size of cluster to be supported and all the rest of to-be-implemented functionality is TBD