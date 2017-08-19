# purescript-cheat-sheet
A quick reference sheet for PureScript syntax and features

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

