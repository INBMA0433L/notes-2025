[↑ Back](./README.md)

# `D102` - `DELETE` statement

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

### Subquery-based exercises

1. Delete each country that does not have any medals.

1. Delete each discipline that does not have any events.

1. Delete each event that which name is missing and it does not have any corresponding result.

### Manually cascaded exercises

1. Delete each event that has exactly `3` results.

   1. What events must be deleted?

   1. Delete the corresponding results.

   1. Delete the events.

1. Delete *Hungary* (as a country) from the database with all the corresponding data!

   1. Delete the corresponding medals.

   1. Delete the corresponding results.

   1. Delete the corresponding team member entries.

   1. Delete the corresponding athletes.

   1. Delete the country.

1. Delete each country from the database with all the corresponding data that have any medals but not participated in any events.

   1. What countries must be deleted?

   1. Delete the corresponding medal entries.

   1. Delete the corresponding team member entries.

   1. Delete the corresponding athletes.

   1. Delete the countries.

1. Delete each country from the database that participated in any event of any discipline whose name starts with the letter `W`.

   1. What countries must be deleted?

   1. Delete the corresponding results.

   1. Delete the corresponding team member entries.

   1. Delete the corresponding athletes.

   1. Delete the corresponding medal entries.

   1. Delete the countries.