[↑ Back](./README.md)

# `C101` - Subselects, vector (1D) result

## Schema diagram

![Schema diagram](./img/olympics-schema.png)

## Exercises

1. Return each African **country name** that starts with the same letter as any European country name.

   ```sql
   SELECT name
   FROM o_countries
   WHERE continent = 'Africa'
   AND SUBSTR(name, 1, 1) IN (
      SELECT DISTINCT SUBSTR(name, 1, 1)
      FROM o_countries
      WHERE continent = 'Europe'
   );
   ```

1. Return each African **country name** that does not start with the same letter as any European country name.

   ```sql
   SELECT name
   FROM o_countries
   WHERE continent = 'Africa'
   AND SUBSTR(name, 1, 1) NOT IN (
      SELECT DISTINCT SUBSTR(name, 1, 1)
      FROM o_countries
      WHERE continent = 'Europe'
   );
   ```

1. Return the **name** of each country that scored `51`, `36` or `14` gold medals.

   ```sql
   SELECT name
   FROM o_medal_table
   JOIN o_countries ON c_id = country_id
   WHERE gold IN (51, 36, 14);
   ```

1. Return each value which appears in the gold and in the bronze column too.

   ```sql
   SELECT DISTINCT gold
   FROM o_medal_table
   WHERE gold IN (
      SELECT bronze
      FROM o_medal_table
   );
   ```

1. Return each value which appears in the gold column, while does not appear in the bronze column.

   ```sql
   SELECT DISTINCT gold
   FROM o_medal_table
   WHERE gold NOT IN (
      SELECT bronze
      FROM o_medal_table
   );
   ```

1. Return the **name** and the **gold medals** of each country that scored as many medals as a country whose name starts with the letter `R`. Do not return any country whose name starts with the letter `R`.

   ```sql
   SELECT name, gold
   FROM o_medal_table
         JOIN o_countries ON c_id = country_id
   WHERE
      gold IN (
      SELECT DISTINCT gold
      FROM o_medal_table
               JOIN o_countries ON c_id = country_id
      WHERE SUBSTR(name, 1, 1) = 'R'
   ) AND name NOT LIKE 'R%';
   ```
