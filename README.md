# purescript-cheat-sheet
An a quick cheat sheet reference for PureScript syntax and features

## Operators

### Prelude Infix Operators

| Symbol          | Function                | Defined in                   | Meaning                      |
|-----------------|-------------------------|------------------------------|------------------------------|
| `<$>`           | `map`                   | `Data.Functor`               |         |
| `<#>`           | `mapFlipped`            | `Data.Functor`               |         |
| `<$`            | `voidRight`             | `Data.Functor`               |         |
| `$>`            | `voidLeft`              | `Data.Functor`               |         |
| `<@>`           | `flap`                  | `Data.Functor`               |         |
| `<*>`           | `apply`                 | `Control.Apply`              |         |
| `<*`            | `applyFirst`            | `Control.Apply`              |         |
| `*>`            | `applySecond`           | `Control.Apply`              |         |
| `$`             | `apply`                 | `Data.Function`              |         |
| `#`             | `applyFlipped`          | `Data.Function`              |         |
| `<<<`           | `compose`               | `Control.Semigroupoid`       |         |
| `>>>`           | `composeFlipped`        | `Control.Semigroupoid`       |         |
| `>>=`           | `bind`                  | `Control.Bind`               |         |
| `=<<`           | `bindFlipped`           | `Control.Bind`               |         |
| `>=>`           | `composeKleisli`        | `Control.Bind`               |         |
| `<=<`           | `composeKleisliFlipped` | `Control.Bind`               |         |
| `~>`            | `NaturalTransformation` | `Data.NaturalTransformation` |         |
| `<>`            | `append`                | `Data.Semigroup`             | String concatenation         |
| `&&`            | `conj`                  | `Data.HeytingAlgebra`        | Boolean OR                   |
| `\|\|`          | `disj`                  | `Data.HeytingAlgebra`        | Boolean AND                  |
| `==`            | `eq`                    | `Data.Eq`                    | Equality check               |
| `/=`            | `notEq`                 | `Data.Eq`                    | Inequality check             |
| `<`             | `lessThan`              | `Data.Ord`                   | Less than                    |
| `<=`            | `lessThanOrEq`          | `Data.Ord`                   | Less than or equal           |
| `>`             | `greaterThan`           | `Data.Ord`                   | Greater than                 |
| `>=`            | `greaterThanOrEq`       | `Data.Ord`                   | Greater than or equal        |
| `+`             | `add`                   | `Data.Semiring`              | Numeric addition             |
| `*`             | `mul`                   | `Data.Semiring`              | Numeric multiplication       |
| `-`             | `sub`                   | `Data.Ring`                  | Numeric subtraction          |
| `/`             | `div`                   | `Control.EuclideanRing`      | Numeric division             |

