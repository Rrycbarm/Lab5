# Unit Testing Documentation template

Authors:

Date:

Version:

# Contents

- [Order Integers](#order-integers)
- [Calories](#calories)
- [Parallelogram](#parallelogram)
- [Inventory](#inventory)

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

## Criteria

- All values > 0
- Good calories
- Good ratio

## Predicates 

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| All values > 0 | Carb > 0 and Proteins > 0 and fat > 0 |
| Good calories | Calories < 1000 |
| Good ratio | 2* (Carb + proteins) > fat

## Boundaries

| Criteria            | Boundary values             |
| ------------------- | --------------------------- | 

## Combination of predicates

| All values > 0 | Good calories | Good ratio | Valid | Test |
| -- | -- | -- | -- | -- |
| False | - | - | Invalid | acceptableToEat(100, -2, 300) -> Error; acceptableToEat(100, 100, -300) -> Error; acceptableToEat(-100, 30, 300) -> Error |
| True | False | - | Valid | acceptableToEat(1001, 200, 300) -> False |
| | True | False | Valid | acceptableToEat(50, 50, 201) -> False |
| | | True | Valid | acceptableToEat(100, 100, 199) -> True | 

# Parallelogram

## Criteria

- Points in first quadrant  
- Well formed parallelogram
- Area > 0 

## Predicates 

| Criteria                  | Predicate    |
| ------------------------- | ------------ |
| Points in first quadrant | x1 > 0 && x2 > 0 && x3 > 0 && x4 > 0 && y1 > 0 && y2 > 0 && y3 > 0 && y4 > 0 |
| Well formed parallelogram | x1 - x2 == x3 - x4 && y1 - y2 == y3 - y4 && x1 - x3 = x2 - x4 && y1 - y3 == y2 - y4 |
| Area > 0 | result values always > 0 or -1 |

## Boundaries

| Criteria            | Boundary values             |
| ------------------- | --------------------------- | 

## Combination of predicates

| Points in first quadrant | Well formed parallelogram | Area > 0 | Valid | Test |
| -- | -- | -- | -- | -- |
| False | - | - | Invalid | paralleloogram(1, 2, 3, 4, -5, 6, 7, 8) -> -1 |
| True | False | - | Invalid | parallelogram(1, 5, 3, 4, 1, 1, 3, 10) -> -1 |
| | True | False | Invalid | - |
| | | True | Valid | parallelogram(1, 5, 4, 8, 3, 3, 7, 7) -> 16 |

# Inventory

## addItem(Item I)

### Criteria
- Item null
- Item exists already

### Predicates 

| Criteria | Predicate |
| -- | -- |
| Item null | Item == null |
| Item exits already | searchItem(Item.itemCode) == null |

### Combination of predicates
| Item null | Item exits already | Valid | Test |
| -- | -- | -- | -- |
| True | - | Invalid | addItem(null) -> Error |
| False | False | Valid | addItem(Item1)
| | True | Valid | addItem(Item1); addItem(Item1) -> exception |

## Item searchItem(String itemCode)

### Criteria
- String null
- Item exists

### Predicates
| Criteria | Predicate |
| -- | -- |
| String null | String == null |
| Item exits |  |

### Combination of predicates
| String null | Item exits | Valid | Test |
| -- | -- | -- | -- |
| True | - | Invalid | searchItem(null) -> Error |
| False | False | Valid | addItem(Item1); searchItem(Item1.itemcode) -> Item1 |
| | True | Valid | searchItem("abc") -> exception |

## int availabilityItem (String itemCode)

### Criteria
- String null
- Item exists

### Predicates
| Criteria | Predicate |
| -- | -- |
| String null | String == null |
| Item exits | searchItem(itemCode) != null |

### Combination of predicates
| String null | Item exits |Valid | Test |
| -- | -- | -- | -- |
| True | - | Invalid | availabilityItem(null) -> Error |
| False | False | Invalid | availabilityItem(Item) -> Exception |
| | True | Valid | addItem(Item); availability(Item.itemCode) -> Item.availability |

## void subtractItem (String itemCode)

### Criteria
- String null
- Item present 
- Quantity > 0

### Predicates
| Criteria | Predicate |
| -- | -- |
| String null | String == null |
| Item exits | searchItem(itemCode) != null |
| Quantity > 0 | availabilityItem(itemCode) > 0 |

### Combination of predicates
| String null | Item exits | Quantity > 0 |Valid | Test |
| -- | -- | -- | -- | -- |
| True | - | - | Invalid | subtractItem(null) -> Error |
| False | False | - | Invalid | subtractItem(Item) -> Exception |
| | True | False | Valid |Item.availability = 0; addItem(Item); subtractItem(Item) -> exception |
| | | True | Valid | Item.availability = 10;addItem(Item); subtractItem(Item) |

## void addQtyToItem(String itemCode, int qty_to_add);

### Criteria
- String null
- Item present 

### Predicates
| Criteria | Predicate |
| -- | -- |
| String null | String == null |
| Item exits | searchItem(itemCode) != null |

### Combination of predicates
| String null | Item exits |Valid | Test |
| -- | -- | -- | -- |
| True | - | Invalid | addQtyToItem(null, 1) -> Error |
| False | False | Invalid | addQtyToItem("abc", 1) -> Exception |
| | True | Valid | Item.availability = 5; addItem(Item); addQtyToItem(Item.itemCode, 10); availabilityItem(Item.itemCode) -> 15 |

## void subtractQtyToItem(String itemCode, int qty_to_add);

### Criteria
- String null
- Item present 
- New availability >= 0

### Predicates
| Criteria | Predicate |
| -- | -- |
| String null | String == null |
| Item exits | searchItem(itemCode) != null |
| New availability < 0 | availabilityItem(itemCode) - qty_to_add >= 0 |

### Combination of predicates
| String null | Item exits | New availability >= 0 | Valid | Test |
| -- | -- | -- | -- | -- |
| True | - | - | Invalid | subtractQtyToItem(null, 1) -> Error |
| False | False | - | Invalid | subtractQtyToItem("abc", 1) -> Exception |
| | True | False | Valid | Item.availabilty = 3; addItem(Item); subtractItem(Item.itemCode, 4) -> Error |
| | | True | Valid | Item.availabilty = 5; addItem(Item); subtractItem(Item.itemCode, 4); availabiltyItem(Item.itemCode) -> 1 |