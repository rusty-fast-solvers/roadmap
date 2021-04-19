# rusty-fast-solvers Roadmap

The purpose of **rusty-fast-solvers** is to create an infrastructure for the development of fast integral
equation solvers around the Rust Programming Language and Python.

This repository is meant to host open discussions around the project.


### Goals of the project

We want to build up a fast direct solver infrastructure for boundary integral equations arising from
Green's fct. representations of problems in acoustics, electrostatics and electromagnetics. The goal
is to build a unified approach for the fast forward evaluation of operators and the design of approximate inverses.

The mathematical techniques to build on are

* Representation of far-field transformations by expansions into fundamental solutions, similar to the Kernel-Independent FMM
* Compression of operators using algebraic techniques, such as randomised methods and adaptive-cross-approximation
* Representations of operators in the form A = P_1 G _ P2, where A is the integral operator, G is the point-to-point evaluation of the Green's fct. and P_1 and P_2 are sparse matrices that e.g. map to function spaces. We want to build fast forward evaluators for G, and take the product structure into account to build fast approximate inverses for A.

### Development environment

We are planning all developments to use Rust for low-level components and Python for high-level interfaces. Why Rust and not C++? While Rust is a young language, it has backing from major companies and numerical tools in Rust are quickly maturing. Rust throughout uses high-level concepts that allow a productive pace of development. The ``cargo`` package manager and the module system mean that complex CMake files are not necessary any more and projects can easily be ported between Windows, Mac, and Linux. Rust has excellent threading support and well-working auto-vectorization. It is very easy to build Python interfaces without complex build scripts, making productive integrated development between Python and Rust straight forward.

### Planned subprojects

An important concept is a very fine-grained separation of concerns. The following subprojects are in planning.

* **rusty-green-kernel** A low-level library to allow the fast direct evaluation of particle interactions between sources and targets
* **rusty-tree** Clustering algorithms such as Octrees and H-Matrix type ClusterTrees
* **rusty-compression** Implementation of low-rank-compression tools
* **rusty-translation** Translation of low-rank expansions of fields (e.g. M2L, L2L, operators)
* **rusty-fmm** Full forward FMM implementation
* **rusty-inverse** Representations of approximate inverses



