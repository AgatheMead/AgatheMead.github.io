---
layout: post
title: Linear Programming
---

## Optimization techniques
Linear programming (LP) is a powerful method used to solve optimization problems( e.g. shortest paths, maxflow, bipartite matching, and many, many more) subject to linear constraints, and has been applied in a wide variety of situations and contexts.
Linear transformations are almost the most intutive process for our sense. However in reality we are constrainted by the limited availability of resources. The methods of linear programming were originally developed between 1945 and 1955 by American mathematicians. At that time when President Truman took office in 1945, the disorderly postwar reconversion of the economy of the US was marked by severe shortages of many goods^{3}. And the US was hit by long strikes in major industries in 1946. Problems such as workforce constraints and raw material quantities arose in industry and economic planning. The simplest problems having two variables in them can be solved graphically. However, problems occuring in industry have a lot more variables leading to even more constraints, and such problems have to rely on computers to free our hands.

![Linear prgramming in 2D: feasible region bounded by the constraint set.](https://b7.pngbarn.com/png/336/272/linear-programming-feasible-region-simplex-algorithm-optimization-problem-mathematical-optimization-mathematics-png-clip-art.png "Linear prgramming in 2D: feasible region bounded by the constraint set.")

## Solvers
Basic LP problem can be described in standard form.

![The maximal/minimal value of a given objevtive function is usually found within corner points.](https://res.cloudinary.com/dyd911kmh/image/upload/f_auto,q_auto:best/v1563200754/image1_dg9p0t.png "The maximal/minimal value of a given objevtive function is usually found within corner points.")

- The objective function to be optimized. 
- The set of feasible vectors is called the constraint set expressed in the form of linear (in)equations.
- A LP problem is feasible if the constraint set is not empty, otherwise it is infeasible. 
- Any setting of values satisfying all constraints is a feasible solution.

### Simplex method
General process for solving linear programming is to form the feasibility region using linear inequalities (or called constraints). Within the feasibility region all inequalities are satisfied. Then we figure out the coordinates of the corners of this region and test out maximum/minimum. 
_Simplex method_ is the first algorithm for solving LP problems proposed by George Dantzig back in 1947, shortly after WWII, in response to logistical problems. In practice, the simplex method exhibits linear complexity. The worst case complexity is _O(m+n)_, where _n_ and _m_ denote the number of variables and the number of constraints, respectively. Starting somewhere along the edge of the feasible region, and pivoting from one feasible solution to another, at each step improving the value of the objective function (never decreasing objective function), and at final terminating in a finite number of such transitions.

![Workflow of simplex method for solving linear programs. For the simplex algorithm, it is more convenient to work with equality constraints. In slack form, all constraints except for the non-negativity constraints are equalities^{6}.](/images/simplex.png "Workflow of simplex method for solving linear programs. For the simplex algorithm, it is more convenient to work with equality constraints. In slack form, all constraints except for the non-negativity constraints are equalities^{6}.")

To further boost the efficiency of the simplex method, George Dantzig and W.Orchard-Hays revised the previous work and proposed the revised version in 1953^{8} by adding the details of computing the entering variables and departing variables.

### Dual simple algorithm
Every LP problem (primal problem) has a coinside LP problem as its dual. If the primal problem is a minimization problem, then its dual is a maximization problem and vice versa. Any feasible solution to dual is an upper bound to primal, and any feasible solution to primal is a lower bound to dual. The dual can help to provide a bound to difficult primal problems. However, the dual simplex method try to find an optimal solution to the primal as early as it can, regardless the feasibility of the solution. It then moves vertex-by-vertex, gradually decreasing the infeasibility while maintaining optimality. It terminates when an optimal feasible solution to the primal problem is found. 

![Workflow of dual simple algorithm for solving linear programs.](https://image.slidesharecdn.com/5-161104024002/95/5-advance-topics-in-lp-23-638.jpg?cb=1478227274 "Workflow of dual simple algorithm for solving linear programs.")

### Interior-point method
Researchers have long tried to develop solutions whose worst case running times are polynomial functions of the problem size. In 1984, Karmarkar proved that LP problems could be solved with polynomial-time complexity^{12}. _Interior-point method_, the primary alternative to the simplex method, traverses the interior of the feasible set of solutions, have benefited significant from the power of computers. Instead of simplex methods that searching from vertex to vertex along the edges, interior-point methods go through the inside of the feasible space.

![Workflow of interior-point method for solving linear programs.](https://ars.els-cdn.com/content/image/3-s2.0-B9780123743640500114-f04-35-9780123743640.jpg "Workflow of interior-point method for solving linear programs.")

Year | Method
-----|----------------
1939 | Production planning <a href="Cockshott, W.P., 2007. Mises, Kantorovich and economic computation."> [15] </a>
1947 | Simplex algorithm <a href="https://dl.acm.org/doi/pdf/10.1145/87252.88081"> [16] </a>
1950 | Applications in many fields
1953 | Revised simplex algorithm <a href="https://www.jstor.org/stable/pdf/2001993.pdf?casa_token=N-CDFqaQNZcAAAAA:u39iXQVnMmdxbHEC-F3D29V3gHIPK3CVBodVefetwp9PNjbk-ubs3u51ZL0QateDiB5EWFP_fQMpmU7RCQCxiU0Bq6meC5H1whXPpkH4xhwI3iswxg"> [10] </a>
1979 | Ellipsoid algorithm <a href="http://www.mathnet.ru/php/archive.phtml?wshow=paper&jrnid=dan&paperid=42319&option_lang=eng"> [11] </a>
1984 | Projective scaling algorithm <a href="https://dl.acm.org/doi/pdf/10.1145/800057.808695?casa_token=ThgrXzQ45P0AAAAA:HQfiJjruARaKrGGX2IspgLWhOmDxMR8VOQttBXVOMowirC0E03N3OTfEHc7PKMSS5v6HkmWU72M"> [12] </a>
1990 | Interior-point method <a href="https://www.jstor.org/stable/pdf/43692347.pdf?casa_token=1do21YAIkNsAAAAA:oiqrxoiYlYJ89Nw4vTj3DIuzvVkNotv1xd9mwA3OlhowJ3EB8u9_MTQvrwSAl-TLX3QB67cvhWOy6PWKDAZuoActoA7h9y-g6tDSpjTssYnq6L8llQ"> [13] </a> <a href="https://www.researchgate.net/profile/Akiko_Yoshise/publication/234810405_A_Primal-Dual_Interior_Point_Algorithm_for_Linear_Programming/links/0c960526a79f5f2ab2000000/A-Primal-Dual-Interior-Point-Algorithm-for-Linear-Programming.pdf"> [14] </a>
-----|----------------

### Implementations
Many practical problems can be easily formulated as LPs. Nowadays, many commercial solvers, e.g. CLP, GLPK, Google Cloud, and GUROBI, etc., provide us matual implementations for LP issues. It is interesting that different implementations of the well-established LP result in wide performance and robutness variations. To explain such wide disparities between different implementations, we will look into three factors. 

-*Sparse Linear Algebra*   The constraint matrices in LP are typically sparse, containing very few non-zero entries. Both the simplex method and interior-point method need to handle with factored sparse matrices/vectors. It takes years of experience in sparse numerical linear algebra and linear programming to understand the computational issues associated with building efficient sparse matrix algorithms for LP^{2}.
-*Numerical Errors*   Linear equations are solved in finite-precision arithmetic, thus slight numerical errors in the results are inevitable. Designing effective strategies for managing such errors is a crucial part of building LP algorithms.
-*Heuristic Strategies*   For examples, simplex method repeatly pick one variable to enter the basis. The strategies for choosing variables have a profound effect on the runtime of the algorithm. 

## Integer linear programming
The LP algorithms disscussed above have been continuous in the sense that decision vaariables are allowed to be fractional. However, fractional solutions are not always realistic, for example the number of some production cannot be fractional. In many setting the term Interger programming is said to be a mixed integer linear programming (MILP) when some of the variables are restricted to be integer. 
> NP-completeness. 
>> P: Class of decision problems that can be solved in polynomial-time.
>> NP: Decision problems where at least the YES-instances have polynomial-time proofs that the answer is YES.
>> NP-complete: Problems cannot be solved by polynomial-time algorithms. 

The bad news is: integer linear programming is NP-complete. During the past decade, there appeared many articles using LP to solve NP-complete problems, however the usage of LP for polynomial solutions of NP-complete problems, especially for large instances, cannot be met^{17, 18}. 

### Linear programming relaxation
The relaxiation of a MILP is to remove the integrality constraint of each variable. The resulting relaxiation is a linear program, and it is like we transform an NP optimization problem into a decision problem that can be solved in polynomial time. The solution to the relaxed linear program can be used to gain information about hte solution to the original integer program. 

![A general integer program and its LP-relaxation from wiki.](https://upload.wikimedia.org/wikipedia/commons/thumb/0/06/IP_polytope_with_LP_relaxation.svg/1280px-IP_polytope_with_LP_relaxation.svg.png "A general integer program and its LP-relaxation from wiki.")

## Takeaways
- LP touches nearly every field in some way, providing solutions from scheduling to optimization. 
- The simplex method is one of the greatest and most successful algorithms of all time.
- Different implementations of LP might result in wide disparities performance and robutness.
- In reality, LP problems might have additional constraints when some variables are restricted to be integer.

## Links
[1] Vanderbei, R., Linear Programming: Foundations and Extensions, 2010

[2] https://www.gurobi.com/resource/linear-programming-basics/

[3] https://en.wikipedia.org/wiki/History_of_the_United_States_(1945–1964)

[4] https://www.math.ucla.edu/~tom/LP.pdf

[5] http://web.mit.edu/15.053/www/AMP-Chapter-02.pdf

[6] https://www.cl.cam.ac.uk/teaching/1617/AdvAlgo/lp.pdf 

[7] V. Klee and G.J. Minty, "How Good is the Simplex Algorithm" In O. Shisha, editor, Inequalities, III, pages 159-175. Academic Press, New York, NY, 1972.

[8] Dantzig, G.B., 1953. Notes on Linear Programming—Part III: Computational Algorithm of the Revised Simplex Method.

[9] Dantzig, G.B. and Orchard-Hays, W., 1953. Notes on Linear Programming: Part V Alternate Algorithm for the Revised Simplex Method Using a Product Form for the Inverse.

[10] Dantzig, G.B. and Orchard-Hays, W., 1954. The product form for the inverse in the simplex method. Mathematical Tables and Other Aids to Computation, pp.64-67.

[11] L.G. Khachian, A Polynomial Algorithm for Linear Programming, Soviet Mathematics, Doklady 20/1 (1979). http://www.mathnet.ru/php/getFT.phtml?jrnid=dan&paperid=42319&what=fullt&option_lang=eng

[12] Karmarkar, N., 1984, December. A new polynomial-time algorithm for linear programming. In Proceedings of the sixteenth annual ACM symposium on Theory of computing (pp. 302-311).

[13] Zi-Luan, W., 1987. An interior point method for linear programming. Journal of Computational Mathematics, pp.342-351.

[14] Kojima, M., Mizuno, S. and Yoshise, A., 1989. A primal-dual interior point algorithm for linear programming. In Progress in mathematical programming (pp. 29-47). Springer, New York, NY.

[15] Kantorovich, L.V., 1939. The mathematical method of production planning and organization. Management Science, 6(4), pp.363-422.

[16] Dantzig, G.B., 1990. Origins of the simplex method. In A history of scientific computing (pp. 141-151).

[17] http://web.mit.edu/15.053/www/AMP-Chapter-09.pdf

[18] Hofman, R. and ING, E., 2007. Why LP Cannot Solve Large Instances of NP-complete Problems in Polynomial Time. In IMECS (pp. 596-599).

----
****