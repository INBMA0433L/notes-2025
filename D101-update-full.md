[↑ Back](./README.md)

# `D101` - `UPDATE` statement

## Schema diagram

![Schema diagram](./img/olympics-schema.png)

## Exercises

> [!IMPORTANT]
>
> You are going to modify the state of your schema that can cause issues in other exercises. Thus, we must guarantee that each query is being executed in the original state.
>
> Execute your query that updates the database, check the new state, and have a `ROLLBACK` statement. Do not commit your changes.

### Basic exercises

1. Update those medal entries that don't have a gold medal. Set the **gold medals** to `1` for each country that doesn't have any gold medals.

   ```sql
   UPDATE o_medal_table
   SET gold = 1
   WHERE gold = 0;
   ```

1. Set the name of each European country to uppercase.

   ```sql
   UPDATE o_countries
   SET name = UPPER(name)
   WHERE continent = 'Europe';
   ```

1. Update those countries that do not have a continent. Set the **continent** column to `unknown`.

   ```sql
   UPDATE o_countries
   SET continent = 'unknown'
   WHERE continent IS NULL;
   ```

1. Swap the `population` and the `area` of each country to fix the schema.

   ```sql
   UPDATE o_countries
   SET population = area,
      area = population;
   ```

   *Unsafe query: 'Update' statement without 'where' updates all table rows at once*

### Subquery-based exercises

1. Update the youngest athlete. Set his/her name to `Tralalelo Tralala`.

   ```sql
   UPDATE o_athletes
   SET name = 'Tralalelo Tralala'
   WHERE birthdate = (SELECT MAX(birthdate)
                     FROM o_athletes);
   ```

1. Update those countries whose population is missing. Set their **population** to the average of populations.

   ```sql
   UPDATE o_countries
   SET population = (
      SELECT ROUND(AVG(population))
               FROM o_countries)
   WHERE population IS NULL;
   ```

1. Update those countries whose capital is missing. Set their **capital** to the longest among them.

   ```sql
   UPDATE o_countries
   SET capital = (SELECT capital
                  FROM o_countries
                  WHERE LENGTH(capital) = (SELECT MAX(LENGTH(capital))
                                          FROM o_countries))
   WHERE capital IS NULL;
   ```

1. Update those medal table entries that have `0` gold medals. Set their **gold**, **silver**, and **bronze** values to the values of `China`.

   ```sql
   UPDATE o_medal_table
   SET (gold, silver, bronze) = (
      SELECT gold, silver, bronze
      FROM o_countries
         JOIN o_medal_table
         ON c_id = country_id
      WHERE name = 'China'
   )
   WHERE gold = 0;
   ```

1. Update those countries whose continent is missing. Set their **continent** to the one with the least corresponding countries.

   ```sql
   UPDATE o_countries
   SET continent = (SELECT continent
                  FROM (SELECT continent, COUNT(*)
                        FROM o_countries
                        WHERE continent IS NOT NULL
                        GROUP BY continent
                        ORDER BY COUNT(*))
                  WHERE ROWNUM = 1)
   WHERE continent IS NULL;
   ```

1. Update those countries that have participated in disciplines whose names start with the letter `W`. Add the prefix `W` to the country names, such as `W Hungary`. Use a single space as the delimiter.

   ```sql
   UPDATE o_countries
   SET name = 'W ' || name
   WHERE c_id IN (SELECT DISTINCT country_id
                  FROM o_countries
                     JOIN o_athletes ON o_countries.c_id = o_athletes.country_id
                     JOIN o_results ON o_athletes.a_id = o_results.athlete_id
                     JOIN o_sport_events ON o_results.event_id = o_sport_events.e_id
                     JOIN o_sport_disciplines ON o_sport_events.discipline_id = o_sport_disciplines.d_id
                  WHERE o_sport_disciplines.name LIKE 'W%');
   ```

1. Update those countries that have participated in one of the disciplines that Hungary is. Add the suffix `(rival)` to the country names, such as `Germany (rival)`. Use a single space as the delimiter.

   ```sql
   UPDATE o_countries
   SET name = name || ' (rival)'
   WHERE c_id IN (SELECT DISTINCT country_id
                        FROM o_countries
                           JOIN o_athletes ON o_countries.c_id = o_athletes.country_id
                           JOIN o_results ON o_athletes.a_id = o_results.athlete_id
                           JOIN o_sport_events ON o_results.event_id = o_sport_events.e_id
                        WHERE o_countries.name != 'Hungary'
                        AND discipline_id IN (SELECT DISTINCT discipline_id
                                                FROM o_countries
                                                   JOIN o_athletes ON o_countries.c_id = o_athletes.country_id
                                                   JOIN o_results ON o_athletes.a_id = o_results.athlete_id
                                                   JOIN o_sport_events ON o_results.event_id = o_sport_events.e_id
                                                WHERE o_countries.name = 'Hungary'));
   ```
