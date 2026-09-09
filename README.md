# PA2 | ECE2112 | EXPERIMENT 2 | DIONALDO, PVA
---
### **NUMPY**
#### Submitted by Pierre Van Aken A. Dionaldo | 2ECE-A | 09.08.2026

This repository showcases the objective and detailed discussion of the experiment from the Programming Assignment 2 last September 1, 2026 where the class discussed Module 2 - **Numerical Python (NUMPY)**

---
### **Objectives**
---
At the end of this laboratory activity, the student should be able to:

1. create and reshape NumPy arrays using appropriate NumPy functions;
2. perform vectorized numerical operations on an ndarray;
3. compute array statistics and use Boolean conditions to select elements; and
4. save computed NumPy arrays as .npy files.

The students are also expected to write a Python code in a Jupyter Notebook and import NumPy as np to solve each of the following problems with the following instructions:

- Use NumPy array operations. Do not use Python loops or list comprehensions to perform the required numerical calculations or filtering.
- Do not hard-code a computed result. Construct every result from the array specified in the problem.
- Use the exact variable and output filenames stated below.
- Display the requested checks in the notebook before saving each result.
- Do not use libraries other than NumPy.
  
---
### **Programming Problems**
---
#### **A. REPRODUCIBLE NORMALIZATION PROBLEM**

Create a reproducible random 5×5 integer ndarray named X. Use the following two statements before performing any calculation:
```
np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))
```
Normalize the complete array using
```
Z = (X - x¯) / σ
```
where x¯ is the mean of all 25 elements and σ is their population standard deviation as returned by
NumPy’s default std() call. Store the normalized array in X normalized.

**Required checks**: Display X, X normalized, its mean, and its standard deviation. Up to floating point rounding, the normalized mean must be 0 and the normalized standard deviation must be 1.

Save the normalized array as:
```
X_normalized.npy
```

**CODE**
```
import numpy as np

np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))

mean = X.mean()
sigma = X.std()

X_normalized = (X - mean) / sigma

print("PROBLEM A: REPRODUCIBLE NORMALIZATION\n")

print("Original Array X:\n", X)
print("\nNormalized Array X_normalized:\n", X_normalized)
print("\nMean of X_normalized:", X_normalized.mean())
print("Standard Deviation of X_normalized:", X_normalized.std())

np.save("X_normalized.npy", X_normalized)
```

**OUTPUT**
```
PROBLEM A: REPRODUCIBLE NORMALIZATION

Original Array X:
 [[48 11 15 67 21]
 [11 41 13 66 24]
 [71 79 53 67 70]
 [77 35 91 19 96]
 [35 54 37 41 17]]

Normalized Array X_normalized:
 [[ 0.06340841 -1.36714726 -1.2124926   0.79801809 -0.98051059]
 [-1.36714726 -0.20723725 -1.28981993  0.75935442 -0.86451959]
 [ 0.95267275  1.26198209  0.25672675  0.79801809  0.91400909]
 [ 1.18465476 -0.43921926  1.72594609 -1.05783793  1.91926443]
 [-0.43921926  0.29539042 -0.36189192 -0.20723725 -1.13516526]]

Mean of X_normalized: 0.0
Standard Deviation of X_normalized: 0.9999999999999999
```

The following functions and methods in this code are:
- `import numpy as np`: this is used to load the NumPy library into this script and give it the shortcut name *np*
- `np.random.seed(2112)`: this is used to initialize NumPy's pseudo-random number generator with a fixed seed of 2112.
- `X = np.random.randint(10, 101, size=(5, 5))`: setting *X* as the reproducible random 5×5 integer ndarray
- `mean = X.mean()
   sigma = X.std()`: Setting both variables to the aggregate function of *Mean* and *Standard Deviation*
- `X_normalized = (X - mean) / sigma`: function of normalized array
  > Where *X* is the element, *mean* is the mean of the 25 element, *sigma* is the population standard deviation
- `print("PROBLEM A: REPRODUCIBLE NORMALIZATION\n")`: Prints the header of the code
- `print("Original Array X:\n", X)`: Prints the original array X
- `print("\nNormalized Array X_normalized:\n", X_normalized)`: Prints the normalized array X using the function
- `print("\nMean of X_normalized:", X_normalized.mean())`:  Prints the mean of normalized array X
- `print("Standard Deviation of X_normalized:", X_normalized.std())`: Prints the standard deviation of normalized array X
- `np.save("X_normalized.npy", X_normalized)`: saves the np file of X_normalized

---
#### **B. CUBES DIVISIBLE BY 4 PROBLEM**
Using NumPy, create the first 100 positive integers, cube every element, and reshape the result into a
10 × 10 ndarray named C. Thus, C begins with 1^3 and ends with 100^3

Use a Boolean condition on C to obtain every cubed value divisible by 4. Store the selected values in
div by 4. Preserve NumPy’s normal row-major selection order.

**Required checks**: Display the shape of C, the array div by 4, and the number of selected elements.
A correct solution has 50 selected elements; the first is 8 and the last is 1,000,000.

Save the selected array as:
`div_by_4.npy`

