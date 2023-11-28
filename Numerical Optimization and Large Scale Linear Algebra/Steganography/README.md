# Steganography via Least Squares

*Numerical Optimization and Large Scale Linear Algebra*  
*MSc in Data Science, Department of Informatics*  
*Athens University of Economics and Business*

## *Introduction*

- In steganography, a secret message is embedded in an image in such a way that the image looks the same
- In this project, we explore a simple approach to steganography that relies on constrained least squares
- The secret message is given by a $k$-vector $s$ with entries that are all either +$1$ or -$1$ (boolean vector)
- The original image is given by the $n$-vector $x$, where $n$ is usually much larger than $k$
- We send (or publish or transmit) the modified message $x+z$, where $z$ is an $n$-vector of modifications
- We would like $z$ to be small, so that the original image $x$ and the modified one $x+z$ look (almost) the same
- Our accomplice decodes the message $s$ by multiplying the modified image by a $k \times n$ matrix $D$
- The multiplication yields the $k$-vector $y = D(x + z)$
- The message is then decoded as $\hat{s}=sign(y)$
- The matrix $D$ must have linearly independent rows, but otherwise is arbitrary

## *Project Overview*

- We need to minimize $\|z\|^{2}$ subject to the equality constraint $D(x+z)=\alpha s$, which we can write as $Dz=\alpha s-Dx$
- This is a least norm problem, with solution (assuming that $D$ has linearly independent rows) $z=D^{†}(\alpha s-Dx)$
- We generate the matrix  $D $ randomly and normalize it to have norm $\| D \|=1$, and compute $D^{†}$
- The modified image  $x+z $ may have entries outside the range $[0, 1]$
- We replace any negative values in the modified image with zero, and any values greater than one with one
- We adjust $\alpha$ until the original and modified images look the same, but the message is decoded correctly
