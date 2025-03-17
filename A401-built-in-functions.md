[↑ Back](./README.md)

# `A401` - Built-in functions

## Dealing with `NULL` values

### The `NVL()` function

#### Reference

1. [SQL Language Reference - `NVL`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/NVL.html)

#### Exercises

1. Return the **name**, the **population**, and the **continent** of the country `Cook Islands`.

   ```sql
   SELECT name, population, continent
   FROM o_countries
   WHERE name = 'Cook Islands';
   ```

1. Return the **name**, the **population**, and the **continent** of country `Cook Islands`. Replace the missing continent name with the `"unknown"` string.

   ```sql
   SELECT name, population, NVL(continent, 'unknown')
   FROM o_countries
   WHERE name = 'Cook Islands';
   ```

1. Return the **name**, the **population**, and the **continent** of each country. Replace the missing continent names with the `"unknown"` string.

   ```sql
   SELECT name, population, NVL(continent, 'unknown')
   FROM o_countries;
   ```

1. Return the **name**, the **population**, and the **continent** of each country. Replace the missing continent names with the `"unknown"` and the missing population values with the `0` value.

   ```sql
   SELECT name, NVL(population, 0), NVL(continent, 'unknown')
   FROM o_countries;
   ```

### The `NVL2()` function

#### Reference

1. [SQL Language Reference - `NVL2`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/NVL2.html)

#### Exercises

1. Return the **name** of each country with an additional column that contains **whether the country's continent is known**. Use the values `"yes"` and `"no"` in the second column.

## String functions

### Functions `LOWER()`, `UPPER()`, and `INITCAP()`

#### Reference

1. [SQL Language Reference - `UPPER`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/UPPER.html)
1. [SQL Language Reference - `LOWER`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/LOWER.html)
1. [SQL Language Reference - `INITCAP`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/INITCAP.html)

#### Examples

1. example

   ```sql
   SELECT name, UPPER(name)
   FROM o_countries;
   ```

1. example

   ```sql
   SELECT name, LOWER(name)
   FROM o_countries;
   ```

1. example

   ```sql
   SELECT name, INITCAP(name)
   FROM o_sport_events;
   ```

### Function `CONCAT()`

#### Reference

1. [SQL Language Reference - `CONCAT`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/CONCAT.html)

#### Examples

1. example

   ```sql
   SELECT name || gender
   FROM o_sport_events;
   ```

1. example
   
   ```sql
   SELECT CONCAT(name, gender)
   FROM o_sport_events;
   ```

1. example
  
   ```sql
   SELECT name || ' ' || gender
   FROM o_sport_events;
   ```

1. example
   
   ```sql
   SELECT CONCAT(name, CONCAT(' ', gender))
   FROM o_sport_events;
   ```

1. example
   
   ```sql
   SELECT name || ' (' || gender || ')'
   FROM o_sport_events;
   ```

1. example
   
   ```sql
   SELECT CONCAT(name, CONCAT(' (', CONCAT(gender, ')')))
   FROM o_sport_events;
   ```

### Function `SUBSTR()`

#### Reference

1. [SQL Language Reference - `SUBSTR`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/SUBSTR.html)

#### Examples

1. example
   
   ```sql
   SELECT name, SUBSTR(name, 3)
   FROM o_sport_events;
   ```

1. example
   
   ```sql
   SELECT name, SUBSTR(name, 1)
   FROM o_sport_events;
   ```

1. example
   
   ```sql
   SELECT name, SUBSTR(name, 0)
   FROM o_sport_events;
   ```

1. example
   
   ```sql
   SELECT name, SUBSTR(name, -3)
   FROM o_sport_events;
   ```

1. example
   
   ```sql
   SELECT name, SUBSTR(name, 1, 3)
   FROM o_sport_events;
   ```

1. example
   
   ```sql
   SELECT name, SUBSTR(name, -5, 2)
   FROM o_sport_events;
   ```

1. example
   
   ```sql
   SELECT name, SUBSTR(name, 2, 1)
   FROM o_sport_events;
   ```

### Function `LENGTH()`

#### Reference

1. [SQL Language Reference - `LENGTH`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/LENGTH.html)

#### Examples

