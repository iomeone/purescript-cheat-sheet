# <img src="https://rawgithub.com/purescript/logo/master/favicon/purescript-favicon-black.svg" width="48"> Purescript Cheat Sheet

## Table of Contents

1. [Language Summary](#language-summary)
2. [Benefits](#benefits)
3. [Hello World](#hello-world)
    * [Example Using Smolder](#example-using-smolder)
4. [Comments](#comments)
5. [Operators](#operators)
    * [Prelude Infix Operators](#prelude-infix-operators)
6. [Modules](#modules)
    * [Defining Modules](#defining-modules)
    * [Importing Modules](#importing-modules)

## Language Summary

 * A strongly-typed functional programming language that compiles to JavaScript
 * Features Hindley-Milner type annotations & top-level type inference
 * Compiles to easy to read, easy to understand JavaScript code
 * Very similar to Haskell in many ways, but strictly evaluated
 * Similar to Elm, but offers more advanced type features, like type classes, and can be used for both UI & server-side programming

## Benefits

* Compile to readable JavaScript and reuse existing JavaScript code easily
* An extensive collection of libraries for development of web applications, web servers, apps and more
* Excellent tooling and editor support with instant rebuilds
* An active community with many learning resources
* Build real-world applications using functional techniques and expressive types, such as:
    * Algebraic data types and pattern matching
    * Row polymorphism and extensible records
    * Higher kinded types
    * Type classes with functional dependencies
    * Higher-rank polymorphism

## Hello World

### Example Using Smolder

File `HelloWorld.purs`:
```purescript
import Prelude
import Text.Smolder (html, lang, h1, text)

-- Hello world example
main = html ! lang "en" $ do
  h1 $ text "Hello World!"
```

## Comments
```purescript
-- Single line comment

{-
Multi-line comment
-}
```

## Operators

### Prelude Infix Operators

| Symbol          | Function                | Defined in                   | Meaning                      
|-----------------|-------------------------|------------------------------|------------------------------
| `<$>`           | `map`                   | `Data.Functor`               | `map` can be used to turn functions `a -> b` into functions `f a -> f b` whose argument and return types use the type constructor `f`, where `f` is a Functor.       
| `<#>`           | `mapFlipped`            | `Data.Functor`               | `mapFlipped` is `map` with its arguments reversed.    
| `<$`            | `voidRight`             | `Data.Functor`               | Ignore the return value of a computation, using the specified return value.        
| `$>`            | `voidLeft`              | `Data.Functor`               | A version of `voidRight` with its arguments flipped.        
| `<@>`           | `flap`                  | `Data.Functor`               | Apply a value in a computational context to a value in no context. Generalizes `flip`. (Flips the order of the arguments to a function of two arguments)        
| `<*>`           | `apply`                 | `Control.Apply`              | `apply` is used to apply a function to an argument under a type constructor.        
| `<*`            | `applyFirst`            | `Control.Apply`              | Combine two effectful actions, keeping only the result of the first.        
| `*>`            | `applySecond`           | `Control.Apply`              | Combine two effectful actions, keeping only the result of the second.        
| `$`             | `apply`                 | `Data.Function`              | Applies an argument to a function, allowing parentheses to be ommitted in some cases. (Like `<\|` in Elm, F#, etc.)       
| `#`             | `applyFlipped`          | `Data.Function`              | `applyFlipped` is `apply` with its arguments reversed. (Like `\|>` in Elm, F#, etc.)    
| `<<<`           | `compose`               | `Control.Semigroupoid`       | Backwards composition. Used for composing pure functions.        
| `>>>`           | `composeFlipped`        | `Control.Semigroupoid`       | Forwards composition, or `compose` with its arguments reversed.      
| `>>=`           | `bind`                  | `Control.Bind`               | `bind` composes computations in sequence, using the return value of one computation to determine the next computation.        
| `=<<`           | `bindFlipped`           | `Control.Bind`               | `bindFlipped` is `bind` with its arguments reversed.        
| `>=>`           | `composeKleisli`        | `Control.Bind`               | Forwards Kleisli composition. Used for composing monadic functions of type `(a -> m b)` and `(b -> m c)`.        
| `<=<`           | `composeKleisliFlipped` | `Control.Bind`               | Backwards Kleisli composition, or `composeKleisli` with its arguments flipped.        
| `~>`            | `NaturalTransformation` | `Data.NaturalTransformation` | A natural transformation is a mapping between type constructors of kind `* -> *` where the mapping operation has no ability to manipulate the inner values.         
| `<>`            | `append`                | `Data.Semigroup`             | Concatenate two Semigroup values. (Example: String concatenation)       
| `&&`            | `conj`                  | `Data.HeytingAlgebra`        | Boolean AND                   
| `\|\|`          | `disj`                  | `Data.HeytingAlgebra`        | Boolean OR                  
| `==`            | `eq`                    | `Data.Eq`                    | Equality check               
| `/=`            | `notEq`                 | `Data.Eq`                    | Inequality check             
| `<`             | `lessThan`              | `Data.Ord`                   | Less than                    
| `<=`            | `lessThanOrEq`          | `Data.Ord`                   | Less than or equal           
| `>`             | `greaterThan`           | `Data.Ord`                   | Greater than                 
| `>=`            | `greaterThanOrEq`       | `Data.Ord`                   | Greater than or equal        
| `+`             | `add`                   | `Data.Semiring`              | Addition             
| `*`             | `mul`                   | `Data.Semiring`              | Multiplication       
| `-`             | `sub`                   | `Data.Ring`                  | Subtraction          
| `/`             | `div`                   | `Control.EuclideanRing`      | Division             


## Modules

### Defining Modules

```purescript
-- Defining a module that exports everything
module Mymodule where

-- Export only specified entities
module Mymodule (Type, value) where

-- Export all or specific states of type
module Mymodule 
  ( Error(Forbidden, Timeout)
  , Stuff(..)
  ) where

type Error
  = Forbidden String
  | Timeout String
  | NotFound String
```

#### Importing Modules
```purescript
-- qualified imports

-- unqualified imports
```
