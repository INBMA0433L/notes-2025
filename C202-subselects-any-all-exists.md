[↑ Back](./README.md)

# `C202` - Conditions `ANY`, `ALL`, and `EXISTS`

## Schema diagram

![Schema diagram](./img/olympics-schema.png)

## Reference

1. [`ANY` Condition](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/ANY-Condition.html)
1. [`ALL` Condition](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/ALL-Condition.html)
1. [`EXISTS` Condition](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/EXISTS-Condition.html)

## Exercises

1. Return the **ID** and **name** of each country that has any medals (thus, it appears in the `o_medal_table` table).

1. Return **each country** that is the most populous on its continent.

1. Return **each country** that has greater population than one of the European countries has.

1. Return **each country** that has greater population than all of the European countries has.
    
1. Return **each country** name which first letter stands in the alphabetic order after all the European countries' first letters.

1. Return the **name** and the **gold medals** of each country that has more gold medals than at least one European country has.

1. Return the **name** and the **gold medals** of each country that has more gold medals than all the European countries.
