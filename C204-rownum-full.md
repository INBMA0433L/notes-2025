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

1. Return **the country** having the fifth greatest area.

1. Return **each country** whose population is less than the population of the country having the fifth greatest area.

1. Return the **name** and the **gold medals** of each country that scored one of the five greatest gold medals.

1. Return **each country** that scored the least number of medals.

1. Return **each country** that scored one of the least `5` medals.

1. Return the **name** and the **area** of each African country which area is greater than the 5th greatest European area and less than the 3rd greatest Asian area.

1. Return the **ID**, the **name**, the **place**, and the **medals** of each country. Return the value of `0` instead of all the `NULL` values. Order the table to be a real medal table. If two countries scored the same amount of medals, order them by their names.

1. Return the **place** of Cuba based on the previous query.

1. Return the **ID**, the **name**, the **place**, and the **medals** of each country whose position precedes or follows Cuba by at most two places.

1. Return the **name** of each country whose first letter is the same as the 25th most populous country's one or the 25th greatest country's one.
