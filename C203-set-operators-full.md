[↑ Back](./README.md)

# `C203` - Set Operators

## Schema diagram

![Schema diagram](./img/olympics-schema.png)

## Reference

1. [The Set Operators](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/The-UNION-ALL-INTERSECT-MINUS-Operators.html)

## Exercises

1. Return **each value** that both appears in the `gold` and `bronze` columns of the medal table.

   1. Solve the exercise without using set operators.

      ```sql
      SELECT DISTINCT gold
      FROM o_medal_table
      WHERE gold IN (
         SELECT bronze
         FROM o_medal_table
      );
      ```

   1. Solve the exercise using set operators.

      ```sql
      SELECT gold
      FROM o_medal_table
      INTERSECT
      SELECT bronze
      FROM o_medal_table;
      ```

1. Return **each value** that appears in the `gold` or `bronze` column of the medal table.

   ```sql
   SELECT gold
   FROM o_medal_table
   UNION
   SELECT bronze
   FROM o_medal_table;
   ```

1. Return **each value** that appears in the `gold` column but does not appear in the `bronze` column of the medal table.

   1. Solve the exercise without using set operators.

      ```sql
      SELECT DISTINCT gold
      FROM o_medal_table
      WHERE gold NOT IN (
         SELECT bronze
         FROM o_medal_table
      );
      ```

   1. Solve the exercise using set operators.

      ```sql
      SELECT gold
      FROM o_medal_table
      MINUS
      SELECT bronze
      FROM o_medal_table;
      ```

1. Return **each value** that appears in the `bronze` column but does not appear in the `gold` column of the medal table.

   1. Solve the exercise without using set operators.

      ```sql
      SELECT DISTINCT bronze
      FROM o_medal_table
      WHERE bronze NOT IN (
         SELECT gold
         FROM o_medal_table
      );
      ```

   1. Solve the exercise using set operators.

      ```sql
      SELECT bronze
      FROM o_medal_table
      MINUS
      SELECT gold
      FROM o_medal_table;
      ```

1. Return **each letter** that appears as the first letter of any country name but does not appear as the first letter of any continent.

   1. Solve the exercise without using set operators. 

      ```sql
      SELECT DISTINCT SUBSTR(name, 1, 1)
      FROM o_countries
      WHERE SUBSTR(name, 1, 1) NOT IN (
         SELECT SUBSTR(continent, 1, 1)
         FROM o_countries
         WHERE continent IS NOT NULL
      );
      ```
      
   1. Solve the exercise using set operators.

      ```sql
      SELECT SUBSTR(name, 1, 1)
      FROM o_countries
      MINUS
      SELECT SUBSTR(continent, 1, 1)
      FROM o_countries;
      ```

1. Return **each letter** that appears as the first letter of any country name but does not appear as the first letter of any continent. Order the rows in ascending order.

   1. Solve the exercise without using set operators.

      ```sql
      SELECT DISTINCT SUBSTR(name, 1, 1)
      FROM o_countries
      WHERE SUBSTR(name, 1, 1) NOT IN (
         SELECT SUBSTR(continent, 1, 1)
         FROM o_countries
         WHERE continent IS NOT NULL
      )
      ORDER BY 1;
      ```

      Check it without the subquery's condition!

   1. Solve the exercise using set operators.

      ```sql
      SELECT SUBSTR(name, 1, 1)
      FROM o_countries
      MINUS
      SELECT SUBSTR(continent, 1, 1)
      FROM o_countries
      ORDER BY 1;
      ```

1. Return **each letter** that appears as the first letter of any European country name but does not appear as the first letter of any African country name.

   1. Solve the exercise without using set operators.

      ```sql
      SELECT DISTINCT SUBSTR(name, 1, 1)
      FROM o_countries
      WHERE continent = 'Europe' AND SUBSTR(name, 1, 1) NOT IN (
         SELECT SUBSTR(name, 1, 1)
         FROM o_countries
         WHERE continent = 'Africa'
      );
      ```

   1. Solve the exercise using set operators.

      ```sql
      SELECT SUBSTR(name, 1, 1)
      FROM o_countries
      WHERE continent = 'Europe'
      MINUS
      SELECT SUBSTR(name, 1, 1)
      FROM o_countries
      WHERE continent = 'Africa';
      ```

1. Return **each letter** that both appears as the first letter of any European and any African country name.

   1. Solve the exercise without using set operators.

      ```sql
      SELECT DISTINCT SUBSTR(name, 1, 1)
      FROM o_countries
      WHERE continent = 'Europe' AND SUBSTR(name, 1, 1) IN (
         SELECT SUBSTR(name, 1, 1)
         FROM o_countries
         WHERE continent = 'Africa'
      );
      ```

   1. Solve the exercise using set operators.

      ```sql
      SELECT SUBSTR(name, 1, 1)
      FROM o_countries
      WHERE continent = 'Europe'
      INTERSECT
      SELECT SUBSTR(name, 1, 1)
      FROM o_countries
      WHERE continent = 'Africa';
      ```
