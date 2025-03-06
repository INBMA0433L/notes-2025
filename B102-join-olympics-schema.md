[↑ Back](./README.md)

# `B102` - Joining tables / The Olympics Schema

## Schema diagram

![Schema diagram](./img/olympics-schema.png)

## Exercises (warmup)

1. Try to connect the `o_countries` and `o_medal_table` tables using the following types of JOINs:

   1. `CROSS JOIN`

   1. `JOIN`

   1. `LEFT JOIN`

   1. `RIGHT JOIN`

   1. `FULL JOIN`

   1. `NATURAL JOIN`

   What types work and what is the number of returned records?


1. Try to connect the `o_sport_disciplines` and `o_sport_events` tables using the following types of JOINs:

   1. `CROSS JOIN`

   1. `JOIN`

   1. `LEFT JOIN`

   1. `RIGHT JOIN`

   1. `FULL JOIN`

   1. `NATURAL JOIN`

   What types work and what is the number of returned records?

## Exercises

1. Return the **name** of each country together with its **gold**, **silver**, and **bronze** medals. Return a country only if it scored at least one medal.

1. Return the **name** of each country together with its **gold**, **silver**, and **bronze** medals. Return each country even if it has not scored any medals.

1. Return the **name** of each country together with its **gold**, **silver**, and **bronze** medals. Return each country even if it has not scored any medals. Return zero (`0`) values instead of the `NULL` values.

1. Return the **name** of each European country together with its **gold**, **silver**, and **bronze** medals. Return each country even if it has not scored any medals. Return zero (`0`) values instead of the `NULL` values.

1. Return the **name** of each European country together with its **gold**, **silver**, and **bronze** medals. Return each country even if it has not scored any medals. Return zero (`0`) values instead of the `NULL` values.

1. Return each **continent** with its **gold**, **silver**, and **bronze** medals.

1. Return each **continent** with its **gold**, **silver**, and **bronze** medals. Display the `"unknown"` string instead of the `NULL` values.

1. Return each **continent** with its **gold**, **silver**, and **bronze** medals. Display the `"unknown"` string instead of the `NULL` values. Order the rows by the gold medals in descending order.

1. Return each **continent** with its **gold**, **silver**, and **bronze** medals. Display the `"unknown"` string instead of the `NULL` values. Order the rows by the gold medals in descending order. Return a continent only if it has more than `15` gold medals.

1. Return each **continent** with its **gold**, **silver**, and **bronze** medals scored by those corresponding countries whose population is less than `100000`. Display the `"unknown"` string instead of the `NULL` values. Order the rows by the gold medals in descending order. Return a continent only if it has more than `15` gold medals.

1. Return each **continent** with the number of their **gold medals**.

1. Return each **continent** with the number of their **gold medals**. Return a continent only if it has more than `50` gold medals.

1. Return each **continent** with the number of  **their gold medals** and the number of the **corresponding countries**. Return a continent only if it has more than `50` gold medals and at least `33` corresponding countries.

1. Return each **continent** with the number of  **their gold medals** and the number of the **corresponding countries**. Return a continent only if it has more than `50` gold medals and at least `33` corresponding countries. Name the columns as `"continent"`, `"gold"`, and `"countries"`.

1. Return each **continent** with the number of  **their gold medals** and the number of the **corresponding countries**. Return a continent only if it has more than `50` gold medals and at least `33` corresponding countries. Name the columns as `"continent"`, `"gold"`, and `"countries"`. Order the rows by the gold medals in descending order.

1. Return the **name** of each sport discipline with the **number of corresponding events**.

1. Return the **name** of each sport discipline with the **number of corresponding events without names**.

1. Return the **name** of each sport discipline with the **number of corresponding events without names**. Return a discipline only if it has at least one event with the given condition.

1. Return the **name** of each continent that is located on the same continent as Hungary is located.

1. Return each **capital** that starts with the same letter as Hungary's capital starts.

1. Return the **name** and the **gold medals** of each country that scored more medals than Hungary scored.

1. Return the **name** of each athlete and the **name of his/her team**. Return only real combinations.

1. Return the **name** of each team and the **number of its members**. Return a team only if it has at least one member.

1. Return the **name** of each team and the **number of its members**. Return a team even it has no members.

1. Return the **name** and the **nationality** of each team, with the **number of its members**. Return a team even it has no members.

1. Return each **continent** with the **number of the corresponding teams**.

1. Return the **name** of each country with the **number of the corresponding events**.

1. Return the **name** of each country with the **number of the corresponding disciplines**.

1. Return the **name** of each discipline with the **number of the corresponding countries**. Order the rows by the number of the corresponding countries in descending order.
