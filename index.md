@def title = "MATH 180"
@def tags = ["mathematics", "maths", "math"]

# Triangular Numbers

\tableofcontents

## Our Question

\question{#12}{
The $n^{\text{th}}$ triangular number $t_n$ is the number \begin{equation*}t_n=1+2+3+\dots+n.\end{equation*} For example, \begin{equation*}t_1=1, \quad t_2=3, \quad t_3=6, \quad t_4=10,\end{equation*} and so on. Is the product of two different triangular numbers ever a perfect cube? If so, when? What about the product of three different triangular numbers? Four?
}

## Why

## Our Methods

\definition{triangular number}{
Consider the infinite series whose terms are the natural numbers, i.e., \equation{1+2+3+4+5+\dots.} Then, the $n^{\text{th}}$ triangular number $t_n$ is the $n^{\text{th}}$ partial sum of this infinite series, i.e., \equation{\align{t_n&=1+2+3+4+5+\dots+n\\&=\sum_{i=1}^{n}i\\&=\frac{(n+1)n}{2}.}}
}

```python
def tri(n):
  if n == 1:
    return 1;
  else:
    return tri(n-1) + n;

triangular = [];
for i in range(1, 1000):
  triangular.append(tri(i));
```

## Our Results

## Future
