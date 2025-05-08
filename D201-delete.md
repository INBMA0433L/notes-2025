[↑ Back](./README.md)

# `D201` - `DELETE` statement

## Schema diagram

![Schema diagram](./img/olympics-schema.png)

## Exercises

> [!IMPORTANT]
>
> You are going to modify the state of your schema, which can cause issues in other exercises. Thus, we must guarantee that each query is being executed in the original state.
>
> Execute your query that updates the database, checks the new state, and has a `ROLLBACK` statement. Do not commit your changes.

### Basic exercises

1. Delete each medal table entry that does not have at least `1` gold medal.

1. Delete the country which name is *American Samoa*!

1. Delete the country which name is *Hungary*!

   *Why cannot we delete Hungary but American Samoa?*

### Subquery-based exercises

1. Delete each country that does not have any medals.

1. Delete each discipline that does not have any events.

1. Delete each event that which name is present and it does not have any corresponding result.

### Manually cascaded exercise

1. Delete *Hungary* (as a country) from the database with all the corresponding data!

   1. Delete the corresponding medals.

   1. Delete the corresponding results.

   1. Delete the corresponding team member entries.
   
   1. Delete the corresponding athletes.

   1. Delete the country.
