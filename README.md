Forked from https://github.com/nsmryan/HEAL

RGEP Examples
=============

This repository will server as my test of pulling together a worked example of RGEP, Robust Gene Expression Programming using the HEAL library.

Paper to review is here:
https://ac.els-cdn.com/S1877050911004972/1-s2.0-S1877050911004972-main.pdf?_tid=6305469a-13ff-11e8-b7f4-00000aab0f26&acdnat=1518885011_942a832139f81e71624868b29c447939

Getting Started:
Install Haskell compiler if you don't have one. I'm using https://www.haskell.org/platform/

On the command line, test it's running: 
```shell
> ghci
GHCi, version 8.2.2: http://www.haskell.org/ghc/  :? for help
Prelude>
```


HEAL
====

Haskell Evolutionary Algorithm Library- This repository is the reference implementation for Robust Gene Expression Programming (RGEP).

This library was written to explore Gene Expression Programming (GEP), Binary Gene Expression Programming (BGEP),
Prefix Gene Expression Programming (PGEP), and a combination of these designed by the author called Robust
Gene Expression Programming (RGEP).


The title of the thesis was Robust Gene Expression Programming: Evolving Treeless Expression Trees.

The design of RGEP was intended to simplify the original GEP algorithm using technics from the literature (PGEP, BGEP
being prime examples) while maintaining the performance of the original algorithm on some commonly studied problems.

In addition, the thesis explored the implications of using a postfix notation instead of the original "karva" notation
used in GEP or the prefix notation used in PGEP.
