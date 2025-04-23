[↑ Back](./README.md)

# `D101` - `UPDATE` statement

## Schema diagram

![Schema diagram](./img/olympics-schema.png)

## Exercises

> [!IMPORTANT]
>
> You are going to modify the state of your schema, which can cause issues in other exercises. Thus, we must guarantee that each query is being executed in the original state.
>
> Execute your query that updates the database, checks the new state, and has a `ROLLBACK` statement. Do not commit your changes.

### Basic exercises

1. Update those medal entries that don't have a gold medal. Set the **gold medals** to `1` for each country that doesn't have any gold medals.

1. Set the name of each European country to uppercase.

1. Update those countries that do not have a continent. Set the **continent** column to `unknown`.

1. Swap the `population` and the `area` of each country to fix the schema.

### Subquery-based exercises

1. Update the youngest athlete. Set his/her name to `Tralalelo Tralala`.

1. Update those countries whose population is missing. Set their **population** to the average of populations.

1. Update those countries whose capital is missing. Set their **capital** to the longest among them.

1. Update those medal table entries that have `0` gold medals. Set their **gold**, **silver**, and **bronze** values to the values of `China`.
