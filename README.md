# purescript-cheat-sheet
An a quick cheat sheet reference for PureScript syntax and features

## Operators

### Prelude Infix Operators

| Symbol          | Function                | Defined in                   | Meaning |
|-----------------|-------------------------|------------------------------|---------|
| `<$>`           | `map`                   | `Data.Functor`               |         |
| `<#>`           | `mapFlipped`            | `Data.Functor`               |         |
| `<$`            | `voidRight`             | `Data.Functor`               |         |
| `$>`            | `voidLeft`              | `Data.Functor`               |         |
| `<@>`           | `flap`                  | `Data.Functor`               |         |
| `<*>`           | `apply`                 | `Control.Apply`              |         |
| `<*`            | `applyFirst`            | `Control.Apply`              |         |
| `*>`            | `applySecond`           | `Control.Apply`              |         |
| `+`             | `add`                   | `Data.Semiring`              |         |
| `*`             | `mul`                   | `Data.Semiring`              |         |
| `-`             | `sub`                   | `Data.Ring`                  |         |
| `<`             | `lessThan`              | `Data.Ord`                   |         |
| `<=`            | `lessThanOrEq`          | `Data.Ord`                   |         |
| `>`             | `greaterThan`           | `Data.Ord`                   |         |
| `>=`            | `greaterThanOrEq`       | `Data.Ord`                   |         |
| `$`             | `apply`                 | `Data.Function`              |         |
| `#`             | `applyFlipped`          | `Data.Function`              |         |
| `>>=`           | `bind`                  | `Control.Bind`               |         |
| `=<<`           | `bindFlipped`           | `Control.Bind`               |         |
| `>=>`           | `composeKleisli`        | `Control.Bind`               |         |
| `<=<`           | `composeKleisliFlipped` | `Control.Bind`               |         |
| `/`             | `div`                   | `Control.EuclideanRing`      |         |
| `==`            | `eq`                    | `Data.Eq`                    |         |
| `/=`            | `notEq`                 | `Data.Eq`                    |         |
| `<<<`           | `compose`               | `Control.Semigroupoid`       |         |
| `>>>`           | `composeFlipped`        | `Control.Semigroupoid`       |         |
| `~>`            | `NaturalTransformation` | `Data.NaturalTransformation` |         |
| `&&`            | `conj`                  | `Data.HeytingAlgebra`        |         |
| `||`            | `disj`                  | `Data.HeytingAlgebra`        |         |
| `<>`            | `append`                | `Data.Semigroup`             |         |

