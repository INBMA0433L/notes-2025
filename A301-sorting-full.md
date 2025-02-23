
[↑ Back](./README.md)

# Sorting

## Reference

1. [`SELECT` statement](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/SELECT.html)

## Explanation

TODO

## Exercises

1. Return the **ID**, the **gold medals**, the **silver medals**, and the **bronze medals** of each medal table entry. Sort the rows by the **gold medals** in ascending order.

    ```sql
    SELECT *
    FROM o_medal_table
    ORDER BY 2;
    ```

    ```sql
    SELECT *
    FROM o_medal_table
    ORDER BY gold;
    ```

    ```sql
    SELECT *
    FROM o_medal_table
    ORDER BY gold ASC;
    ```

1. Return the **ID**, the **gold medals**, the **silver medals**, and the **bronze medals** of each medal table entry. Sort the rows by the **gold medals** in descending order.

    ```sql
    SELECT *
    FROM o_medal_table
    ORDER BY gold DESC;
    ```

    ```sql
    SELECT *
    FROM o_medal_table
    ORDER BY 2 DESC;
    ```

1. Return the **ID**, the **gold medals**, the **silver medals**, and the **bronze medals** of each medal table entry. Sort the rows by the **gold medals** in descending order, then by the **silver medals** in ascending order.

    ```sql
    SELECT *
    FROM o_medal_table
    ORDER BY gold DESC, silver;
    ```

1. Return the **ID**, the **gold medals**, the **silver medals**, and the **bronze medals** of each medal table entry. Sort the rows by the **gold medals** in descending order, then by the **silver medals** in descending order.

    ```sql
    SELECT *
    FROM o_medal_table
    ORDER BY gold DESC, silver DESC;
    ```

1. Return the **ID**, the **gold medals**, the **silver medals**, the **bronze medals**, and **the total medals** of each medal table entry. Sort the rows by the **total medals** in descending order, then by the **gold medals** in ascending order.

    ```sql
    SELECT *
    FROM o_medal_table
    ORDER BY gold + silver + bronze DESC, gold;
    ```

1. Return each **sport discipline**. Sort the rows by the **names**.

    ```sql
    SELECT *
    FROM o_sport_disciplines
    ORDER BY name;
    ```

1. Return each **sport discipline**. Sort the rows by the **names** in descending order.

    ```sql
    SELECT *
    FROM o_sport_disciplines
    ORDER BY name DESC;
    ```

1. Return each **athelete**. Sort the rows by the **birthdates** in descending order, then by the **names** in ascending order.

    ```sql
    SELECT *
    FROM o_athletes
    ORDER BY birthdate DESC, name;
    ```