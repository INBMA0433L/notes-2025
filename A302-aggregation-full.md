[↑ Back](./README.md)

# `A302` - Aggregation

## The `COUNT()` function

### Reference

1. [`COUNT`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/COUNT.html)

### Exercises

1. Return the **number of rows** in the `o_sport_events` table.

    ```sql
    SELECT COUNT(*)
    FROM o_sport_events;
    ```

1. Return the **number of rows** in the `o_countries` table.

    ```sql
    SELECT COUNT(*)
    FROM o_countries;
    ```

1. Return the **number of gender values** in the `o_sport_events` table.

    ```sql
    SELECT COUNT(gender)
    FROM o_sport_events;
    ```

1. Return the **number of continent values** in the `o_countries` table.

    ```sql
    SELECT COUNT(continent)
    FROM o_countries;
    ```

1. Return the **number of distinct genders** in the `o_sport_events` table.
    
    ```sql
    SELECT COUNT(DISTINCT gender)
    FROM o_sport_events;
    ```

1. Return the **number of distinct continents** in the `o_countries` table.

    ```sql
    SELECT COUNT(DISTINCT continent)
    FROM o_countries;
    ```

1. Return the **number of distinct genders** and the **number of distinct names** in the `o_sport_events` table.
    
    ```sql
    SELECT COUNT(DISTINCT gender), COUNT(DISTINCT name)
    FROM o_sport_events;
    ```

1. Return the **number of distinct genders** and the **number of distinct names** in the `o_sport_events` table. Use the aliases `"genders"` and `"names"` for the columns.
    
    ```sql
    SELECT COUNT(DISTINCT gender) AS genders, COUNT(DISTINCT name) as names
    FROM o_sport_events;
    ```


## The `MIN()`, `MAX()`, and `AVG()` functions

### Reference

1. [`MIN` function](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/MIN.html)
1. [`MAX` function](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/MAX.html)
1. [`AVG` function](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/AVG.html)

### Exercises

1. Return the **minimum number of gold medals**, the **maximum number of gold medals**, and the **average number of gold medals** in the `o_medal_table` table.
    
    ```sql
    SELECT MIN(gold), MAX(gold), AVG(gold)
    FROM o_medal_table;
    ```

1. Return the **earliest birthdate** and the **latest birthdate** on which an athlete was born.
    
    ```sql
    SELECT MIN(birthdate), MAX(birthdate)
    FROM o_athletes;
    ```

1. Return the **first name** and the **last name** of athletes in alphabetic order.
    
    ```sql
    SELECT MIN(name), MAX(name)
    FROM o_athletes;
    ```

1. Return the **minimum number of medals**, the **maximum number of medals**, and the **average number of medals** in the `o_medal_table` table.

    ```sql
    SELECT MIN(gold + silver + bronze), MAX(gold + silver + bronze), AVG(gold + silver + bronze)
    FROM o_medal_table;
    ```

## The `GROUP BY` clause

### Exercises

1. Return **each gender** and the **number of corresponding events**.

    ```sql
    SELECT gender, COUNT(*)
    FROM o_sport_events
    GROUP BY gender;
    ```

1. Return **each name** and the **number of corresponding events**.

    ```sql
    SELECT name, COUNT(*)
    FROM o_sport_events
    GROUP BY name;
    ```

1. Return **each continent** and the **number of corresponding countries**.

    ```sql
    SELECT continent, COUNT(*)
    FROM o_countries
    GROUP BY continent;
    ```

1. Return **each birthplace** and the **number of corresponding athletes**.

    ```sql
    SELECT birthplace, COUNT(*)
    FROM o_athletes
    GROUP BY birthplace;
    ```

1. Return **each place** and the **number of corresponding notes**.

    ```sql
    SELECT place, COUNT(note)
    FROM o_results
    GROUP BY place;
    ```

1. Return **each place** and the **number of unique corresponding notes**.

    ```sql
    SELECT place, COUNT(DISTINCT note)
    FROM o_results
    GROUP BY place;
    ```

1. Return **each continent**, the **least corresponding area**, the **greatest corresponding area**, and the **average of corresponding areas**. 

    ```sql
    SELECT continent, MIN(area), MAX(area), AVG(area)
    FROM o_countries
    GROUP BY continent;
    ```

1. Return **each total medal value** and the **number of corresponding countries**.

    ```sql
    SELECT gold + silver + bronze, COUNT(*)
    FROM o_medal_table
    GROUP BY gold + silver + bronze;
    ```

1. Return **each discipline ID** and the **number of corresponding events**.

    ```sql
    SELECT discipline_id, COUNT(*)
    FROM o_sport_events
    GROUP BY discipline_id;
    ```

1. Return **each discipline ID** and the **number of corresponding event names**.

    ```sql
    SELECT discipline_id, COUNT(name)
    FROM o_sport_events
    GROUP BY discipline_id;
    ```

## The `HAVING` clause

### Exercises

1. Return **each continent** and the **number of corresponding countries**. Omit the `NULL` value from the output.

    ```sql
    SELECT continent, COUNT(*)
    FROM o_countries
    WHERE continent IS NOT NULL
    GROUP BY continent;
    ```

    ```sql
    SELECT continent, COUNT(*)
    FROM o_countries
    GROUP BY continent
    HAVING continent IS NOT NULL;
    ```

1. Return **each continent** and the **number of corresponding countries**. Return a continent if the number of corresponding countries is greater than `30`.

    ```sql
    SELECT continent, COUNT(*)
    FROM o_countries
    GROUP BY continent
    HAVING COUNT(*) > 30;
    ```

    > *This doesn't work:*
    > ```sql
    > SELECT continent, COUNT(*)
    > FROM o_countries
    > WHERE COUNT(*) > 30
    > GROUP BY continent;
    > ```

1. Return **each continent** and the **average of corresponding populations**, and the **number of corresponding countries**. Return a continent if the average of corresponding populations is less than `500000`.
   
    ```sql
    SELECT continent, AVG(population), COUNT(*)
    FROM o_countries
    GROUP BY continent
    HAVING AVG(population) < 500000;
    ```

1. Return **each discipline ID** and the **number of corresponding event names**. Return a discipline ID if it has any event name.

    ```sql
    SELECT discipline_id, COUNT(name)
    FROM o_sport_events
    GROUP BY discipline_id;
    ```

## Multiple column names

1. Return **each event name and gender combination** with the **number of the corresponding events**.
   
    ```sql
    SELECT name, gender, COUNT(*)
    FROM o_sport_events
    GROUP BY name, gender;
    ```

1. Return **each gold medal and silver medal combination** with the **number of the corresponding entries**.
   
    ```sql
    SELECT gold, silver, COUNT(*)
    FROM o_medal_table
    GROUP BY gold, silver;
    ```
