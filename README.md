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



# SQL Joins: Many-to-Many

## Objectives

  * Write many-to-many SQL joins
    - INNER JOIN all fields
    - INNER JOIN selected fields
    - INNER JOIN selected fields with aliases
  * Write many-to-many SQL joins that return subsets of data
  * Explain syntax and structure of many-to-many SQL joins

## Instructions

  1. Create a database called many-joins
  2. Connect to many-joins database using psql
  3. Run joins.sql file while connected to db:
    - `\i many-joins.sql`

## Notes

  * INNER JOIN all fields

    ```sql
    SELECT * FROM author
    INNER JOIN author_book
    ON author.id = author_book.author_id

    INNER JOIN book

    ON book.id = author_book.book_id;

    ```

  * INNER JOIN selected fields
    - author name
    - author email
    - book title

    ```sql
    SELECT author.name, author.email, book.title  FROM author
    INNER JOIN author_book
    ON author.id = author_book.author_id
    INNER JOIN book
    ON book.id = author_book.book_id;
    ```

  * INNER JOIN selected fields with aliases
    - author id (aliased)
    - author name
    - book id (aliased)
    - book title
    ```sql
    SELECT author.id AS author_id, author.name, book.id AS book_id, book.title FROM author
    INNER JOIN author_book
    ON author.id = author_book.author_id
    INNER JOIN book
    ON book.id = author_book.book_id;
    ```

  * INNER JOIN subset of data
    - All fields for 'Mark' and his book(s)
    ```sql
    SELECT * FROM author
    INNER JOIN author_book
    ON author.id = author_book.author_id

    INNER JOIN book
    ON book.id = author_book.book_id

    WHERE author.id = 2 ;
    -- or WHERE author.name = 'Mark'
    
    ```


  * INNER JOIN subset of data
    - All fields for 'Modern Romance' and its author(s)
    ```sql
    SELECT * FROM author
    INNER JOIN author_book
    ON author.id = author_book.author_id

    INNER JOIN book
    ON book.id = author_book.book_id

    Where book.id = 4 ;










## Resources

* [Learn - Joins Syntax](https://github.com/gSchool/sql-curriculum/blob/master/Joins.md#joins---syntax)
* [Visual Representation of SQL Joins](https://www.codeproject.com/Articles/33052/Visual-Representation-of-SQL-Joins)