1. example

   ```sql
   SELECT name, LENGTH(name)
   FROM o_sport_events;
   ```

### Functions `LPAD()` and `RPAD()`

#### Reference

1. [SQL Language Reference - `LPAD`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/LPAD.html)
1. [SQL Language Reference - `RPAD`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/RPAD.html)

#### Examples

1. example
   
   ```sql
   SELECT name, LPAD(name, 20)
   FROM o_sport_events;
   ```

1. example
   
   ```sql
   SELECT name, LPAD(name, 20, '*')
   FROM o_sport_events;
   ```

1. example
   
   ```sql
   SELECT name, RPAD(name, 20)
   FROM o_sport_events;
   ```

1. example
   
   ```sql
   SELECT name, RPAD(name, 20, '*')
   FROM o_sport_events;
   ```

### Functions `LTRIM()` and `RTRIM()`

#### Reference

1. [SQL Language Reference - `LTRIM`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/LTRIM.html)
1. [SQL Language Reference - `RTRIM`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/RTRIM.html)
1. [SQL Language Reference - Selecting from the `DUAL` table](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/Selecting-from-the-DUAL-Table.html)

#### Examples

1. example
   
   ```sql
   SELECT LTRIM('coconut', 'c')
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT LTRIM('coconut', 'co')
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT LTRIM('coconut', 't')
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT LTRIM('       coconut     ', ' ')
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT RTRIM('       coconut     ', ' ')
   FROM dual;
   ```

### Function `REPLACE()`

#### Reference

1. [SQL Language Reference - `REPLACE`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/REPLACE.html)

#### Examples

1. example
   
   ```sql
   SELECT REPLACE('coconut', 'o')
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT REPLACE('coconut', 'o')
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT REPLACE('coconut', 'co')
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT REPLACE('coconut', 'co', 'ko')
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT REPLACE('coconut', 'co', 'a')
   FROM dual;
   ```

### Function `INSTR()`

#### Reference

1. [SQL Language Reference - `INSTR`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/INSTR.html)

#### Examples

   ```sql
   SELECT INSTR(name, ' '), name
   FROM O_COUNTRIES;
   ```

1. example

   ```sql
   SELECT INSTR(name, 'S'), name
   FROM O_COUNTRIES;
   ```

1. example

   ```sql
   SELECT INSTR(name, ' S'), name
   FROM O_COUNTRIES;
   ```

## Math functions

### Function `ABS()`

#### Reference

1. [SQL Language Reference - `ABS`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/ABS.html)

#### Examples

1. example

   ```sql
   SELECT ABS(15)
   FROM dual;
   ```

1. example

   ```sql
   SELECT ABS(-15)
   FROM dual;
   ```

### Function `POWER()`

#### Reference

1. [SQL Language Reference - `POWER`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/POWER.html)

#### Examples

1. example
   
   ```sql
   SELECT POWER(2, 4)
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT POWER(-2, 4)
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT POWER(2, -4)
   FROM dual;
   ```

### Function `SQRT()`

#### Reference

1. [SQL Language Reference - `SQRT`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/SQRT.html)

#### Examples

1. example
   
   ```sql
   SELECT SQRT(2)
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT SQRT(4)
   FROM dual;
   ```

### Function `MOD()`

#### Reference

1. [SQL Language Reference - `MOD`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/MOD.html)

#### Examples

1. example
   
   ```sql
   SELECT MOD(5, 2)
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT MOD(20, 7)
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT MOD(-1, 3)
   FROM dual;
   ```

### Function `CEIL()`

#### Reference

1. [SQL Language Reference - `CEIL`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/CEIL.html)

#### Examples

1. example
   
   ```sql
   SELECT CEIL(3.14)
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT CEIL(5)
   FROM dual;
   ```

### Function `FLOOR()`

#### Reference

1. [SQL Language Reference - `FLOOR`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/FLOOR.html)

#### Examples

1. example
   
   ```sql
   SELECT FLOOR(3.14)
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT FLOOR(5)
   FROM dual;
   ```
   
### Function `ROUND()`

#### Reference

1. [SQL Language Reference - `ROUND (number)`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/ROUND-number.html)

#### Examples

