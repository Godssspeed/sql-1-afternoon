<img src="https://s3.amazonaws.com/devmountain/readme-logo.png" width="250" align="right">

# Project Summary

In this project we will be practicing inserting and querying data using SQL. We'll make use of a handy online tool provided by DevMountain that will allow us to write SQL online. <a href="https://postgres.devmountain.com/">Click me</a>

On the left are the Tables with their fields, the right is where we will be writing our queries, and the bottom is where we will see our results.

Any new tables or records that we add into the database will be removed after you refresh the page.

Use [www.sqlteaching.com](http://www.sqlteaching.com/) or [sqlbolt.com](http://sqlbolt.com/) as resources for the missing keywords you'll need.

## Table - People

### Instructions

1. Create a table called person that records a person's id, name, age, height ( in cm ), city, favorite_color.

   - id should be an auto-incrementing id/primary key - Use type: SERIAL

   CREATE person (
   id SERIAL,
   name VARCHAR(255),
   age: INTEGER,
   height: DECIMAL,
   city: VARCHAR(255),
   favorite_color: VARCHAR(255),
   )

2. Add 5 different people into the person database. \* Remember to not include the person_id because it should auto-increment.
   INSERT INTO person (name, age, height, city, favorite_color)
   VALUES('Will', 25, 182.88, 'Chicago', 'Red' );

INSERT INTO person (name, age, height, city, favorite_color)
VALUES('Roy', 28, 185.42, 'Frisco', 'Orange' );

INSERT INTO person (name, age, height, city, favorite_color)
VALUES('Geno', 27, 167.64, 'Chicago', 'Blue');

INSERT INTO person (name, age, height, city, favorite_color)
VALUES('Leanne', 29, 165.09, 'Grand Prarie', 'Purple');

INSERT INTO person (name, age, height, city, favorite_color)
VALUES('Redine', 60, 160.02, 'Monroe', 'Money' );

3. List all the people in the person table by height from tallest to shortest.
   SELECT name FROM person ORDER BY height

4. List all the people in the person table by height from shortest to tallest.
   SELECT name FROM person ORDER BY height DESC

5. List all the people in the person table by age from oldest to youngest.
   SELECT name FROM person ORDER BY age DESC

6. List all the people in the person table older than age 20.
   SELECT name FROM person WHERE age >= 20

7. List all the people in the person table that are exactly 18.
   SELECT name FROM person WHERE age = 18

8. List all the people in the person table that are less than 20 and older than 30.
   SELECT name FROM person WHERE age < 20 AND age > 30

   <!-- Should use OR instead -->

9. List all the people in the person table that are not 27 (Use not equals).

SELECT name FROM person WHERE age NOT IN (27)

10. List all the people in the person table where their favorite color is not red.

SELECT name FROM person WHERE favorite_color NOT IN ('Red')

11. List all the people in the person table where their favorite color is not red and is not blue.

SELECT name FROM person WHERE favorite_color NOT IN ('Red','Blue')

12. List all the people in the person table where their favorite color is orange or green.

SELECT name FROM person WHERE favorite_color IN ('Orange','Green')

13. List all the people in the person table where their favorite color is orange, green or blue (use IN).

SELECT name FROM person WHERE favorite_color IN ('Orange','Green','Blue')

14. List all the people in the person table where their favorite color is yellow or purple (use IN).

SELECT name FROM person WHERE favorite_color IN ('Yellow','Purple')/

### Solution

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
CREATE TABLE person ( person_id SERIAL, name VARCHAR(200), age INTEGER, height INTEGER, city VARCHAR(200), favorite_color VARCHAR(200) );
```

</details>

<details>

<summary> <code> #2 </code> </summary>

```sql
INSERT INTO person ( name, age, height, city, favorite_color ) VALUES ( 'First Last', 21, 182, 'City', 'Color' );
```

</details>

<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT * FROM person ORDER BY height DESC;
```

</details>

<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT * FROM person ORDER BY height ASC;
```

</details>

<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT * FROM person ORDER BY age DESC;
```

</details>

<details>

<summary> <code> #6 </code> </summary>

```sql
SELECT * FROM person WHERE age > 20;
```

</details>

<details>

<summary> <code> #7 </code> </summary>

```sql
SELECT * FROM person WHERE age = 18;
```

</details>

<details>

<summary> <code> #8 </code> </summary>

```sql
SELECT * FROM person WHERE age < 20 OR age > 30;
```

</details>

<details>

<summary> <code> #9 </code> </summary>

```sql
SELECT * FROM person WHERE age != 27;
```

</details>

<details>

<summary> <code> #10 </code> </summary>

```sql
SELECT * FROM person WHERE favorite_color != 'red';
```

</details>

<details>

<summary> <code> #11 </code> </summary>

```sql
SELECT * FROM person WHERE favorite_color != 'red' AND favorite_color != 'blue';
```

</details>

<details>

<summary> <code> #12 </code> </summary>

```sql
SELECT * FROM person WHERE favorite_color = 'orange' OR favorite_color = 'green';
```

</details>

<details>

<summary> <code> #13 </code> </summary>

```sql
SELECT * FROM person WHERE favorite_color IN ( 'orange', 'green', 'blue' );
```

</details>

<details>

<summary> <code> #14 </code> </summary>

```sql
SELECT * FROM person WHERE favorite_color IN ( 'yellow', 'purple' )
```

</details>

</details>

## Table - orders

### Instructions

1. Create a table called orders that records: person_id, product_name, product_price, quantity.

CREATE TABLE orders (
person_id SERIAL,
product_name VARCHAR(255),
product_price decimal,
quantity INTEGER
)

2. Add 5 orders to the orders table.
   - Make orders for at least two different people.
   - person_id should be different for different people.
     INSERT INTO orders (product_name, product_price, quantity)
     VALUES('Xbox One', 499.99, 2);

INSERT INTO orders (product_name, product_price, quantity)
VALUES('PS4', 399.99, 1);

INSERT INTO orders (product_name, product_price, quantity)
VALUES('Switch', 299.99, 3);

INSERT INTO orders (product_name, product_price, quantity)
VALUES('RTX', 1549.99, 1);

INSERT INTO orders (product_name, product_price, quantity)
VALUES('iPad', 899.99, 2)

3. Select all the records from the orders table.
   SELECT \* FROM orders
4. Calculate the total number of products ordered.
   SELECT SUM(quantity) FROM orders
5. Calculate the total order price.
   SELECT SUM(product_price \* quantity) FROM orders
6. Calculate the total order price by a single person_id.
   SELECT SUM(product_price \* quantity) FROM orders WHERE person_id = 1

### Solution

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
CREATE TABLE orders ( person_id SERIAL, product_name VARCHAR(200), product_price NUMERIC, quantity INTEGER );
```

</details>

<details>

<summary> <code> #2 </code> </summary>

```sql
INSERT INTO orders ( person_id, product_name, product_price, quantity ) VALUES ( 0, 'Product', 12.50, 2 );
```

</details>

<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT * FROM orders;
```

</details>

<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT SUM(quantity) FROM orders;
```

</details>

<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT SUM(product_price * quantity) FROM orders;
```

</details>

<details>

<summary> <code> #6 </code> </summary>

```sql
/* The value of person_id depends on what IDs you used. Use a valid ID from your table */
SELECT SUM(product_price * quantity) FROM orders WHERE person_id = 0;
```

</details>

</details>

## Table - artist

### Instructions

1. Add 3 new artists to the artist table. ( It's already created )
   INSERT INTO artist (name)
   VALUES('JAY Z');

INSERT INTO artist (name)
VALUES('Future');

INSERT INTO artist (name)
VALUES('Lil Wayne');

2. Select 10 artists in reverse alphabetical order.
   SELECT name FROM artist ORDER BY name LIMIT 10
3. Select 5 artists in alphabetical order.
   SELECT name FROM artist ORDER BY name LIMIT 5
4. Select all artists that start with the word 'Black'.
   SELECT name FROM artist WHERE name LIKE 'Black%'
5. Select all artists that contain the word 'Black'.
   SELECT name FROM artist WHERE name LIKE '%Black%'

### Solution

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
INSERT INTO artist ( name ) VALUES ( 'artist name' );
```

</details>

<details>

<summary> <code> #2 </code> </summary>

```sql
SELECT * FROM artist ORDER BY name DESC LIMIT 10;
```

</details>

<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT * FROM artist ORDER BY name ASC LIMIT 5;
```

</details>

<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT * FROM artist WHERE name LIKE 'Black%';
```

</details>

<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT * FROM artist WHERE name LIKE '%Black%';
```

</details>

</details>

## Table - employee

### Instructions

1. List all employee first and last names only that live in Calgary.
   SELECT first_name,last_name FROM employee WHERE city IN ('Calgary')

2. Find the birthdate for the youngest employee.
   SELECT first_name,last_name,birth_date FROM employee ORDER BY birth_date DESC LIMIT 1

3. Find the birthdate for the oldest employee.
   SELECT first_name,last_name,birth_date FROM employee ORDER BY birth_date LIMIT 1
4. Find everyone that reports to Nancy Edwards (Use the ReportsTo column).
   - You will need to query the employee table to find the Id for Nancy Edwards
     SELECT first_name,last_name FROM employee WHERE reports_to = 2
5. Count how many people live in Lethbridge.
   SELECT COUNT (first_name) FROM employee WHERE city IN ('Lethbridge')

### Solution

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
SELECT first_name, last_name FROM employee WHERE city = 'Calgary';
```

</details>

<details>

<summary> <code> #2 </code> </summary>

```sql
SELECT MAX(birth_date) from employee;
```

</details>

<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT MIN(birth_date) from employee;
```

</details>

<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT * FROM employee WHERE reports_to = 2;
```

</details>

<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT COUNT(*) FROM employee WHERE city = 'Lethbridge';
```

</details>

</details>

## Table - invoice

### Instructions

1. Count how many orders were made from the USA.
   SELECT COUNT (invoice_id) FROM invoice WHERE billing_country IN ('USA')
2. Find the largest order total amount.
   SELECT total FROM invoice ORDER BY total DESC LIMIT 1
3. Find the smallest order total amount.
   SELECT total FROM invoice ORDER BY total LIMIT 1
4. Find all orders bigger than \$5.
   SELECT invoice_id, customer_id, invoice_date FROM invoice WHERE total > 5
5. Count how many orders were smaller than \$5.
   SELECT COUNT (total) FROM invoice WHERE total >5
6. Count how many orders were in CA, TX, or AZ (use IN).
   SELECT COUNT (total) FROM invoice WHERE billing_state IN ('CA','TX','AZ')
7. Get the average total of the orders.
   SELECT AVG(total) FROM invoice
8. Get the total sum of the orders.
   SELECT AVG(total) FROM invoice

### Solution

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
SELECT COUNT(*) FROM invoice WHERE billing_country = 'USA';
```

</details>

<details>

<summary> <code> #2 </code> </summary>

```sql
SELECT MAX(total) FROM invoice;
```

</details>

<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT MIN(total) FROM invoice;
```

</details>

<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT * FROM invoice WHERE total > 5;
```

</details>

<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT COUNT(*) FROM invoice WHERE total < 5;
```

</details>

<details>

<summary> <code> #6 </code> </summary>

```sql
SELECT COUNT(*) FROM invoice WHERE billing_state in ('CA', 'TX', 'AZ');
```

</details>

<details>

<summary> <code> #7 </code> </summary>

```sql
SELECT AVG(total) FROM invoice;
```

</details>

<details>

<summary> <code> #8 </code> </summary>

```sql
SELECT SUM(total) FROM invoice;
```

</details>

</details>

## Contributions

If you see a problem or a typo, please fork, make the necessary changes, and create a pull request so we can review your changes and merge them into the master repo and branch.

## Copyright

© DevMountain LLC, 2017. Unauthorized use and/or duplication of this material without express and written permission from DevMountain, LLC is strictly prohibited. Excerpts and links may be used, provided that full and clear credit is given to DevMountain with appropriate and specific direction to the original content.

<p align="center">
<img src="https://s3.amazonaws.com/devmountain/readme-logo.png" width="250">
</p>
