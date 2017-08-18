# <img src="http://www.purescript.org/img/logo.svg" width="26" > Purescript Cheat Sheet

## Table of Contents

1. [Hello World](#hello-world)
2. [Comments](#comments)
3. [Operators](#operators)
3. [Modules](#modules)
    * [Imports](#imports)

## Hello World
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

| Symbol          | Function                | Defined in                   | Meaning                      
|-----------------|-------------------------|------------------------------|------------------------------
| `<$>`           | `map`                   | `Data.Functor`               | `map` can be used to turn functions `a -> b` into functions `f a -> f b` whose argument and return types use the type constructor `f`, where `f` is a Functor.       
| `<#>`           | `mapFlipped`            | `Data.Functor`               | `mapFlipped` is `map` with its arguments reversed.    
| `<$`            | `voidRight`             | `Data.Functor`               | Ignore the return value of a computation, using the specified return value.        
| `$>`            | `voidLeft`              | `Data.Functor`               | A version of `voidRight` with its arguments flipped.        
| `<@>`           | `flap`                  | `Data.Functor`               | Apply a value in a computational context to a value in no context. Generalizes `flip`. (Flips the order of the arguments to a function of two arguments)        
| `<*>`           | `apply`                 | `Control.Apply`              | `apply` is used to apply a function to an argument under a type constructor.        
| `<*`            | `applyFirst`            | `Control.Apply`              | Combine two effectful actions, keeping only the result of the second.        
| `*>`            | `applySecond`           | `Control.Apply`              | Combine two effectful actions, keeping only the result of the second.        
| `$`             | `apply`                 | `Data.Function`              | Applies an argument to a function, allowing parentheses to be ommitted in some cases.        
| `#`             | `applyFlipped`          | `Data.Function`              | `applyFlipped` is `apply` with its arguments reversed.        
| `<<<`           | `compose`               | `Control.Semigroupoid`       | Backwards composition. Used for composing pure functions.        
| `>>>`           | `composeFlipped`        | `Control.Semigroupoid`       | Forwards composition, or `compose` with its arguments reversed.      
| `>>=`           | `bind`                  | `Control.Bind`               | `bind` composes computations in sequence, using the return value of one computation to determine the next computation.        
| `=<<`           | `bindFlipped`           | `Control.Bind`               | `bindFlipped` is `bind` with its arguments reversed.        
| `>=>`           | `composeKleisli`        | `Control.Bind`               | Forwards Kleisli composition. Used for composing monadic functions of type `(a -> m b)` and `(b -> m c)`.        
| `<=<`           | `composeKleisliFlipped` | `Control.Bind`               | Backwards Kleisli composition, or `composeKleisli` with its arguments flipped.        
| `~>`            | `NaturalTransformation` | `Data.NaturalTransformation` | A natural transformation is a mapping between type constructors of kind `* -> *` where the mapping operation has no ability to manipulate the inner values.         
| `<>`            | `append`                | `Data.Semigroup`             | Concatenate two Semigroup values. (Example: String concatenation)       
| `&&`            | `conj`                  | `Data.HeytingAlgebra`        | Boolean OR                   
| `\|\|`          | `disj`                  | `Data.HeytingAlgebra`        | Boolean AND                  
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

#### Imports
```purescript
-- qualified imports

-- unqualified imports
```