1. example
   
   ```sql
   SELECT ROUND(3.14159)
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT ROUND(3.14159, 1)
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT ROUND(3.14159, 2)
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT ROUND(1414.242, 0)
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT ROUND(1414.242, 0)
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT ROUND(1414.242, -1)
   FROM dual;
   ```

1. example
   
   ```sql
   SELECT ROUND(1414.242, -2)
   FROM dual;
   ```
   
## Date functions

### Function `SYSDATE`

#### Reference

1. [SQL Language Reference - `SYSDATE`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/SYSDATE.html)

#### Examples

1. example
   
   ```sql
   SELECT SYSDATE
   FROM dual;
   ```

### Function `MONTHS_BETWEEN()`

#### Reference

1. [SQL Language Reference - `MONTHS_BETWEEN`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/MONTHS_BETWEEN.html)

#### Examples

1. example

   ```sql
   SELECT name, birthdate, MONTHS_BETWEEN(SYSDATE, birthdate)
   FROM o_athletes;
   ```

1. example

   ```sql
   SELECT name, birthdate, MONTHS_BETWEEN(birthdate, SYSDATE)
   FROM o_athletes;
   ```

1. example

   ```sql
   SELECT name, birthdate, ROUND(MONTHS_BETWEEN(SYSDATE, birthdate))
   FROM o_athletes;
   ```

### Function `ADD_MONTHS()`

#### Reference

1. [SQL Language Reference - `ADD_MONTHS`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/ADD_MONTHS.html)

#### Examples

1. example
   ```sql
   SELECT name, birthdate, ADD_MONTHS(birthdate, 1)
   FROM o_athletes;
   ```

1. example
   ```sql
   SELECT name, birthdate, ADD_MONTHS(birthdate, 5)
   FROM o_athletes;
   ```

1. example
   ```sql
   SELECT name, birthdate, ADD_MONTHS(birthdate, 1)
   FROM o_athletes;
   ```

### Function `NEXT_DAY()`

#### Reference

1. [SQL Language Reference - `NEXT_DAY`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/NEXT_DAY.html)

#### Examples

1. example

   ```sql
   SELECT name, birthdate, NEXT_DAY(birthdate, 1)
   FROM o_athletes;
   ```

1. example
   ```sql
   SELECT name, birthdate, NEXT_DAY(birthdate, 3)
   FROM o_athletes;
   ```

1. example
   ```sql
   SELECT name, birthdate, NEXT_DAY(birthdate, 7)
   FROM o_athletes;
   ```

1. example
   ```sql
   SELECT name, birthdate, NEXT_DAY(birthdate, 10)
   FROM o_athletes;
   ```

### Function `LAST_DAY()`

#### Reference

1. [SQL Language Reference - `LAST_DAY`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/LAST_DAY.html)

#### Examples

1. example

   ```sql
   SELECT name, birthdate, LAST_DAY(birthdate)
   FROM o_athletes;
   ```
### Function `EXTRACT()`

#### Reference

1. [SQL Language Reference - `EXTRACT (datetime)`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/EXTRACT-datetime.html)

#### Examples

1. example

   ```sql
   SELECT SYSDATE,
   EXTRACT(YEAR FROM SYSDATE),
   EXTRACT(MONTH FROM SYSDATE),
   EXTRACT(DAY FROM SYSDATE)
   FROM DUAL;
   ```

### Function `TO_DATE()`

#### Reference

1. [SQL Language Reference - `TO_DATE`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/TO_DATE.html)

#### Examples

1. example

   ```sql
   SELECT TO_DATE('26-06-2025', 'DD-MM-YYYY') AS "Days until the exam period :)"
   FROM dual;
   ```

### Function `TRUNC(date)`

#### Reference

1. [SQL Language Reference - `TRUNC(date)`](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/TRUNC-date.html)

#### Examples

1. example

   ```sql
   SELECT TRUNC(TO_DATE('26-06-2025', 'DD-MM-YY'), 'YEAR'),
         TRUNC(TO_DATE('26-06-2025', 'DD-MM-YY'), 'MONTH'),
         TRUNC(TO_DATE('26-06-2025', 'DD-MM-YY'), 'DAY'),
   FROM dual;
   ```
