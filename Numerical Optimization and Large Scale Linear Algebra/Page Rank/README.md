# PageRank

*Numerical Optimization and Large Scale Linear Algebra*  
*MSc in Data Science, Department of Informatics*  
*Athens University of Economics and Business*

## *Introduction*

- PageRank is an algorithm used by Google Search to rank web pages in their search engine results
- It is named after both the term "web page" and co-founder Larry Page
- PageRank is a way of measuring the importance of website pages
- According to Google, PageRank works by counting the number and quality of links to a page
- Doing so, it tries to determine a rough estimate of how important the website is
- The underlying assumption is that more important websites are likely to receive more links from other sites

## *Project Overview*

- We define functions both for the **Power method** and the iterative **Gauss-Seidel method**
- For both methods, we consider as  $\alpha=0.85 $ and stopping criterion  $\tau=10^{-8} $
- Also, the vector $\alpha$ having 1 if it corresponds to a node without outbound links, and 0 otherwise
- Then, using both methods, we find the PageRank vector $\pi$ and compare their results and performances
- We repeat the previous task, but now with $\alpha=0.99$ and we compare again their results and performances
- Furthermore, using both methods, we check if the components of $\pi$ converge at the same time to their limits
- We try to find which of them converge faster, *those that correspond to important nodes or to non important?*

## *Data*

- The file `Stanweb.dat.zip` contains the connectivity matrix for the webpages of Stanford University
- In the first column are contained the nodes, while in the second the node with which is connected
- The third column contains their weights

## *Resources*

- Packages: `numpy`, `pandas`, `matplotlib`, `scipy`
- Software: Jupyter Notebook

## *The 2 Methods*

### Power Method

- Power method is an eigenvalue algorithm
- Given a diagonizable matrix $A$, the algorithm will produce:
    - a number $\lambda$, which is the greatest (in absolute value) eigenvalue of $A$
    - a non-zero vector  $v $, which is a corresponding eigenvector of  $\lambda $, that is,  $Av=\lambda v $
- Power method is a very simple algorithm, but it may converge slowly
- The most time-consuming operation of the algorithm is the multiplication of matrix $A$ by a vector
- Therefore, this algorithm is effective for a very large sparse matrix with appropriate implementation

### Gauss-Seidel Method

- The Gauss-Seidel method is an iterative method used to solve a system of linear equations
- It is, also, known as the Liebmann method and is similar to the Jacobi method
- Theoritically, it can be applied to any matrix with non-zero elements on the diagonals
- However, convergence is only guaranteed if one of the following two conditions is met:
    - the matrix is strictly diagonally dominant, or
    - the matrix is symmetric and positive definite
