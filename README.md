# BNF.MAC [github](https://github.com/leo-butler/bnf.git "repo link")#

A package to compute the normal form of a hamiltonian function,
including the Birkhoff-Gustavson normal form. Implemented in the
[Maxima CAS](https://maxima.sourceforge.net/ "Maxima url") language.

## Usage ##

Load and run the testsuite:

``` maxima
(%i1) load(bnf) $
(%i2) batch(rtest_bnf,'test) $
```

Compute the second-order Birkhoff normal form of the hamiltonian

``` math
H=B q³/3 + (q² + p²)/2.
```

``` maxima
(%i3) declare(B,constant) $
(%i4) ezbnf([q,p], (q^2+p^2)/2 + B*q^3/3, 4);

i= 3 
i= 4 
i= 4 
(%o4) [I1-(5*B^2*I1^2)/12,I1 = %q^2/2+%p^2/2,
       [ϣ[1,2] = 0,ϣ[0,3] = -(2*B)/9,ϣ[2,1] = -B/3,ϣ[3,0] = 0,
        ϣ[1,3] = (47*B^2)/144,a[2] = -(5*B^2)/12,ϣ[0,4] = 0,ϣ[2,2] = 0,
        ϣ[3,1] = (25*B^2)/144,ϣ[4,0] = 0],0,
       ((36*a[2]+15*B^2)*q^4+48*B*q^3+((72*a[2]+83*B^2)*%p^2+72)*q^2
                            +96*B*%p^2*q+(36*a[2]+32*B^2)*%p^4+72*%p^2)
        /144,
       (47*B^2*%q*p^3)/144-(2*B*p^3)/9+(25*B^2*%q^3*p)/144-(B*%q^2*p)/3+%q*p]

```

Which gives

\[ H_2 = I_{1}-{{5\,B^2\,I_{1}^2}\over{12}}, \]

and the remaining elements in the list `%o4` are

  * $I_1$ is the quadratic part of $H$;
  * a list of parameters used to solve for the generating function $φ$ and $H_2$;
  * a check sum which should be $0$;
  * $H_2$ in mixed variables;
  * the generating function $φ$ of the transformation from $H$ to $H_2$.

