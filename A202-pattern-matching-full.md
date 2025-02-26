
[↑ Back](./README.md)

# `LIKE` condition (Pattern matching)

## Reference

1. [Pattern-matching Conditions](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/Pattern-matching-Conditions.html)

## Explanation

1. For you the `LIKE` is enough, we do not discuss the `LIKEC`, `LICE2`, and `LIKE4` keywords.
1. Placeholders `_` and `%` must be known.

## Exercises

1. Return each **country** which name matches `Albania`.

   ```sql
   SELECT *
   FROM o_countries
   WHERE name LIKE 'Albania';
   ```

1. Return each **country** which name starts with the letter `A`.

   ```sql
   SELECT *
   FROM o_countries
   WHERE name LIKE 'A%';
   ```

1. Return each **country** which name starts with the letter `A`, continues with a custom character, then ends with the sequence `gola`.

   ```sql
   SELECT *
   FROM o_countries
   WHERE name LIKE 'A_gola';
   ```

1. Return each **country** which name ends with the sequence `istan`.

   ```sql
   SELECT *
   FROM o_countries
   WHERE name LIKE '%istan';
   ```

1. Return each **country** which name starts with the letter `A`, and ends with the sequence `istan`.

   ```sql
   SELECT *
   FROM o_countries
   WHERE name LIKE 'A%istan';
   ```

1. Return each **country** which name starts with the letter `A`, ends with the letter `a`, and exactly `5` letters long.

   ```sql
   SELECT *
   FROM o_countries
   WHERE name LIKE 'A___a';
   ```
    
1. Return each **country** which name starts with the letter `A` and at least `8` letters long.

   ```sql
   SELECT *
   FROM o_countries
   WHERE name LIKE 'A_______%';
   ```
    
1. Return each **country** which name starts with the sequence `Aust` and ends with the sequence `ia`.

   ```sql
   SELECT *
   FROM o_countries
   WHERE name LIKE 'Aust%ia';
   ```
    
1. Return each **country** which area starts with the digit `3`.

   ```sql
   SELECT *
   FROM o_countries
   WHERE area LIKE '3%';
   ```
