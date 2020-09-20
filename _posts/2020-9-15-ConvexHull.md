---
layout: post
title: Convex Hull
---

## A bit of the history
With the development of high-performance computers, large-scale optimization problems from different fields became much more solvable. Although the concept _computational geometry_ was widely applaused in the mid-1970's, geometry is one of the longest studied mathematical problems in enormous pratical applications. 

### Why convex matters
>> _"...in fact, the great watershed in optimization isn't between linearity and nonlinearity, but convexity and nonconvexity."_
>> 
>> R. Tyrrell Rockafellar, in SIAM Review, 1993

In the cases that the relationship between the input and output is curved, either curving upward or curving downward. The first modern formalization of the concept of convex function is believed to be the _Jensen's Inequality_: The mean of a convex function of a variable is always greater than the function of the mean variable. The definition of convex function has become a standard element in calculus handbooks.

![Pictorial representation of a convex function and a concave function from Probabilitycourse.com.](https://www.probabilitycourse.com/images/chapter6/Convex_b.png)

![A convex polygon vs. a concave (or non-convex) polygon. A concave curve can be easily switched to a convex one by inverting the output of the function.](https://www.differencebetween.info/sites/default/files/images/4/convex-nonconvex.jpg)

Convex optimization problems are defined as where all of the contraints are convex functions. This should refresh you with some of the relevant concepts. The convex hull (CH) can be explained as an enclosed set of points forming the smallest convex polygon, without any inward corners. Algebraically, a function is convex if, for any two points _*x*_ and _*y*_, the line between _*g(x)*_ and _*g(y)*_ stay above the function _*g(\dot)*_.
If the current corner bends inwards, the cross product will be positive, otherwise, this corner bends outwards. Keep checking the next point and repeat.

Why Convex? In reality, convex optimization are far more general than linear programming problems. For convex sets, one sees its promising properties in the study of the simplex method and of continuity of convex functions. This allows it to be solved quickly and reliably under large numbers of variables and constraints. 

Here we sum up popular convex algorithms as follows. 
- Jarvis March (2D cases of Gift Wrapping)
- Incremental Method
- Quick Hull
- Divide and Conquer
- Graham's Scan
- Monotone Chain
- Kirkpatrick-Seidel
- Chan

### Graham's scan algorithm^{5}
The 'big-bang' of computaional geometry is credited to Graham's research. His paper titled _An efficient algorithm for determining the convex hull of a finite planar set_ was a reponse to Bells Lab's request for a much rapidly solution for ten throusand points which used to be a challenging number for both human and computers in the 1960s. 
To find the convex of a set of points, the first phase of the algorithm is to identify the most left and top point (the minimal point) alone y-axis. THe remaining points are sorted in increasing angular value (ranging from 90 degree to 270 degree) and them the main phase of Graham's scan can begin examining the convexity of each point. 
If any points are concave, then there exists a better path that reduces the overall perimeter point. Graham's scan algorithm exploits this property by drawing a direct line between its two neighbor points.

![Animation of Graham's algorithm^{2}](https://miro.medium.com/max/388/1*3AI-zT522z8cjGn8EGcL5g.gif)

However, Graham's scan algorithm cannot be extended to cover problems in 3D or higher dimensions. 

### Gift wrapping algorithm^{6}
Jarvi's March, published one year later than Graham's paper, proposed a novel approach uses technique called _gift wrapping_, which was introduced by Chand and Kapur in 1970. They figured out that the convex hull has few nodes in the perimeter set. In real-world data, the distribution of points often shows heavily clustered and can be wrapped up by a few points comprised the perimeter. This attribute intuition can help us to implement algorithms to compute the convex hull more rapidly.  
Similar to Graham's Scan, Jarvi's March is initialized by locating a starting node in the convex hull. Start from the the leftmost point and keep wrapping points in counter clock wise direction. To find the next point in output, the selected point beats all other points at counter clock wise oreientation, otherwise it will be a concave. 

![Animation of gift wrapping algorithm^{3}](https://iq.opengenus.org/content/images/2018/06/anim1.gif)

### Complexity analysis
We conclude the complexity of common convex hull algorithms as follows. _n_ denotes the number of points in a set, and _h_ being the number of points in the convex hull. If you need to work out the time complexity from scratch, these details are covered in their original papers. 

Algorithm | Time Complexity 
----------|----------------
Greedy | _O(n^2)_
<a href="https://dl.acm.org/doi/pdf/10.1145/321556.321564">Gift Wrapping</a>  <a href="https://www.sciencedirect.com/science/article/pii/0020019073900203"> Jarvi's March</a>| _O(nh)_ 
<a href="https://ci.nii.ac.jp/naid/30007731417/">Graham' Scan</a> | _O(nlogn)_
<a href="https://dl.acm.org/doi/pdf/10.1145/235815.235821">Quick Hull</a> | _O(nlogn)_
<a href="https://dl.acm.org/doi/pdf/10.1145/359423.359430">Divide and Conquer</a> | _O(nlogn)_
<a href="https://www.sciencedirect.com/science/article/pii/0020019079900723">Monotone Chain</a> | _O(nlogn)_
<a href="https://www.sciencedirect.com/science/article/pii/002001908490084X">Incremental Method</a> | _O(nlogn)_
<a href="https://ecommons.cornell.edu/bitstream/handle/1813/6417/83-577.ps?sequence=2">Kirkpatrick-Seidel</a> | _O(nlogh)_
<a href="https://link.springer.com/article/10.1007/BF02712873">Chan</a> | _O(nlogh)_
----------|----------------

## How convex hulls are used in reality?


### Image processing
One of the parcital applications of divide and conquer approach towards CP is image processing. Like many other apps, Photoshop has built-in edge dection tool that helps users quickly select or mask certain areas of the photo. Just simply draw a rectangle around the object and the object selection tool will do the rest for us. A convex hull of a complex object can be used as a much simplified geometry for rapid broad phase collision detection. Interestingly, in Matlab the function `regionprops` can do the trick that construct the smallest convex polygon for objected detected. Pratical applications have been reported in the field of agriculture and medical.

### Convex optimization in machine learning
Machine learning problems are generally formulated as some loss function optimization on training datasets. Loss functions account for the discrepancy between the predictions of the trained model and the  ground truth. For instance, in robot motion planning, to move from current location to a destination, the shortest path will either be the straight line between two points (without obstacles) or one of the the two polygonal chains of the convex hull. 

### Hazard leak evacuation
Imagine that when a disaster such as a chemical leak or nuclear radiation leak happens, we need to determine the perimeter for immediate evacuation by constructing the convex hull of areas with affected levels. For indoor scenarios, since graph model is ofen used to represent structure and connectivity of buildings, e.g. each room can be viewed as a node, and cooridos are associated with edges. A semantic model for facilitating calculation of evacuation routes based on convex hull is presented^{}, Particular building characteristics related to exit possibilities such as available doors and windows are considered as leading.

### Disease epidemic tracking
A specific study in tracking animal epidemic is mentioned^{8}. The convex hull at time _t_ after the disease outbreak provides a rough measure of the area over which the infections of individuals have spread up to _t_.

![The snapshot of the trajectories of infected individuals at the epidemics outbreak, indicating that as the epidemic grows in space, the corresponding convex hull also grows in time.](https://www.pnas.org/content/pnas/110/11/4239/F1.medium.gif)

## External links
[1] Preparata, F.P. and Hong, S.J., 1977. Convex hulls of finite sets of points in two and three dimensions. Communications of the ACM, 20(2), pp.87-93.

[2] https://towardsdatascience.com/convex-hull-an-innovative-approach-to-gift-wrap-your-data-899992881efc 

[3] https://iq.opengenus.org/gift-wrap-jarvis-march-algorithm-convex-hull/

[4] https://assets.cambridge.org/97805218/50056/excerpt/9780521850056_excerpt.pdf 

[5] Ronald L Graham. "An efficient algorithm for determining the convex hull of a finite planar set." Information processing letters, vol.1, no.4, pp.132-133, 1972.

[6] Donald R. Chand, and Sham S. Kapur. "An algorithm for convex polytopes."Journal of the ACM (JACM), vol.17, no.1, pp.78-86, 1970.

[7] https://www.chrisharrison.net/index.php/Research/ConvexHull

[8] Spatial extent of an outbreak in animal epidemics. Eric Dumonteil, Satya N. Majumdar, Alberto Rosso, Andrea Zoia. Proceedings of the National Academy of Sciences Mar 2013, 110 (11) 4239-4244; DOI: 10.1073/pnas.1213237110

[9] https://www.coursera.org/learn/computational-geometry

[10] https://www.coursera.org/lecture/algorithms-part1/convex-hull-KHJ1t

[11] Meijers, M., Zlatanova, S. and Pfeifer, N., 2005, June. 3D geoinformation indoors: structuring for evacuation. In Proceedings of Next generation 3D city models (Vol. 6, pp. 11-16). Germany Bonn.

----
****