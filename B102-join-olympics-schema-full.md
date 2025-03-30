[↑ Back](./README.md)

# `B102` - Joining tables / The Olympics Schema

## Schema diagram

![Schema diagram](./img/olympics-schema.png)

## Exercises

### Single JOIN

1. Return the **name** of each country together with its **gold**, **silver**, and **bronze** medals. Return a country only if it scored at least one medal.

   ```sql
   SELECT name, gold, silver, bronze
   FROM o_countries
      JOIN o_medal_table ON c_id = country_id;
   ```

   ```sql
   SELECT name, gold, silver, bronze
   FROM o_countries
      CROSS JOIN o_medal_table
   WHERE c_id = country_id;
   ```

1. Return the **name** of each country together with its **gold**, **silver**, and **bronze** medals. Return each country even if it has not scored any medals.

   ```sql
   SELECT name, gold, silver, bronze
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id;
   ```

   ```sql
   SELECT name, gold, silver, bronze
   FROM o_countries,
      o_medal_table
   WHERE c_id = country_id(+);
   ```

1. Return the **name** of each country together with its **gold**, **silver**, and **bronze** medals. Return each country even if it has not scored any medals. Return zero (`0`) values instead of the `NULL` values.

   ```sql
   SELECT name, gold, silver, bronze
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id;
   ```

   ```sql
   SELECT name, NVL(gold, 0), NVL(silver, 0), NVL(bronze, 0)
   FROM o_countries,
      o_medal_table
   WHERE c_id = country_id(+);
   ```

1. Return the **name** of each European country together with its **gold**, **silver**, and **bronze** medals. Return each country even if it has not scored any medals. Return zero (`0`) values instead of the `NULL` values.

   ```sql
   SELECT name, NVL(gold, 0), NVL(silver, 0), NVL(bronze, 0)
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   WHERE continent = 'Europe';
   ```

1. Return the **name** of each European country together with its **gold**, **silver**, and **bronze** medals. Return each country even if it has not scored any medals. Return zero (`0`) values instead of the `NULL` values.

   ```sql
   SELECT name, NVL(gold, 0), NVL(silver, 0), NVL(bronze, 0)
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   WHERE continent = 'Europe'
   ORDER BY gold, name;
   ```

   What is the problem with this query?

   ```sql
   SELECT name, NVL(gold, 0), NVL(silver, 0), NVL(bronze, 0)
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   WHERE continent = 'Europe'
   ORDER BY NVL(gold, 0), name;
   ```

   ```sql
   SELECT name, NVL(gold, 0), NVL(silver, 0), NVL(bronze, 0)
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   WHERE continent = 'Europe'
   ORDER BY 2, name;
   ```

1. Return each **continent** with its **gold**, **silver**, and **bronze** medals.

   ```sql
   SELECT continent, SUM(gold), SUM(silver), SUM(bronze)
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   GROUP BY continent;
   ```

1. Return each **continent** with its **gold**, **silver**, and **bronze** medals. Display the `"unknown"` string instead of the `NULL` values.

   ```sql
   SELECT NVL(continent, 'unknown'), SUM(gold), SUM(silver), SUM(bronze)
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   GROUP BY continent;
   ```

1. Return each **continent** with its **gold**, **silver**, and **bronze** medals. Display the `"unknown"` string instead of the `NULL` values. Order the rows by the gold medals in descending order.

   ```sql
   SELECT NVL(continent, 'unknown'), SUM(gold), SUM(silver), SUM(bronze)
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   GROUP BY continent
   ORDER BY SUM(gold) DESC;
   ```

1. Return each **continent** with its **gold**, **silver**, and **bronze** medals. Display the `"unknown"` string instead of the `NULL` values. Order the rows by the gold medals in descending order. Return a continent only if it has more than `15` gold medals.

   ```sql
   SELECT NVL(continent, 'unknown'), SUM(gold), SUM(silver), SUM(bronze)
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   GROUP BY continent
   HAVING SUM(gold) > 15
   ORDER BY SUM(gold) DESC;
   ```

1. Return each **continent** with its **gold**, **silver**, and **bronze** medals scored by those corresponding countries whose population is less than `100000`. Display the `"unknown"` string instead of the `NULL` values. Order the rows by the gold medals in descending order. Return a continent only if it has more than `15` gold medals.

   ```sql
   SELECT NVL(continent, 'unknown'), SUM(gold), SUM(silver), SUM(bronze)
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   WHERE population < 100000
   GROUP BY continent
   HAVING SUM(gold) > 15
   ORDER BY SUM(gold) DESC;
   ```
   
