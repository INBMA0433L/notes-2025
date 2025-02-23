[↑ Back](./README.md)

# `A302` - Aggregation

## The `COUNT()` function

### Reference

1. [`COUNT`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/COUNT.html)

### Exercises

1. Return the **number of rows** in the `o_sport_events` table.

1. Return the **number of rows** in the `o_countries` table.

1. Return the **number of gender values** in the `o_sport_events` table.

1. Return the **number of continent values** in the `o_countries` table.

1. Return the **number of distinct genders** in the `o_sport_events` table.
    
1. Return the **number of distinct continents** in the `o_countries` table.

1. Return the **number of distinct genders** and the **number of distinct names** in the `o_sport_events` table.
    
1. Return the **number of distinct genders** and the **number of distinct names** in the `o_sport_events` table. Use the aliases `"genders"` and `"names"` for the columns.

## The `MIN()`, `MAX()`, and `AVG()` functions

### Reference

1. [`MIN` function](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/MIN.html)
1. [`MAX` function](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/MAX.html)
1. [`AVG` function](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/AVG.html)

### Exercises

1. Return the **minimum number of gold medals**, the **maximum number of gold medals**, and the **average number of gold medals** in the `o_medal_table` table.
    
1. Return the **earliest birthdate** and the **latest birthdate** on which an athlete was born.
    
1. Return the **first name** and the **last name** of athletes in alphabetic order.
    
1. Return the **minimum number of medals**, the **maximum number of medals**, and the **average number of medals** in the `o_medal_table` table.

## The `GROUP BY` clause

### Exercises

1. Return **each gender** and the **number of corresponding events**.

1. Return **each name** and the **number of corresponding events**.

1. Return **each continent** and the **number of corresponding countries**.

1. Return **each birthplace** and the **number of corresponding athletes**.

1. Return **each place** and the **number of corresponding notes**.

1. Return **each place** and the **number of unique corresponding notes**.

1. Return **each continent**, the **least corresponding area**, the **greatest corresponding area**, and the **average of corresponding areas**. 

1. Return **each total medal value** and the **number of corresponding countries**.

1. Return **each discipline ID** and the **number of corresponding events**.

1. Return **each discipline ID** and the **number of corresponding event names**.

## The `HAVING` clause

### Exercises

1. Return **each continent** and the **number of corresponding countries**. Omit the `NULL` value from the output.

1. Return **each continent** and the **number of corresponding countries**. Return a continent if the number of corresponding countries is greater than `30`.

1. Return **each continent** and the **average of corresponding populations**, and the **number of corresponding countries**. Return a continent if the average of corresponding populations is less than `500000`.
   
1. Return **each discipline ID** and the **number of corresponding event names**. Return a discipline ID if it has any event name.

## Multiple column names

1. Return **each event name and gender combination** with the **number of the corresponding events**.
   
1. Return **each gold medal and silver medal combination** with the **number of the corresponding entries**.
   