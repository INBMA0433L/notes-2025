[↑ Back](./README.md)

# `C101` - Subselects, single (0D) result

## Schema diagram

![Schema diagram](./img/olympics-schema.png)

## Exercises

1. Return the **name** of each country that is located in the same continent as Hungary is located.

   ```sql
   SELECT name
   FROM o_countries
   WHERE continent = (
      SELECT continent
      FROM o_countries
      WHERE name = 'Hungary'
   );
   ```

1. Return each **capital** that starts with the same letter as Hungary's capital starts.

   ```sql
   SELECT capital
   FROM o_countries
   WHERE SUBSTR(capital, 1, 1) = (
      SELECT SUBSTR(capital, 1, 1)
      FROM o_countries
      WHERE name = 'Hungary'
   );
   ```

1. Return the **name** and the **gender** of each event that belongs to the Swimming discipline.

   ```sql
   SELECT name, gender
   FROM o_sport_events
   WHERE discipline_id = (
      SELECT d_id
      FROM o_sport_disciplines
      WHERE name = 'Swimming'
   );
   ```

1. Return the **name** and the **population** of each country which population is greater than the average.

   ```sql
   SELECT name, population
   FROM o_countries
   WHERE population > (
      SELECT AVG(population)
      FROM o_countries
   );
   ```

1. Return the **name** and the **gold medals** of each country which gained more gold medals than the average.

   ```sql
   SELECT name, gold
   FROM o_countries
   JOIN o_medal_table ON c_id = country_id
   WHERE gold >= (
      SELECT AVG(gold)
      FROM o_medal_table
   );
   ```

1. Return the **name** and the **total medals** of each country which gained more medals (in total) than the average.

   ```sql
   SELECT name, gold + silver + bronze
   FROM o_countries
      JOIN o_medal_table ON c_id = country_id
   WHERE gold >= (
      SELECT AVG(gold + silver + bronze)
      FROM o_medal_table
   );
   ```

1. Return the **name** and the **gold medals** of the country which gained the most of gold medals.

   ```sql
   SELECT name, gold
   FROM o_medal_table
      JOIN o_countries ON c_id = country_id
   WHERE gold = (
      SELECT MAX(gold)
      FROM o_medal_table
   );
   ```

1. Return the **name**, the **gold medals**, and **the silver** medals of each country which gained the most of gold or the most of silver medals.

   ```sql
   SELECT name, gold, silver
   FROM o_medal_table
      JOIN o_countries ON c_id = country_id
   WHERE gold = (
      SELECT MAX(gold)
      FROM o_medal_table
   ) OR silver = (
      SELECT MAX(silver)
      FROM o_medal_table
   );
   ```

1. Return the **name** and the **gold medals** of each country. Do not use any JOIN!

   ```sql
   SELECT name,
      (
         SELECT gold
         FROM o_medal_table
         WHERE c_id = country_id
      )
   FROM o_countries;
   ```

1. Return the **name** and the **gold medals** of each country that scored at least one gold medal. Do not use any JOIN!

   ```sql
   SELECT gold,
       (SELECT name
        FROM o_countries
        WHERE c_id = country_id)
   FROM o_medal_table
   WHERE gold >= 1;
   ```

1. Return the **name** of each continent that scored more gold medals than China.

   ```sql
   SELECT continent, SUM(gold)
   FROM o_countries
      JOIN o_medal_table
      ON c_id = country_id
   GROUP BY continent
   HAVING SUM(gold) > (
      SELECT gold
      FROM o_countries
         JOIN o_medal_table
         ON c_id = country_id
      WHERE name = 'China'
   );
   ```

   ```sql
   SELECT continent, SUM(gold)
   FROM o_countries
      JOIN o_medal_table
            ON c_id = country_id
   GROUP BY continent
   HAVING SUM(gold) > (
      SELECT gold
      FROM o_medal_table
      WHERE country_id = (
         SELECT c_id
         FROM o_countries
         WHERE name = 'China'
      )
   );
   ```

1. Return the **name**, the **continent** and the **population** of each country that is in the same continent as Hungary and its population is greater or equal to the population of Hungary. Order the countries by their population in descending order.

   ```sql
   SELECT name, continent, population
   FROM o_countries
   WHERE continent = (
      SELECT continent
      FROM o_countries
      WHERE name = 'Hungary'
   ) AND population >= (
      SELECT population
      FROM o_countries
      WHERE name = 'Hungary'
   )
   ORDER BY population DESC;
   ```
