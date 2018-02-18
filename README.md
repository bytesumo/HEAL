Forked from https://github.com/nsmryan/HEAL

RGEP Examples
=============

This repository will serve as my test of pulling together a worked example of RGEP, Robust Gene Expression Programming using the HEAL library.

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

An issue is that the monad-mersenne-random package is failing to build with this error:
```
/private/var/folders/th/cx3byth94rv223s8h6rfmnxc0000gn/T/stack44764/monad-mersenne-random-0.1/Control/Monad/Mersenne/Random.hs:50:10: error:
        • No instance for (Applicative Rand)
            arising from the superclasses of an instance declaration
        • In the instance declaration for ‘Monad Rand’
```
There is a fixed version (I hope!) here: https://github.com/Batou99/monad-mersenne-random.git
But to include it in the project, rather than the one on hackage, you need to do the following (according to this thread: https://www.reddit.com/r/haskell/comments/3rgq61/using_github_url_in_cabal_files_as_dependencies/)

To build and use this patched version, we need to set up a sandbox (local module) and build it so we can use it. I tried this:
```
cd ..
git clone https://github.com/Batou99/monad-mersenne-random.git
cd monad*
cabal sandbox init
cabal install --only-dependencies
cabal build
# now that patched version is built
cd rgep # change back to your project directory
cabal sandbox init # create a sandbox here too
sandbox add-source ../monad-mersenne-random
cabal install --only-dependencies
```
Now the dependencies to run the HEAL code should be satisfied by updating the cabal dependencies:

```
executable rgep
  hs-source-dirs:      src
  main-is:             Main.hs
  default-language:    Haskell2010
  build-depends:       base >= 4.7 && < 5, mersenne-random-pure64, monad-mersenne-random, containers
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
