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

``` math
H₂=I₁-5 B² I₁²/12 
```

and the remaining elements in the list `%o4` are

  * I₁ is the quadratic part of H;
  * a list of parameters used to solve for the generating function φ and H₂;
  * a check sum which should be 0;
  * H₂ in mixed variables;
  * the generating function φ of the transformation from H to H₂.


For a longer set of examples, see the [rtest_bnf.mac](https://github.com/leo-butler/bnf/blob/master/rtest_bnf.mac) file.

## Notes ##

A reference for the Birkhoff normal form using generating functions is section 6.4 of
[Robinson's Dynamical Systems](https://www.crcpress.com/Dynamical-Systems-Stability-Symbolic-Dynamics-and-Chaos/Robinson/p/book/9780849384950 "Textbook").

## Requirements ##

This package requires the following

  * [with_gensyms](https://github.com/leo-butler/with_gensyms.git "with_gensyms"), a Maxima package.
  * a unicode-aware lisp or the unicodedata package in Maxima.

## TODO ##

Implement a Lie transformation version.

## Contact ##

Email `printf(true,"~{~c~}",[108,101,111,46,98,117,116,108,101,114,64,117,109,97,110,105,116,111,98,97,46,99,97]);`
