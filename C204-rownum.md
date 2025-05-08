[↑ Back](./README.md)

# `C204` - `ROWNUM` Pseudocolumn

## Schema diagram

![Schema diagram](./img/olympics-schema.png)

## Reference

1. [`ROWNUM` Pseudocolumn](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/ROWNUM-Pseudocolumn.html)

## Workaround

1. Return the **ID**, the **name**, and the **area** of each country. Return the value of the `ROWNUM` column.

   ```sql
   SELECT ROWNUM, c_id, name, area
   FROM o_countries;
   ```

1. Return the first `5` countries. Return the value of the `ROWNUM` column.

   ```sql
   SELECT ROWNUM, c_id, name, area
   FROM o_countries
   WHERE ROWNUM <= 5;
   ```

1. Return the **fifth country**.
   
   ```sql
   SELECT ROWNUM, c_id, name, area
   FROM o_countries
   WHERE ROWNUM = 5;
   ```

   This query does not work.

1. Return **each country** except the first four countries. 

   ```sql
   SELECT ROWNUM, c_id, name, area
   FROM o_countries
   WHERE ROWNUM >= 5;
   ```

   This query does not work.

1. Return **each country** having one of the `5` greatest areas.

   ```sql
   SELECT ROWNUM, c_id, name, area
   FROM o_countries
   WHERE ROWNUM <= 5
   ORDER BY area;
   ```

   This query does not work.

1. Return the **ID**, the **name**, and the **area** of each country. Order the countries by their areas in descending order. Return the value of the `ROWNUM` column.
   
   ```sql
   SELECT ROWNUM, c_id, name, NVL(area, 0)
   FROM o_countries
   ORDER BY NVL(area, 0) DESC;
   ```

   This does not how we expect.

## Exercises

1. Return **each country** having one of the `5` greatest areas.

   ```sql
   SELECT *
   FROM (
      SELECT *
      FROM o_countries
      ORDER BY area DESC NULLS LAST
   )
   WHERE ROWNUM <= 5;
   ```

1. Return **the country** having the fifth greatest area.

   ```sql
   SELECT *
   FROM (
      SELECT ROWNUM AS position, sub.*
      FROM (
         SELECT *
         FROM o_countries
         ORDER BY area DESC NULLS LAST
      ) sub
   )
   WHERE position = 5;
   ```

1. Return **each country** whose population is less than the population of the country having the fifth greatest area.

   ```sql
   SELECT *
   FROM o_countries
   WHERE population < (
      SELECT population
      FROM (
         SELECT ROWNUM AS position, sub.*
         FROM (
            SELECT *
            FROM o_countries
            ORDER BY area DESC NULLS LAST
         ) sub
      )
      WHERE position = 5
   );
   ```

1. Return the **name** and the **gold medals** of each country that scored one of the five greatest gold medals.

   ```sql
   SELECT *
   FROM (
      SELECT name, gold
      FROM o_countries
         JOIN o_medal_table ON c_id = country_id
      ORDER BY gold DESC
   ) sub
   WHERE ROWNUM <= 5;
   ```

1. Return **each country** that scored the least number of medals.

   ```sql
   SELECT o_countries.*
   FROM o_countries
      JOIN o_medal_table ON c_id = country_id
   WHERE gold + silver + bronze = (
      SELECT *
      FROM (
         SELECT DISTINCT gold + silver + bronze
         FROM o_medal_table
         ORDER BY gold + silver + bronze
      ) sub
      WHERE ROWNUM = 1
   );
   ```
    
1. Return **each country** that scored one of the least `5` medals.

   ```sql
   SELECT o_countries.*
   FROM o_countries
      JOIN o_medal_table ON c_id = country_id
   WHERE gold + silver + bronze IN (
      SELECT *
      FROM (
         SELECT DISTINCT gold + silver + bronze
         FROM o_medal_table
         ORDER BY gold + silver + bronze
      ) sub
      WHERE ROWNUM <= 5
   );
   ```

