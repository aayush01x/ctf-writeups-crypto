`inputs` function takes input, 5 elements for 5x5 diagonal constructing a diaongal matrix. `check` function checks if the determinant of the matrix passed in the function is non-zero. `fun` function constructs a diagonal matrix 5x5 diagonal matrix with diagonal elements constructed by breaking the flag in parts of 5, converting them to long. Then it multiplies passed matrix with this constructed matrix and outputs the trace of the produced matrix.

First thing to notice is that matrix passed to `fun` is also a diagonal matrix. When two diagonal matrices are multiplied, corresponding elements in diagonal just get multiplied.
So, if input diagonal matrix is defined by $d_1,d_2,d_3,d_4,d_5$ and flag diagonal matrix by $f_1,f_2,f_3,f_4,f_5$, then multiplied diagonal matrix is $d_1 f_1, d_2 f_2, d_3 f_3, d_4 f_4, d_4 f_5$.
So, we get the value of $$d_1 f_1 +  d_2 f_2 + d_3 f_3 +  d_4 f_4 + d_4 f_5$$
We can create instance multiple number of times to get trace for any value of $d_1,d_2,d_3,d_4,d_5$.
So, we input following values in 6 instances:
```
1,1,1,1,1
2,1,1,1,1
1,2,1,1,1
1,1,2,1,1
1,1,1,2,1
1,1,1,1,2
```
This gives us the result of following equations
$$f_1+f_2+f_3+f_4+f_5 = z_0$$

$$2f_1+f_2+f_3+f_4+f_5 = z_1$$

$$f_1+2f_2+f_3+f_4+f_5 = z_2$$

$$f_1+f_2+2f_3+f_4+f_5 = z_3$$

$$f_1+f_2+f_3+2f_4+f_5 = z_4$$

$$f_1+f_2+f_3+f_4+2f_5 = z_5$$

We can obtain $f_1,f_2,f_3,f_4,f_5$ as following:
$$f_1 = z_1 - z_0$$
$$f_2 = z_2 - z_0$$
$$f_3 = z_3 - z_0$$
$$f_4 = z_4 - z_0$$
$$f_5 = z_5 - z_0$$

So, the final flag is ```long_to_bytes(f1) +long_to_bytes(f2)+long_to_bytes(f3)+long_to_bytes(f4)+long_to_bytes(f5)```

python exploit can be found in `exploit.py`

**Flag**: `uiuctf{tr4c1ng_&&_mult5!}`