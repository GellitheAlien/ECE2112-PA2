## ECE2112-PA2

Made by: Geri Allison Geneta | 2ECE-B

This repository contains our Programming Assignment 2 for ECE2112. This project covers three python problems referenced to Module 2 - Numpy.

```python
import numpy as np
```

## A. Reproducible Normalization Problem

Create a 5 x 5 array of random integers between 10 and 100 using a fixed seed, then normalize its values using its mean and standard deviation.

The following functions and operations were used in this problem:

* np.random.seed(2112) - sets a random seed to ensure that the generated random numbers are reproducible every time the code runs.

* np.random.randint(10, 101, size=(5, 5)) - generates a 5 x 5 2D NumPy array with random integers ranging from 10 to 100.

```python
np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))
X
```

Output:
```text
array([[48, 11, 15, 67, 21],
       [11, 41, 13, 66, 24],
       [71, 79, 53, 67, 70],
       [77, 35, 91, 19, 96],
       [35, 54, 37, 41, 17]])
```

* np.sum() & .size - calculates the total sum of all elements in the array.

```python
Xsum = np.sum(X)
Xsum
```

Output:
```text
np.int64(1159)
```

* .size - gets the total amount of elements in an array.

The mean was determined by dividing the sum of X by its number of elements.

```python
mean = Xsum/ X.size
mean
```

Output:
```text
np.float64(46.36)
```

* np.std() - determines the standard deviation of the array.

```python
std = np.std(X[0:6,0:6])
std
```

Output:
```text
np.float64(25.864075471588002)
```

Applying standard normalization (z-score normalization) across all array elements.

```python
X_normalized = (X - mean)/std
X_normalized
```

Output:
```text
array([[ 0.06340841, -1.36714726, -1.2124926 ,  0.79801809, -0.98051059],
       [-1.36714726, -0.20723725, -1.28981993,  0.75935442, -0.86451959],
       [ 0.95267275,  1.26198209,  0.25672675,  0.79801809,  0.91400909],
       [ 1.18465476, -0.43921926,  1.72594609, -1.05783793,  1.91926443],
       [-0.43921926,  0.29539042, -0.36189192, -0.20723725, -1.13516526]])
```

* np.save() - saves the resulting normalized array into a .npy file named 'X_normalized'.

```python
np.save('X_normalized', X_normalized)
```

## B. Cubes Divisible by 4 Problem

Create a 10 x 10 array containing the cubes of the first 100 positive integers, and filter out only the cubed numbers that are divisible by 4.

The following functions and operations were used in this problem:

* np.arange(1, 101, 1) - creates a 1D array of integers from 1 to 100.

* np.power(..., 3) - computes the cube of each element in the sequence.

* .reshape(10, 10) - transforms the 1D array of 100 cubed values into a 10 x 10 2D matrix.

```python
C = np.power(np.arange(1, 101, 1), 3).reshape(10,10)
C
```

Output:
```text
array([[      1,       8,      27,      64,     125,     216,     343,
            512,     729,    1000],
       [   1331,    1728,    2197,    2744,    3375,    4096,    4913,
           5832,    6859,    8000],
       [   9261,   10648,   12167,   13824,   15625,   17576,   19683,
          21952,   24389,   27000],
       [  29791,   32768,   35937,   39304,   42875,   46656,   50653,
          54872,   59319,   64000],
       [  68921,   74088,   79507,   85184,   91125,   97336,  103823,
         110592,  117649,  125000],
       [ 132651,  140608,  148877,  157464,  166375,  175616,  185193,
         195112,  205379,  216000],
       [ 226981,  238328,  250047,  262144,  274625,  287496,  300763,
         314432,  328509,  343000],
       [ 357911,  373248,  389017,  405224,  421875,  438976,  456533,
         474552,  493039,  512000],
       [ 531441,  551368,  571787,  592704,  614125,  636056,  658503,
         681472,  704969,  729000],
       [ 753571,  778688,  804357,  830584,  857375,  884736,  912673,
         941192,  970299, 1000000]])
```

* Boolean Indexing (C[C % 4 == 0]) - uses the modulo operator % to create a condition that extracts only array elements divisible by 4.

```python
div_by_4 = C[C % 4 == 0]
div_by_4
```

Output:
```text
array([      8,      64,     216,     512,    1000,    1728,    2744,
          4096,    5832,    8000,   10648,   13824,   17576,   21952,
         27000,   32768,   39304,   46656,   54872,   64000,   74088,
         85184,   97336,  110592,  125000,  140608,  157464,  175616,
        195112,  216000,  238328,  262144,  287496,  314432,  343000,
        373248,  405224,  438976,  474552,  512000,  551368,  592704,
        636056,  681472,  729000,  778688,  830584,  884736,  941192,
       1000000])
```

* np.save() - saves the filtered array into a .npy file named 'div_by_4'.

```python
np.save('div_by_4', div_by_4)
```

## C. Above-Mean Square Problem

Create a 6 x 6 array containing the squares of the first 36 positive integers, find the average value of the matrix, and extract all numbers greater than that mean.

The following functions and operations were used in this problem:

* np.power(np.arange(1, 37, 1), 2).reshape(6,6) - generates an array of numbers from 1 to 36, squares each term, and reshapes the result into a 6 x 6 matrix.

```python
S = np.power(np.arange(1, 37, 1), 2).reshape(6,6)
S
```

Output:
```text
array([[   1,    4,    9,   16,   25,   36],
       [  49,   64,   81,  100,  121,  144],
       [ 169,  196,  225,  256,  289,  324],
       [ 361,  400,  441,  484,  529,  576],
       [ 625,  676,  729,  784,  841,  900],
       [ 961, 1024, 1089, 1156, 1225, 1296]])
```

* np.mean() - calculates the overall average value of all elements in the matrix.

```python
S_mean = np.mean(S)
S_mean
```

Output:
```text
np.float64(450.1666666666667)
```

* Boolean Indexing (S[S > S_mean]) - evaluates each square in the array and returns only those strictly greater than the calculated mean.

```python
above_mean = S[S > S_mean]
above_mean
```

Output:
```text
array([ 484,  529,  576,  625,  676,  729,  784,  841,  900,  961, 1024,
       1089, 1156, 1225, 1296])
```

* np.save() - saves the resulting filtered elements into a .npy file named 'above_mean'

```python
np.save('above_mean', above_mean)
```

The end.
