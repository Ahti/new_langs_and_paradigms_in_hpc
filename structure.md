This file contains the structure of the talk. Bullet points are in order but not
split into slides.

Bullet points prefixed by `*` are to be shown on slides. Ones prefixed with `-` are notes to the presenter.

* Definition of language and paradigm
    * Language
        * "A programming language is a formal constructed language designed to communicate instructions to a machine, particularly a computer." - Wikipedia
        * A programming language defines how you tell the computer to do something
        * Languages are closely related to their standard library
            * Boundaries are often unclear
    * Paradigm
        * "A programming paradigm is a fundamental style of computer programming, serving as a way of building the structure and elements of computer programs." - Wikipedia
        * A paradigm tells you how to approach problems/defines common patterns
        * List of paradigms from Wikipedia
            - talk a little about some common paradigms (object-oriented, functional, ...)
    * How do these two relate?
        * "Capabilities and styles of various programming languages are defined by their supported programming paradigms; some programming languages are designed to follow only one paradigm, while others support multiple paradigms." - Wikipedia
        * Most languages are written in a mix of paradigms
            * C++: object-oriented and imperative
            * C: procedural
                * people have built class systems etc.
        * Standard library may be written with a concrete paradigm in mind
            * Example: The C standard library (part of the standard) often only returns a status code from functions and returns the actual data by reference (modifying state) => quite imperative, not functional at all

* Why do we want new languages and paradigms?
    - We already know our trusty old procedural C and Fortran, why should we learn something else?
    - I will show concrete examples of these advantages later on, you'll have to trust me for now
    * Simplify development
        - simply by not having some of the complexities of c (pointers)
        - or by simplifying stuff like inter-process communication (mpi)
    * Fewer kinds of errors possible
        - Languages with a strong type system and/or memory safety guarantees can prevent whole classes of errors at compile time
    * Produces easier-to-maintain code
        * This is a result of the community surrounding the language
        * Easier to write (in a good/idiomatic manner) for inexperienced programmers
            - Lots of inexperienced programmers in HPC (scientists)
        * unit-testing
        * documentation
        - especially important in HPC because often scientists will write code and then ppl running the cluster will optimize it "as a service"
    * Better utilize available resources (esp. Accelerators)

* What problems do new languages face?
    * A large existing codebase of C/Fortran code
        * c interop makes things better
    * Smaller ecosystem of libraries/tools (esp. related to HPC)
        - think mpi
        * related to existing codebase: c interop helps here, too
    * Huge expertise of experienced programmers
        * Important, because in HPC vs application development performance is the focus, not how/what the application does
        * not really any solution except a good easy learning curve
    * C/Fortran compilers have been worked on for decades, so they can optimize code extremely well
        * solution for *some* languages: compile to c, then use c compiler

* What interesting examples are there?
    * Python (especially SciPy)
        * SciPy wraps compiled Fortran and C code, so all hotspots can be kept in a compiled language, while high-level flow can be written in Python
    * Rust
        * Memory safety and a strong type system (similar to Haskell type system)
        * Good C ffi
        * MPI bindings in development
        - side-note: Swift (which is very similar to rust in many aspects) just open sourced by apple and is gaining a lot of traction, but no mpi bindings as of yet
    * Swift/T
        * Describe the high-level flow of your program, call "leaf tasks" to do the actual work program
    * OpenMP 4
        * target construct for running on accelerators
        * simd construct for automatically utilizing simd instructions for numeric operations
