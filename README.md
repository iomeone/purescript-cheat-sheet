# <img src="https://rawgithub.com/purescript/logo/master/favicon/purescript-favicon-black.svg" width="48"> Purescript Cheat Sheet

## Table of Contents

* [Language Summary](#language-summary)
* [Benefits](#benefits)
* [Getting Started](#getting-started)
* [Hello World](#hello-world)
    * [Getting Started](#getting-started)
    * [Simple Logging Example](#simple-logging-example)
    * [Example Using Smolder](#example-using-smolder)
    * [Simple Module Example](#simple-module-example)
* [Comments](#comments)
* [Operators](#operators)
    * [Infix Notation](#infix-notation)
    * [Prefix Notation](#prefix-notation)
    * [Prelude Infix Operators](#prelude-infix-operators)
* [Modules](#modules)
    * [Defining Modules](#defining-modules)
    * [Importing Modules](#importing-modules)

## Language Summary

 * A strongly-typed, pure functional programming language that compiles to JavaScript
 * Features Hindley-Milner type annotations & top-level type inference
 * Compiles to easy to read, easy to understand JavaScript code
 * Very similar to Haskell in many ways, but strictly evaluated
 * Similar to Elm, but offers more advanced type features, like type classes & higher-kinded polymorphism, and can be used for both UI & server-side programming

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


## Getting Started

1. `npm i -g purescript pulp bower` to install PureScript, Pulp, & Bower
2. `mkdir purescript-app` to create a directory for your PureScript app
3. `cd purescript-app` to move into the new directory
4. `pulp init` will generate a boilerplate PureScript project for you to modify as you see fit
5. `pulp run` will build and run the project, logging out `Hello Sailor!` in your terminal

## Hello World

### Simple Logging Example

```purescript
module Main where

import Prelude
import Control.Monad.Eff (Eff)
import Control.Monad.Eff.Console (CONSOLE, log)

main :: forall e. Eff (console :: CONSOLE | e) Unit
main = do
  log "Hello, world!"
```

### Example Using Smolder

```purescript
module Main where

import Prelude

import Control.Monad.Eff (Eff)
import Control.Monad.Eff.Console (CONSOLE, log)
import Text.Smolder.HTML (html, h1)
import Text.Smolder.HTML.Attributes (lang)
import Text.Smolder.Markup (Markup, text, (!))
import Text.Smolder.Renderer.String (render)

doc :: forall e. Markup e
doc = html ! lang "en" $ do
  h1 $ text "Hello, world!"

main :: forall eff. Eff (console :: CONSOLE | eff ) Unit
main = log $ render doc
```

### Simple Module Example

```purescript
module HelloWorld where

import Prelude
import Data.Maybe (Maybe(Just, Nothing))

helloWorld :: Maybe String -> String
helloWorld Nothing = "Hello, world!"
helloWorld (Just x) = "Hello, " <> x <> "!"
```

## Comments

A single line comment starts with `--`:

``` purescript
-- This is a comment
```

Multi-line comments are enclosed in `{-` and `-}`:

``` purescript
{-
  Comment
  continued comment
-}
```

Comments that start with a pipe character, `|`, are considered documentation, and will appear in the output of tools like `psc-docs` and Pursuit. For example:

``` purescript
-- | `bool` performs case analysis for the `Boolean` data type, like an `if` statement.
bool :: forall a. Boolean -> a -> a -> a
bool true x _ = x
bool false _ x = x
```

Note that, unlike Haskell, every line which should be considered documentation must start with a pipe. This allows you to do things like:

``` purescript
-- | Sort an array based on its `Ord` instance.
-- |
-- | This implementation runs in `O(n^2)` time, where `n` is the length of the
-- | input array.
-- TODO: try to optimise this?
sort :: forall a. (Ord a) => Array a -> Array a
sort xs = [...]
```

## Operators

### Infix Notation

Functions in PureScript can alternatively be used with infix notation by wrapping them in backticks. For example,

```purescript
import Prelude
import Data.List (List, range)

ns :: List Int
ns = range 0 999
```

can also be written like this:

```purescript
import Prelude
import Data.List (List, range)

ns :: List Int
ns = 0 `range` 999
```

However, many functions have infix operators defined for convenience. For example, `range` has the `..` operator. The following is equivalent to the above example:

```purescript
import Prelude
import Data.List (List, (..))

ns :: List Int
ns = 0 .. 999
```

You can also define your own custom infix operators. For example, you might define `<$?>` as a custom infix operator for `filter`:

```purescript
import Prelude
import Data.List (List, (..), filter)

infixl 4 filter as <$?>

ns :: List Int
ns = 0 .. 999

multiples :: List Int
multiples = (\n -> mod n 3 == 0 || mod n 5 == 0) <$?> ns
```

### Prefix Notation

Infix operators can alternatively be used with prefix notation by wrapping them in parenthesis. For example,

```purescript
import Prelude

n :: Int
n = 3 + 5
```

can also be written like this:

```purescript
import Prelude

n :: Int
n = (+) 3 5
```

Whether you're using normal function syntax or operator symbols, or infix or prefix notation, you're really just using functions in various forms. It's up to you to use them how you see fit. Use whichever form you feel makes the code you're writing most readable.


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

#### Defining Modules
```purescript
-- Defining a module that exports everything
module MyModule where

-- Export only specified entities
module MyModule
  ( Type
  , value
  ) where

-- Export all or specific states of type
module MyModule
  ( Error(Forbidden, Timeout)
  , Stuff(..)
  , Person
  , class Something
  ) where

data Error
  = Forbidden String
  | Timeout String
  | NotFound String

data Stuff
  = Tag
  | SomeTag
  | AnotherTag

type Person = { name :: String, age :: Int }

class Something a where
  show :: a -> String
```

#### Importing Modules

##### Qualified Imports
```purescript
import Prelude
-- For Prelude, all imports are in scope

import Prelude hiding (div)
-- For Prelude, all imports are in scope except div

import Data.List (Nil)
-- For Data.List, Nil type is in scope

import Data.Array as A
-- For Data.Array, all imports are in scope with the A namespace

import Data.List as L
-- For Data.List, all imports are in scope with the L namespace


Example Usage:
list = 1 L.: 2 L.: 3 L.: Nil
array = 1 A.: 2 A.: 3 A.: []
```

##### Unqualified imports
```purescript
import Data.List ((:))
-- For Data.List, : is in scope

import MyModule (someFunction, someType(..), someType(Tag, AnotherTag), class SomeClass)
-- For MyModule, only the function, types, and class mentioned are in scope
```
