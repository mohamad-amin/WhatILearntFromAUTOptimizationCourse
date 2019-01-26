# What I learnt from the optimization course 

Hi! I took the optimization course this semester, which is offered for master students under supervision of [Dr. Maryam Amirmazlaghani at AUT](http://ceit.aut.ac.ir/autcms/people/verticalPagesAjax/professorHomePage.htm?url=mazlaghani&depurl=computer-engineering&lang=en&cid=11875). As many of my friends and other students asked me about how the course was offered and what the main topics offered in the course are, I decided to write this article in an effort to further clarify what you can learn by taking this course, by sharing my own experiences from taking this course. Feel free to contribute to this article and hope you'll find it useful! 

## Table of Contents
* [Sources](#sources)
	* [The Source Books](#the-source-books)
	* [Slides](#slides)
* [Introduction](#introduction)
	* [What is optimization?](#what-is-optimization)
	* [What are optimization problems?](#what-are-optimization-problems)
	* [How do optimization algorithms work?](#how-do-optimization-algorithms-work)
	* [Where is optimization used?](#where-is-optimization-used)
* [Solving Optimization Problems](#solving-optimization-problems)
	* [Defining Convex Problems](#defining-convex-problems)
	* [Multi Objective Optimization Problems](#multi-objective-optimization-problems)
* [Unconstrained Optimization](#unconstrained-optimization)
	* [Line Search Methods](#line-search-methods)
	* [Trust Region Methods](#trust-region-methods)
* [Unconstrained Optimization Applications](#unconstrained-optimization-applications)
	* [Approximation and Fitting](#approximation-and-fitting)
	* [Statistical-Estimation](#statistical-estimation)
* [Constrained Optimization](#constrained-optimization)
	* [Duality Theorem](#duality-theorem)
	* [Solving Equality Constrained Problems](#solving-equality-constrained-problems)
	* [Solving General Constrained Problems](#solving-general-constrained-problems)


## Sources
First, I mention the source materials that were used in this course.
#### The source books
* [Convex Optimization - Boyd and Vandenberghe](http://web.stanford.edu/~boyd/cvxbook/)
	* All of the chapters were covered (sparsely for sure :D)
* [Numerical Optimization - Jorge Nocedal, Stephen J. Wright](http://www.bioinfo.org.cn/~wangchao/maa/Numerical_Optimization.pdf)
	* Chapters 2 to 5 (also sparsely)

#### Slides
Also, the slides used to teach in the classroom can be found [here](https://ceit.aut.ac.ir/smbweb.php?path=common%2Fmazlaghani%2FOptimization%2FSlides) (Available for AUT students only!).

## Introduction
First, The course started with some introductions of the optimization topic and then it moved on to defining an optimization problem and the algorithms used to solve them, and also further categorize them both.

### What is optimization?
Optimization is portrayed in terms of: 
* Defining an **objective** (a quantitive measurement of performance) 
* Finding the **variables** the **objective** depends on
* Finding the values of the **variables** that optimize the *objective*

Mathematically, we model our problem as an *optimization problem*,  and then use an *optimization algorithm* to solve it.

### What are optimization problems?
Optimization problems are a set of equations in the form below, in which $x$ is the input vector of variables, $f$ is the objective function and $c_i$'s are the constraint functions (scalar functions of $x$) that define certain equations and inequalities that $x$ must satisfy.
$$
minimize \quad f(x)
\\ \text{subject to } c_i \quad \, i =1,2,\dots,n
$$
The set of $x$'s that satisfy all of the $c_i$'s and are in $\mathcal{D}_f$, are called the **feasible set** for this problem; Also, if there is no $c_i$, the problem is called an *unconstrained optimization problem*, and otherwise, it's a *constrained* or *general* optimization problem.
### How do optimization algorithms work?
Optimization algorithms are normally some iterative algorithms, which begin with an initial guess of $x$ and then generate a sequence of improved estimates until they terminate (satisfy a certain criterion). The strategy to improve the estimation is the key difference between different algorithms.

### Where is optimization used?
As you might've guessed already, optimization can be used in a vast majority of fields and solve many kinds of problems, from solving a certain company's employee allocation problems, to defining best exchange portfolio based on a person's budget, or some well known (and hot - these days at least -) topics like finding the optimal parameters for a vide variety of machine learning algorithms like:
* Different Regression Algorithms
* Linear and Kernel SVMs
* K-Means Clustering
* Neural Network Training 
* and so many more!

As they say nowadays:
> Optimization is the heart of machine learning.

## Solving Optimization Problems
Solving the optimization problems at the general form is a really tough challenge! There are currently (and probably, always :D) no efficient algorithms to solve the general optimization problem. Instead, we can solve some specific optimization problems efficiently called **linear programs**, **least square problems** and **convex problems**. General problems are usually solved in terms of defining the solving their *convex subproblems*.

### Defining Convex Problems
The course then goes through defining **convex sets**, **convex functions** and some other related linear algebra stuff and some methods for checking if a function or set is convex or not, including some optimization problem equivalences that help defining convexity of functions and sets. It then uses these concepts to define and verify a **convex problem**, and also studying some attributes of these problems that help us in building efficient algorithms for solving these kind of problems.

### Multi Objective Optimization Problems
Another type of convex problems discussed are the *multi objective optimization problems* which introduces the idea of multiple dimensioned objective functions (or optimizing alike problems at the same times). There comes the introduction of **pareto optimal problems** and **scalarization** for these kinds of problems.

## Unconstrained Optimization
Then the course moves on to introducing some algorithms for solving the unconstrained problems. The algorithms discusses are divided into two types:

### Line Search Methods
These algorithms include two main steps in each iterations:
1. Defining the direction in which we'll make the next step towards to optimal point. Approaches for this step include:
	* Steepest descent direction
	* Newton direction
	* Quasi-newton directions
2. Calculating the step length for each iteration to take onside the direction chosen. The approaches for this part include:
	* Backtrack Step length selection using *wolfe conditions*
	* Cubic interpolation step length selection method

### Trust Region Methods
These algorithms define an area around the current point, and find a direction and a step length simultaneously to go to another point within the area defined, the algorithms discussed in this part are:
* Cauchy Point Algorithm
* DogLeg Algorithm

#### Implementation of these algorithms:
I've implemented these algorithms and demonstrated their example usage in this repository as a homework for this course: [Unconstrained Optimization on GitHub](https://github.com/mohamad-amin/UnconstrainedOptimization)

##  Unconstrained Optimization Applications
Then two main applications of unconstrained optimization are described which include:

### Approximation And Fitting
These applications include several topics:
* Norm Approximation
* Least Norm 
* Least Penalty
* Regularized Least Penalty (Multi Objective)
* Optimal Input Design
* Robust Approximation

### Statistical Estimation
These problems include estimating parameters of a known distribution and solving the well known **MLE** and **MAP** problems (using the methods described) which are used vastly in machine learning.

## Constrained Optimization
The course moves through defining some algorithms for solving constrained optimization problems. As *duality theorem* is used in these algorithms, or as it's used elsewhere for solving these problems (which we'll come to shortly), first the duality theorem and some of its applications in optimization are discussed and then they're used in solving the constrained optimization problems.

### Duality Theorem
According to the *duality theorem*, we can find a dual problem for every optimization problem, which gives us a lower bound on the optimal value of $p^*$ (the optimal value for the original problem).
Then comes two types of duality: ($d^*$ is the optimal value for the dual problem)
* **Weak Duality:** $p^* \ge d^*$
* **Strong Duality:** $p^* = d^*$

And so, we call $p^* - d^*$ the duality gap for our dual and original problems. Thus, the dual problem can be used to find (exact or inexact) lower bounds on the optimal values of original problem.
There comes some conditions such as **Salter's conditions** and **KKT conditions** to check for *strong duality*.
> SVM for example, is a sample of an algorithm which can be solved using its duality problem.

### Solving Equality Constrained Problems
Finally, the course moves on to solving the constrained problems. First we consider the equality constrained problems, in which each $c_i$ is an equality constraint, and there exists at least one $c_i$.
The methods for solving these problems include:
* Eliminating Equality Constraints
* Solving Dual Problem of the original problem
* Newton’s method
	* This is a modification of the original newton algorithm which considers the equality constraint and uses duality to find a step length which both moves through the optimal point and takes into account the feasibility of the point according to the equality constraints.
	* There is also another modification which enables this method to use some infeasible starting point.

-   Feasible Start
-   Infeasible Start

### Solving General Constrained Problems
As the last topic, we move on solving the general constrained optimization problem.
The approach taken here is to approximately formulate the inequality constrained problem as an equality constrained problem. We use a logarithmic barrier to make this approximation work, which gives us a **central path** defined based on the parameter of the logarithmic barrier (called $t$). Then two algorithms are used for calculating the optimal value using the *central path idea*:
* Log Barrier Method
	* The idea behind this method is to choose a small $t$ and a random starting point at the beginning and then increasing $t$ based on satisfying certain criterion until reaching the desired tolerance for each step.
* Primal Dual Interior Point Method
	* The idea behind this algorithm is to use a modified version of the KKT conditions and compute a **primal dual search direction** in each step and use it in conjunction with a line search method to make a step in each iteration and continuing until reaching desired tolerance for primal and dual residuals.
