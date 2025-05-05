[↑ Back](./README.md)

# `C202` - Conditions `ANY`, `ALL`, and `EXISTS`

## Schema diagram

![Schema diagram](./img/olympics-schema.png)

## Reference

1. [`ANY` Condition](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/ANY-Condition.html)
1. [`ALL` Condition](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/ALL-Condition.html)
1. [`EXISTS` Condition](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/EXISTS-Condition.html)

## Exercises

1. Return the **ID** and **name** of each country that has any medals (thus, it appears in the `o_medal_table` table).

   ```sql
   SELECT c_id, name
   FROM o_countries
   WHERE EXISTS (
      SELECT *
      FROM o_medal_table
      WHERE c_id = country_id
   );
   ```

   ```sql
   SELECT c_id, NAME
   FROM o_countries
   WHERE c_id IN (
      SELECT country_id
      FROM o_medal_table
   );
   ```

1. Return **each country** that is the most populous on its continent.

   ```sql
   SELECT *
   FROM o_countries a
   WHERE population = (
      SELECT MAX(population)
      FROM o_countries b
      WHERE a.continent = b.continent
   );
   ```
   
   ```sql
   SELECT *
   FROM o_countries a
   WHERE population IS NOT NULL
      AND continent IS NOT NULL
      AND population >= ALL (
         SELECT NVL(b.population, 0)
         FROM o_countries b
         WHERE a.population IS NOT NULL
         AND a.continent = b.continent
      );
   ```

1. Return **each country** that has greater population than one of the European countries has.

   ```sql
   SELECT *
   FROM o_countries a
   WHERE a.population > ANY (
      SELECT NVL(b.population, 0)
      FROM o_countries b
      WHERE b.continent = 'Europe'
   );
   ```

   ```sql
   SELECT *
   FROM o_countries a
   WHERE EXISTS (
      SELECT NVL(b.population, 0)
      FROM o_countries b
      WHERE b.continent = 'Europe' AND b.population < a.population
   );
   ```

1. Return **each country** that has greater population than all of the European countries has.
    
   ```sql
   SELECT *
   FROM o_countries a
   WHERE a.population > ALL (
      SELECT NVL(b.population, 0)
      FROM o_countries b
      WHERE b.continent = 'Europe'
   );
   ```

   ```sql
   SELECT *
   FROM o_countries a
   WHERE NOT EXISTS (
      SELECT NVL(b.population, 0)
      FROM o_countries b
      WHERE b.continent = 'Europe' AND NVL(b.population, 0) >= NVL(a.population, 0)
   );
   ```

1. Return **each country** name which first letter stands in the alphabetic order after all the European countries' first letters.

   ```sql
   SELECT name
   FROM o_countries
   WHERE SUBSTR(name, 1, 1) > ALL (
      SELECT SUBSTR(name, 1, 1)
      FROM o_countries
      WHERE continent = 'Europe'
   );
   ```

1. Return the **name** and the **gold medals** of each country that has more gold medals than at least one European country has.

   ```sql
   SELECT name, bronze
   FROM o_countries
      JOIN o_medal_table
         ON c_id = country_id
   WHERE bronze > ANY (
      SELECT bronze
      FROM o_countries
         JOIN o_medal_table ON c_id = country_id
      WHERE continent = 'Europe'
   );
   ```

1. Return the **name** and the **gold medals** of each country that has more gold medals than all the European countries.

   ```sql
   SELECT name, bronze
   FROM o_countries
      JOIN o_medal_table ON c_id = country_id
   WHERE bronze > ALL (
      SELECT bronze
      FROM o_countries
         JOIN o_medal_table ON c_id = country_id
      WHERE continent = 'Europe'
   );
   ```