**CODE**
```
C = (np.arange(1, 101) ** 3).reshape(10, 10)
div_by_4 = C [C % 4 == 0]

print (" CUBES DIVISIBLE BY 4 PROBLEM \n")
print ("Shape of C:", C.shape)
print ("Cubes Divisible by 4 Elements:\n", div_by_4)
print ("\nNumber of Selected Elements:", len (div_by_4))

np.save("div_by_4.npy", div_by_4)
```

**OUTPUT**
```
CUBES DIVISIBLE BY 4 PROBLEM 

Shape of C: (10, 10)
Cubes Divisible by 4 Elements:
 [      8      64     216     512    1000    1728    2744    4096    5832
    8000   10648   13824   17576   21952   27000   32768   39304   46656
   54872   64000   74088   85184   97336  110592  125000  140608  157464
  175616  195112  216000  238328  262144  287496  314432  343000  373248
  405224  438976  474552  512000  551368  592704  636056  681472  729000
  778688  830584  884736  941192 1000000]

Number of Selected Elements: 50
```

The following functions and methods in this code are:
- `C = (np.arange(1, 101) ** 3).reshape(10, 10)`: Setting C as the 10x10 ndarray from the cube of 1 to 100
- `div_by_4 = C [C % 4 == 0]`: Setting the boolean condition to obtain every cubed value divisible by 4 and stores it in the variable *div_by_4*
  > *C % 4 ==0* > The value of C divided by 4 must equal to zero to satisfy the condition
- `print (" CUBES DIVISIBLE BY 4 PROBLEM \n")`: Prints the header of the code
- `print ("Shape of C:", C.shape)`: Prints the shape of the array C
- `print ("Cubes Divisible by 4 Elements:\n", div_by_4)`: Prints only the value of the cube of 1 to 100 that is divisible by 4 to the 10x10 ndarray
- `print ("\nNumber of Selected Elements:", len (div_by_4))`: Prints the number of selected elements
  > len () is used to determine the number of elements | this was used and discussed last module
- `np.save("div_by_4.npy", div_by_4)`: saves the np file of div_by_4

- ---
#### **C. ABOVE-MEAN SQUARES PROBLEM**
Create a 6 × 6 ndarray named S containing the squares of the first 36 positive integers in increasing
row-major order. Compute the mean of all elements of S and store it in S mean. Then use Boolean
filtering to select only the elements strictly greater than S mean. Store these values in above mean.

**Required checks**: Display S, S mean, above mean, and the number of selected elements. A correct
solution has 15 selected elements; the first is 484 and the last is 1296.

Save the selected array as:
`above_mean.npy`

**CODE**
```
S = (np.arange(1,37)**2).reshape(6,6)
S_mean = S.mean()
above_mean = S [S>S_mean]

print ("ABOVE-MEAN SQUARES PROBLEM\n")
print ("Array S:\n", S)
print ("\nMean:", S_mean)
print ("Above Mean Array:\n", above_mean)
print ("\nNumber of selected elements:", len(above_mean))

np.save("above_mean.npy", above_mean)
```

**OUTPUT**
```
ABOVE-MEAN SQUARES PROBLEM

Array S:
 [[   1    4    9   16   25   36]
 [  49   64   81  100  121  144]
 [ 169  196  225  256  289  324]
 [ 361  400  441  484  529  576]
 [ 625  676  729  784  841  900]
 [ 961 1024 1089 1156 1225 1296]]

Mean: 450.1666666666667
Above Mean Array:
 [ 484  529  576  625  676  729  784  841  900  961 1024 1089 1156 1225
 1296]

Number of selected elements: 15
```

The following functions and methods in this code are:
- `S = (np.arange(1,37)**2).reshape(6,6)`: Setting S as the 6x6 ndarray from the square of thefirst 36 positive integers in increasing
row-major order. 
- `S_mean = S.mean()`: Sets *S_mean* as the mean of all elements
- `above_mean = S [S>S_mean]`: Sets *above_mean* as the variable to place elements in the ndarray that are above the mean using boolean filtering
- `print ("ABOVE-MEAN SQUARES PROBLEM\n")`: Prints the header of the code
- `print ("Array S:\n", S)`: Prints the original array S
- `print ("\nMean:", S_mean)`: Prints the mean of the original array S
- `print ("Above Mean Array:\n", above_mean)`: Prints the elements that satisfies the  condition where elements must be above the mean using boolean indexing which flattens the array into 1d
- `print ("\nNumber of selected elements:", len(above_mean))`: Prints the number of selected elements in the array S where above_mean elements are printed
- `np.save("above_mean.npy", above_mean)`: saves the np file of above_mean

To view program file for PA2 please visit this link [PA2_2ECEA_DIONALDO.ipynb] (https://github.com/akenvdio/PA2-NUMPY-2ECEA-DIONALDO/blob/main/PA2_2ECEA_DIONALDO.ipynb) and download. Open on Jupyter Notebook or Google Colab and run all cells.

---

## **README File Version History**
- September 8, 2026 - Upload .ipynb file
- September 8, 2026 - Upload README File
- September 8, 2026 - Upload X_normalized.npy file
- September 8, 2026 - Upload above_mean.npy file
- September 8, 2026 - Upload div_by_4.npy file
- September 9, 2026 - Updated README File
- September 10, 2026 - Updated README File

---
### **END OF NOTEBOOK**
