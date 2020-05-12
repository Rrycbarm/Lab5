# Unit Testing Documentation template

Authors:

Date:

Version:

# Contents

- [Order Integers](#order-integers)
- [Calories](#calories)
- [Parallelogram](#parallelogram)

# Order Integers

## Criteria
  - Array not empty
  - Number of elements
  - Number of max elements
  
## Predicates 

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Array not empty | Array == null or Array.size() == 0
|    | Array != null and Array.size() > 0|
| Number of elements | N == 3 |
| | N < 3 |
| | N > 3 |
| Number of max elements | 1 max |
| | 2 max |
| | 3 max | 

## Boundaries 

| Criteria            | Boundary values             |
| ------------------- | --------------------------- | 

## Combination of predicates

| Array not empty | Number of elements | Number of max elements | Valid | Test|
| -- | -- | -- | -- | -- |
| False | - | - | Invalid | Array = null; Array = \[\] -> Error |
| True | < 3 | - | Invalid | Array = \[1, 2\] -> Error |
| | > 3 | - | Invalid | Array = \[1, 2, 3, 4\] -> Error |
| | 3 | 1 | Valid | Array = \[1, 2, 3\] -> 3|
| | | 2 | Valid | Array = \[4, 4, 2\]  -> 4|
| | | 3 | Valid | Array = \[5, 5, 5\] -> 5|

# Calories

# Parallelogram