1. Return the **name** and the **area** of each African country which area is greater than the 5th greatest European area and less than the 3rd greatest Asian area.

   ```sql
   SELECT name, area
   FROM o_countries
   WHERE continent = 'Africa'
      AND area > (
         SELECT area
         FROM (
            SELECT ROWNUM AS position,
                  area
            FROM (
               SELECT area
               FROM o_countries
               WHERE continent = 'Europe'
               ORDER BY 1 DESC
            )
         )
         WHERE position = 5
      )
      AND area < (
         SELECT area
         FROM (
            SELECT ROWNUM AS position,
                  area
            FROM (
               SELECT area
               FROM o_countries
               WHERE continent = 'Asia'
               ORDER BY 1 DESC
            )
         )
         WHERE position = 3
   );
   ```

1. Return the **ID**, the **name**, the **place**, and the **medals** of each country. Return the value of `0` instead of all the `NULL` values. Order the table to be a real medal table. If two countries scored the same amount of medals, order them by their names.

   ```sql
   SELECT ROWNUM AS position, c_id, name, NVL(gold, 0), NVL(silver, 0), NVL(bronze, 0)
   FROM (
      SELECT *
      FROM o_countries
         LEFT JOIN o_medal_table ON c_id = country_id
      ORDER BY NVL(gold, 0) DESC, NVL(silver, 0) DESC, NVL(bronze, 0) DESC, name
   );
   ```

1. Return the **place** of Cuba based on the previous query.

   ```sql
   SELECT position
   FROM (
      SELECT ROWNUM AS position, c_id, name, NVL(gold, 0), NVL(silver, 0), NVL(bronze, 0)
      FROM (
         SELECT *
         FROM o_countries
            LEFT JOIN o_medal_table ON c_id = country_id
         ORDER BY NVL(gold, 0) DESC, NVL(silver, 0) DESC, NVL(bronze, 0) DESC, name
      )
   )
   WHERE name = 'Cuba';
   ```

1. Return the **ID**, the **name**, the **place**, and the **medals** of each country whose position precedes or follows Cuba by at most two places.

   ```sql
   SELECT *
   FROM (
      SELECT ROWNUM AS position, c_id, name, NVL(gold, 0), NVL(silver, 0), NVL(bronze, 0)
      FROM (
         SELECT *
         FROM o_countries
            LEFT JOIN o_medal_table ON c_id = country_id
         ORDER BY NVL(gold, 0) DESC, NVL(silver, 0) DESC, NVL(bronze, 0) DESC, name
      )
   )
   WHERE position - (
      SELECT position
      FROM (
         SELECT ROWNUM AS position, c_id, name,
               NVL(gold, 0), NVL(silver, 0), NVL(bronze, 0)
         FROM (
            SELECT *
            FROM o_countries
               LEFT JOIN o_medal_table ON c_id = country_id
            ORDER BY NVL(gold, 0) DESC, NVL(silver, 0) DESC, NVL(bronze, 0) DESC, name
         )
      )
      WHERE name = 'Cuba'
   ) IN (-2, -1, 1, 2);
   ```

1. Return the **name** of each country whose first letter is the same as the 25th most populous country's one or the 25th greatest country's one.

   ```sql
   SELECT name
   FROM o_countries
   WHERE SUBSTR(name, 1, 1) IN (
      (
         SELECT SUBSTR(name, 1, 1)
         FROM (
            SELECT name, ROWNUM AS position
            FROM (
               SELECT name
               FROM o_countries
               ORDER BY population DESC NULLS LAST
            )
         )
         WHERE position = 25
      ),
      (
         SELECT SUBSTR(name, 1, 1)
         FROM (
            SELECT name, ROWNUM AS position
            FROM (
               SELECT name
               FROM o_countries
               ORDER BY area DESC NULLS LAST
            )
         )
         WHERE position = 25
      )
   );
   ```