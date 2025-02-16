[↑ Back](./README.md)

# `A201` - Selection

## Operators

### Reference

1. [Arithmetic Conditions](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/Arithmetic-Operators.html)

1. [Comparison Conditions](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/Comparison-Conditions.html)

### Exercises

1. Return the each **event** that is organized for women.
   
    ```sql
    SELECT *
    FROM o_sport_events
    WHERE gender = 'women';
    ```

1. Return each **medal table entry** that has at least one gold medal.

    ```sql
    SELECT *
    FROM o_medal_table
    WHERE gold > 0;
    ```

    ```sql
    SELECT *
    FROM o_medal_table
    WHERE gold <> 0;
    ```

    ```sql
    SELECT *
    FROM o_medal_table
    WHERE gold >= 1;
    ```

1. Return each **medal table entry** that has the same number of gold medals and silver medals.
    
    ```sql
    SELECT *
    FROM o_medal_table
    WHERE gold = silver;
    ```
    
    ```sql
    SELECT *
    FROM o_medal_table
    WHERE silver = bronze;
    ```


1. Return each **medal table entry** that has the same number of gold medals, silver medals, and bronze medals.

    ```sql
    SELECT *
    FROM o_medal_table
    WHERE gold = silver AND gold = bronze;
    ```

    **Comments:**

    1. You cannot compare more than 2 values without logical `AND`. Thus, this statement does not work:

        ```sql
        SELECT *
        FROM o_medal_table
        WHERE gold = silver = bronze;
        ```

    1. The logical `AND` is a shortcut operation.


1. Return each **medal table entry** that has not gained any gold medals nor any silver medals.

    ```sql
    SELECT *
    FROM o_medal_table
    WHERE gold = 0 AND silver = 0;
    ```
    
    ```sql
    SELECT *
    FROM o_medal_table
    WHERE gold + silver = 0;
    ```
    
    ```sql
    SELECT *
    FROM o_medal_table
    WHERE gold = 0 AND silver = gold;
    ```

1. Return each **medal table entry** that has not gained any gold medals nor silver medals but has bronze medals.

    ```sql
    SELECT *
    FROM o_medal_table
    WHERE gold = 0 AND silver = 0 AND bronze <> 0;
    ```

    **Comments:**

    1. In the schema, the last two exercises are equivalent. However, you must never consider the special features of a table state when designing a query.

1. Return each **medal table entry** that has gained zero gold medals or silver medals but has bronze medals.

    ```sql
    SELECT *
    FROM o_medal_table
    WHERE (gold = 0 OR silver = 0) AND bronze <> 0;
    ```

    **Comments:**

    1. You can change the precedence using the parenthesis operators.

1. Return each **medal table entry** that has more than 10 gold medals, silver medals, and bronze medals (in total).

    ```sql
    SELECT *
    FROM o_medal_table
    WHERE gold + silver + bronze > 10;
    ```

1. Return each medal table entry that has more than 10 gold medals, silver medals, and bronze medals (in total). Return the total number of medals as an additional column.

    ```sql
    SELECT o_medal_table.*, gold + silver + bronze
    FROM o_medal_table
    WHERE gold + silver + bronze > 10;
    ```

1. Return each medal table entry that has more than 10 gold medals, silver medals, and bronze medals (in total). Return the total number of medals as an additional column. Name the column as `total`.

    ```sql
    SELECT o_medal_table.*, gold + silver + bronze AS total
    FROM o_medal_table
    WHERE gold + silver + bronze > 10;
    ```

    **Comments:**

    1. You cannot refer to the aliases in the selection due to the execution order. Thus, the next statement does not work:

        ```sql
        SELECT o_medal_table.*, gold + silver + bronze AS total
        FROM o_medal_table
        WHERE total > 10;
        ```

## `BETWEEN` condition

### Reference

1. https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/BETWEEN-Condition.html

### Exercises

1. Return each **medal table entry** which number of gold medals is between `5` and `9`.

    ```sql
    SELECT *
    FROM o_medal_table
    WHERE gold >= 5 AND gold <= 9;
    ```

    ```sql
    SELECT *
    FROM o_medal_table
    WHERE gold BETWEEN 5 AND 9;
    ```

    **Comments:**

    1. The `BETWEEN x AND y` expression specifies an interval which lower bound is `x` and upper bound is `y`.
    1. The order of `x` and `y` matters.
    1. The intervals are always inclusive.

1. Return each **medal table entry** which gold medals is between the silver medals and bronze medals.

    ```sql
    SELECT * 
    FROM O_MEDAL_TABLE
    WHERE gold BETWEEN bronze AND silver;
    ```

    **Comments:**

    1. The order still matters. The next statement is not a possible solution:

        ```sql
        SELECT * 
        FROM O_MEDAL_TABLE
        WHERE gold BETWEEN silver AND bronze;
        ```

## `NULL` conditions

### Reference

1. https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/Null-Conditions.html

### Explanation

1. Expressions *unknown* and *missing* refer to the `NULL` values.
1. The equality operators does not work with `NULL` operands.
1. You can use the `IS` operator and the negated `IS NOT` construct for comparisons including `NULL` values.

### Exercises

1. Return each **event** which name is unknown.

    ```sql
    SELECT *
    FROM o_sport_events
    WHERE name IS NULL;
    ```

1. Return each **event** which name is known.

    ```sql
    SELECT *
    FROM o_sport_events
    WHERE name IS NOT NULL;
    ```

1. Return each **gender** (only once) for which an event is scheduled with an unknown name.

    ```sql
    SELECT DISTINCT gender
    FROM o_sport_events
    WHERE name IS NULL;
    ```