1. Return each **continent** with the number of their **gold medals**.

   ```sql
   SELECT continent, SUM(gold)
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   GROUP BY continent;
   ```

1. Return each **continent** with the number of their **gold medals**. Return a continent only if it has more than `50` gold medals.

   ```sql
   SELECT continent, SUM(gold)
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   GROUP BY continent
   HAVING SUM(gold) > 20;
   ```

1. Return each **continent** with the number of  **their gold medals** and the number of the **corresponding countries**. Return a continent only if it has more than `50` gold medals and at least `33` corresponding countries.

   ```sql
   SELECT continent, SUM(gold), COUNT(*)
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   GROUP BY continent
   HAVING SUM(gold) > 20 AND COUNT(*) >= 33;
   ```

1. Return each **continent** with the number of  **their gold medals** and the number of the **corresponding countries**. Return a continent only if it has more than `50` gold medals and at least `33` corresponding countries. Name the columns as `"continent"`, `"gold"`, and `"countries"`.

   ```sql
   SELECT continent, SUM(gold) AS gold, COUNT(*) AS countries
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   GROUP BY continent
   HAVING SUM(gold) > 20 AND COUNT(*) >= 33;
   ```

1. Return each **continent** with the number of  **their gold medals** and the number of the **corresponding countries**. Return a continent only if it has more than `50` gold medals and at least `33` corresponding countries. Name the columns as `"continent"`, `"gold"`, and `"countries"`. Order the rows by the gold medals in descending order.

   ```sql
   SELECT continent, SUM(gold) AS gold, COUNT(*) AS countries
   FROM o_countries
      LEFT JOIN o_medal_table ON c_id = country_id
   GROUP BY continent
   HAVING SUM(gold) > 20 AND COUNT(*) >= 33
   ORDER BY gold DESC;
   ```

1. Return the **name** of each sport discipline with the **number of corresponding events**.

   ```sql
   SELECT name, COUNT(*)
   FROM o_sport_disciplines
      LEFT JOIN o_sport_events ON d_id = discipline_id
   GROUP BY name;
   ```

   What is the problem with this query?

   ```sql
   SELECT o_sport_disciplines.name, COUNT(*)
   FROM o_sport_disciplines
      LEFT JOIN o_sport_events ON d_id = discipline_id
   GROUP BY o_sport_disciplines.name;
   ```

   What is the problem with this query?

   ```sql
   SELECT o_sport_disciplines.name, COUNT(e_id)
   FROM o_sport_disciplines
      LEFT JOIN o_sport_events ON d_id = discipline_id
   GROUP BY o_sport_disciplines.name;
   ```

   ```sql
   SELECT d.name, COUNT(e_id)
   FROM o_sport_disciplines d
      LEFT JOIN o_sport_events e ON d_id = discipline_id
   GROUP BY d.name;
   ```

1. Return the **name** of each sport discipline with the **number of corresponding events without names**.

   ```sql
   SELECT d.name, COUNT(e_id) - COUNT(e.name)
   FROM o_sport_disciplines d
      LEFT JOIN o_sport_events e ON d_id = discipline_id
   GROUP BY d.name;
   ```

1. Return the **name** of each sport discipline with the **number of corresponding events without names**. Return a discipline only if it has at least one event with the given condition.

   ```sql
   SELECT d.name, COUNT(e_id) - COUNT(e.name)
   FROM o_sport_disciplines d
      LEFT JOIN o_sport_events e ON d_id = discipline_id
   GROUP BY d.name
   HAVING COUNT(e_id) - COUNT(e.name) >= 1;
   ```

### Self-JOIN

1. Return the **name** of each country that is located on the same continent as Hungary is located.

   ```sql
   SELECT a.name
   FROM o_countries a,
      o_countries b
   WHERE b.name = 'Hungary'
   AND a.continent = b.continent;
   ```

1. Return each **capital** that starts with the same letter as Hungary's capital starts.

   ```sql
   SELECT a.capital
   FROM o_countries a,
      o_countries b
   WHERE b.name = 'Hungary'
   AND SUBSTR(a.capital, 1, 1) = SUBSTR(b.capital, 1, 1);
   ```

