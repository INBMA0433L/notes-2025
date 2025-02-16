[↑ Back](./README.md)

# `A102` - Projection

## Returning all the records and columns

1. Return each **country**.

    ```sql
    SELECT o_countries.*
    FROM o_countries;
    ```

    ```sql
    SELECT *
    FROM o_countries;
    ```

1. Return each **sport event**.

    ```sql
    SELECT *
    FROM o_sport_events;
    ```


1. Return each **sport discipline**.

    ```sql
    SELECT *
    FROM o_sport_disciplines;
    ```

## Returning a single column

1. Return the **name** of each country.

    ```sql
    SELECT name
    FROM o_countries;
    ```

1. Return the **name** of each event.

    ```sql
    SELECT name
    FROM o_sport_disciplines;
    ```

1. Return the **gender** of each event.

    ```sql
    SELECT gender
    FROM o_sport_disciplines;
    ```

## The `DISTINCT`/`UNIQUE` keywords

1. Return each **gender** (only once) that had any event.

    ```sql
    SELECT DISTINCT gender
    FROM o_sport_events;
    ```

    ```sql
    SELECT UNIQUE gender
    FROM o_sport_events;
    ```

1. Return each **continent** (only once) that has any country.

    ```sql
    SELECT DISTINCT continent
    FROM o_countries;
    ```

    ```sql
    SELECT UNIQUE continent
    FROM o_countries;
    ```

1. Return each **birthplace** (only once) that has any athlete.

    ```sql
    SELECT DISTINCT birthplace
    FROM o_athletes;
    ```
    
    ```sql
    SELECT UNIQUE birthplace
    FROM o_athletes;
    ```
    
## Returning multiple columns

1. Return the **name** and the **capital** of each country.

    ```sql
    SELECT name, capital
    FROM o_countries;
    ```

1. Return the **capital** and the **name** of each country.

    ```sql
    SELECT capital, name
    FROM o_countries;
    ```

1. Return the **name** of each country twice (in two columns).

    ```sql
    SELECT capital, capital
    FROM o_countries;
    ```

1. Return the **name** and the **gender** of each event.

    ```sql
    SELECT name, gender
    FROM o_sport_events;
    ```

1. Return the **ID** and the **gold medals** of each country.

    ```sql
    SELECT country_id, gold
    FROM o_medal_table;
    ```

## Returning custom expressions

1. Return the **ID** and the **total medals** of each country.

    ```sql
    SELECT country_id, gold + silver + bronze
    FROM o_medal_table;
    ```

1. Return the **ID**, the **gold medals**, the **silver medals**, the **bronze medals**, and the **total modals** of each country.

    ```sql
    SELECT country_id, gold, silver, bronze, gold + silver + bronze
    FROM o_medal_table;
    ```

    ```sql
    SELECT o_medal_table.*, gold + silver + bronze
    FROM o_medal_table;
    ```

## Using aliases

1. Return the **name** and the **continent** of each country.

    ```sql
    SELECT name, continent
    FROM o_countries;
    ```

1. Return the **name** and the **continent** of each country. Name the first column as `"country"` (case insensitive).

    ```sql
    SELECT name AS country, continent
    FROM o_countries;
    ```

    ```sql
    SELECT name country, continent
    FROM o_countries;
    ```

1. Return the **name** and the **continent** of each country. Name the first column as `"Country"` (case sensitive).

    ```sql
    SELECT name AS "Country", continent
    FROM o_countries;
    ```

    ```sql
    SELECT name "Country", continent
    FROM o_countries;
    ```

1. Return the **name** and the **continent** of each country. Name the columns as `The country` and `The continent`.

    ```sql
    SELECT name AS "The country", continent AS "The continent"
    FROM o_countries;
    ```

    ```sql
    SELECT name "The country", continent "The continent"
    FROM o_countries;
    ```

1. Return the **name**, the **area**, the **population**, and the **population density** (**population** / **area**) of each country. Name the last column as `Density`.

    ```sql
    SELECT name, area, population, population / area AS "Density"
    FROM o_countries;
    ```
