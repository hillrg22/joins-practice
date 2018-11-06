# Intro to SQL Joins

## Objectives

* Explain the order & structure of join statements
* Write basic SQL joins: `one-to-many`
  - INNER join
  - LEFT join
  - FULL OUTER join
* Write basic SQL joins that only select certain fields
  - INNER join
  - LEFT join

## Instructions

1. Create a database called joins
2. Connect to joins database using psql
3. Run joins.sql file while connected to db:
  - `\i joins.sql`
4. read up on syntax for how to execute INNER JOIN going from 'owner' to 'pet'
  ```SQL
  SELECT * FROM owner
  INNER JOIN pet
  ON owner.id=pet.owner_id;
  ```

5. left join to see owners without Pet
  ```sql
  SELECT * FROM owner
  LEFT JOIN pet
  ON owner.id = pet.owner_id
  WHERE pet.id IS NULL;
  ```
6. full outer join to grab all data from both sides.

  ```sql
  SELECT * FROM owner
  FULL OUTER JOIN pet
  ON owner.id = pet.owner_id;
  ```

7. inner join that only selects certain fields.

  ```sql
  SELECT owner.name, pet.name AS Pet_Name, pet.age AS pet_age FROM owner
  INNER JOIN pet
  ON owner.id = pet.owner_id;
  ```



## Resources

* [Learn - Joins Syntax](https://github.com/gSchool/sql-curriculum/blob/master/Joins.md#joins---syntax)
* [Visual Representation of SQL Joins](https://www.codeproject.com/Articles/33052/Visual-Representation-of-SQL-Joins)
