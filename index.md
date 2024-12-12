@def title = "MATH 180"
@def tags = ["mathematics", "maths", "math"]

# Triangular Numbers

\tableofcontents

## Our Question

\question{#12}{
The $n^{\text{th}}$ triangular number $t_n$ is the number \begin{equation*}t_n=1+2+3+\dots+n.\end{equation*} For example, \begin{equation*}t_1=1, \quad t_2=3, \quad t_3=6, \quad t_4=10,\end{equation*} and so on. Is the product of two different triangular numbers ever a perfect cube? If so, when? What about the product of three different triangular numbers? Four?
}

## Why

- The triangular numbers are a type of polygonal number.
- The triangular numbers are the third diagonal on Pascal's triangle.

## Our Methods

We needed a way to work with an individual triangular number, so

\definition{triangular number}{
Consider the infinite series whose terms are the natural numbers, i.e., \equation{1+2+3+4+5+\dots.} Then, the $n^{\text{th}}$ triangular number $t_n$ is the $n^{\text{th}}$ partial sum of this infinite series, i.e., \align{t_n&=1+2+3+4+5+\dots+n\\&=\sum_{i=1}^{n}i\\&=\frac{(n+1)n}{2}.}
}

As definition manipulation didn't work out, we moved to brute force. Originally, writing our program in C++ came to mind, but since most people would be unfamiliar with the language, I opted for Python which has some resemblance to MATLAB.

Our code was as follows,
```python
import math;

def tri(n):
  if n == 1:
    return 1;
  else:
    return tri(n-1) + n;

# from @nneonneo on stackoverflow
def cbroot(n):
  c = int(n**(1/3.));
  return (c**3 == n) or ((c+1)**3 == n);

triangular = [];
for i in range(1, 777):
  triangular.append(tri(i));

for j in range(0, len(triangular)):
  t_j = triangular[j];
  for k in range(j+1, len(triangular)):
    t_k = triangular[k];
    if cbroot(t_j*t_k):
      print(str(t_j) + " times " + str(t_k) + " is " + str(t_j*t_k));
    for l in range(j+2, len(triangular)):
      t_l = triangular[l];
      if cbroot(t_j*t_k*t_l) and t_k != t_l:
        print(str(t_j) + " times " + str(t_k) + " times " + str(t_l) + " is " + str(t_j*t_k*t_l));
      for m in range(j+3, len(triangular)):
        t_m = triangular[m];
        if cbroot(t_j*t_k*t_l*t_m) and t_k != t_l and t_k != t_m and t_l != t_m:
          print(str(t_j) + " times " + str(t_k) + " times " + str(t_l) + " times " + str(t_m) + " is " + str(t_j*t_k*t_l*t_m));
```

## Our Results

- The first product of two triangular numbers that is a perfect cube is \equation{6\times 36.}
- The first product of three triangular numbers that is a perfect cube is \equation{1\times 6\times 36.}
- The first product of four triangular numbers that is a perfect cube is \equation{15\times 28\times 105\times 210.}

## Future

- Remove permutations.
- Store output in a better format.
- Increase input capacity by switching languages (Python has a soft recursive call limit).
- Find an interesting motivation for ourselves.
