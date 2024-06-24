We see that 5 small primes are getting generated $p,q,r,s,a$ and using them $n$ is found. $e$ is 65537.
So,
$$n = pqrsa$$
$$\phi(n) = (p-1)(q-1)(r-1)(s-1)(a-1)$$
Other than this, its just normal RSA.

**solve.sage**

```python
from Crypto.Util.number import long_to_bytes
n = 317903423385943473062528814030345176720578295695512495346444822768171649361480819163749494400347
e = 65537
enc = 127075137729897107295787718796341877071536678034322988535029776806418266591167534816788125330265
phi = 1
for f in ecm.factor(n):
	phi*=f-1
d = pow(e,-1,phi)
m = pow(enc,d,n)
print(long_to_bytes(int(m)).decode())
```

Flag: `FLAG{S0_3a5y_1254!!}`