### Multiple JOINs

1. Return the **name** and the **gold medals** of each country that scored more medals than Hungary scored.

   ```sql
   SELECT c1.name, m1.gold
   FROM (o_countries c1
            JOIN o_medal_table m1 ON c1.c_id = m1.country_id),
        (o_countries c2
            JOIN o_medal_table m2 ON c2.c_id = m2.country_id)
   WHERE c2.name = 'Hungary'
     AND m1.gold > m2.gold;
   ```

1. Return the **name** of each athlete and the **name of his/her team**. Return only real combinations.

   ```sql
   SELECT t.name, a.name
   FROM o_athletes t
      JOIN o_teammembers ON t.a_id = o_teammembers.team_id
      JOIN o_athletes a ON o_teammembers.athlete_id = a.a_id;
   ```

1. Return the **name** of each team and the **number of its members**. Return a team only if it has at least one member.

   ```sql
   SELECT t.name, COUNT(a.a_id)
   FROM o_athletes t
      JOIN o_teammembers ON t.a_id = o_teammembers.team_id
      JOIN o_athletes a ON o_teammembers.athlete_id = a.a_id
   GROUP BY t.name;
   ```

1. Return the **name** of each team and the **number of its members**. Return a team even it has no members.

   ```sql
   SELECT t.name, COUNT(a.a_id)
   FROM o_athletes t
      LEFT JOIN o_teammembers ON t.a_id = o_teammembers.team_id
      LEFT JOIN o_athletes a ON o_teammembers.athlete_id = a.a_id
   WHERE t.team = 'yes'
   GROUP BY t.name;
   ```

1. Return the **name** and the **nationality** of each team, with the **number of its members**. Return a team even it has no members.

   ```sql
   SELECT t.name, o_countries.name, COUNT(a.a_id)
   FROM o_athletes t
      LEFT JOIN o_teammembers ON t.a_id = o_teammembers.team_id
      LEFT JOIN o_athletes a ON o_teammembers.athlete_id = a.a_id
      LEFT JOIN o_countries ON a.country_id = o_countries.c_id
   WHERE t.team = 'yes'
   GROUP BY t.name, o_countries.name;
   ```

1. Return each **continent** with the **number of the corresponding athletes**.

   ```sql
   SELECT continent, COUNT(a_id)
   FROM o_countries
      LEFT JOIN o_athletes
               ON c_id = country_id
   WHERE team = 'no'
   GROUP BY continent;
   ```

1. Return the **name** of each country with the **number of the corresponding events**.

   ```sql
   SELECT o_countries.name, COUNT(e_id)
   FROM o_countries
      LEFT JOIN o_athletes ON o_countries.c_id = o_athletes.country_id
      LEFT JOIN o_results ON o_athletes.a_id = o_results.athlete_id
      LEFT JOIN o_sport_events ON o_results.event_id = o_sport_events.e_id
   GROUP BY o_countries.name;
   ```

1. Return the **name** of each country with the **number of the corresponding disciplines**.

   ```sql
   SELECT o_countries.name, COUNT(d_id)
   FROM o_countries
      LEFT JOIN o_athletes ON o_countries.c_id = o_athletes.country_id
      LEFT JOIN o_results ON o_athletes.a_id = o_results.athlete_id
      LEFT JOIN o_sport_events ON o_results.event_id = o_sport_events.e_id
      LEFT JOIN o_sport_disciplines ON o_sport_events.discipline_id = o_sport_disciplines.d_id
   GROUP BY o_countries.name;
   ```

1. Return the **name** of each discipline with the **number of the corresponding countries**. Order the rows by the number of the corresponding countries in descending order.

   ```sql
   SELECT o_sport_disciplines.name, COUNT(o_countries.c_id)
   FROM o_sport_disciplines
      LEFT JOIN o_sport_events ON o_sport_disciplines.d_id = o_sport_events.discipline_id
      LEFT JOIN o_results ON o_sport_events.e_id = o_results.event_id
      LEFT JOIN o_athletes ON o_results.athlete_id = o_athletes.a_id
      LEFT JOIN o_countries ON o_athletes.country_id = o_countries.c_id
   GROUP BY o_sport_disciplines.name
   ORDER BY 2 DESC;
   ```