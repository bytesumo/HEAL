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

Create a project using stack where we can test and run the code
```shell
stack -v new rgep simple
```
Download the source, copy it into our project
```
git clone https://github.com/bytesumo/HEAL.git
cp HEAL/*.* rgep/src/.
```
The HEAL library depends on modules, which we need to add to our .cabal configuration file.
We need to edit the default one and add in a couple of libaries
```
executable rgep
  hs-source-dirs:      src
  main-is:             Main.hs
  default-language:    Haskell2010
  build-depends:       base >= 4.7 && < 5, mersenne-random-pure64
```
then we can fire up the repl, load the environment with dependent modules, and import the code.

```
stack ghci -v
```
note there is an error in a HEAL import in EAMonad.hs file. It's looking for import Control.Monad.State.Strict, but this change seemed to fix it:
```
import Control.Monad.ST.Strict
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
