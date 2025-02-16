[↑ Back](./README.md)

# `A201` - Selection

## Operators

### Reference

1. [Arithmetic Conditions](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/Arithmetic-Operators.html)

1. [Comparison Conditions](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/Comparison-Conditions.html)

### Exercises

1. Return the each **event** that is organized for women.
   
1. Return each **medal table entry** that has at least one gold medal.

1. Return each **medal table entry** that has the same number of gold medals and silver medals.
    
1. Return each **medal table entry** that has the same number of gold medals, silver medals, and bronze medals.

1. Return each **medal table entry** that has not gained any gold medals nor any silver medals.

1. Return each **medal table entry** that has not gained any gold medals nor silver medals but has bronze medals.

1. Return each **medal table entry** that has gained zero gold medals or silver medals but has bronze medals.

1. Return each **medal table entry** that has more than 10 gold medals, silver medals, and bronze medals (in total).

1. Return each medal table entry that has more than 10 gold medals, silver medals, and bronze medals (in total). Return the total number of medals as an additional column.

1. Return each medal table entry that has more than 10 gold medals, silver medals, and bronze medals (in total). Return the total number of medals as an additional column. Name the column as `total`.

## `BETWEEN` condition

### Reference

1. https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/BETWEEN-Condition.html

### Exercises

1. Return each **medal table entry** which number of gold medals is between `5` and `9`.

1. Return each **medal table entry** which gold medals is between the silver medals and bronze medals.

## `NULL` conditions

### Reference

1. https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/Null-Conditions.html

### Explanation

1. Expressions *unknown* and *missing* refer to the `NULL` values.
1. The equality operators does not work with `NULL` operands.
1. You can use the `IS` operator and the negated `IS NOT` construct for comparisons including `NULL` values.

### Exercises

1. Return each **event** which name is unknown.

1. Return each **event** which name is known.

1. Return each **gender** (only once) for which an event is scheduled with an unknown name.
