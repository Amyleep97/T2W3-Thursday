# T2W3-Thursday

# Topics

### - Aggregate Functions

### - Joins

## What are aggregate functions?

 - Functions that we apply to a group of data
  ### Common aggregate functions:
    - COUNT: Returns the number of rows. 
Example: ``` SELECT COUNT(city) FROM customers; ```
    
    - SUM: Calculates the sum of a numeric column.
Example: ``` SELECT SUM(total_amount) FROM orders; ```

    - AVG: Calculates the average of a numeric column.
Example: ```  SELECT AVG(total_amount) FROM orders; ```
    - MIN: Returns the minimum value in a column.
  Example: ``` SELECT MIN(total_amount) FROM orders; ```
    - MAX: Returns the maximum value is a column.
Examples: ``` SELECT MAX(total_amount) FROM orders; ```

  - Base Syntax: SELECT aggregate_function(column_name) FROM table_name;
  - Conditions can be used as well (WHERE condition;)


### Group by Clause

- Groups rows based on one or more columns.
- Used with Aggregate functions to perform calculations on each group.

### Syntax
  #### SELECT: column name, aggregate_function(column_name)
  #### FROM table_name
  #### GROUP BY column name;

### Example: 

``` SELECT city, COUNT(*) AS customer_count FROM customers GROUP BY city; ```

### HAVING clause
- Filters groups based on a condition.
- Used with GROUP BY clause.
### Syntax:
  #### SELECT: column name, aggregate_function(column_name)
  #### FROM table_name
  #### GROUP BY column name;
  #### HAVING condition;

### Example:

``` SELECT customer_id, SUM(total_amount) FROM orders GROUP BY customer_id HAVING customer_id=5; ```

## Introductions to Joins

- Joins combine rows from two or more tables based on a related column between them.
- Essential for retrieving data from multiple tables.
- Types: INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN
  
### Syntax:
  #### SELECT column_name1, column_name2
  #### FROM table1
  #### JOIN table2
  #### ON conditon;

 #### Fetching specific column:
 ``` SELECT customers.customer_name, SUM(orders.total_amount) FROM customers, orders WHERE ```

 - A sorter way to type it: 
  ``` SELECT c.customer_name, SUM(o.total_amount) FROM customers c, orders o WHERE ```


``` SELECT c.customer_name, SUM(o.total_amount) FROM customers c INNER JOIN orders o ON``` Then 
```c.customer_id = o.customer_id GROUP BY customer_name;```

## INNER Join

- Returns rows that have matching values in both tables.
- Only returns rows where there is a match in both tables.
  
  ### Syntax:

  #### SELECT column_name1, column_name2
  #### FROM table1
  #### INNER JOIN table2
  #### ON table1.column_name=table2.column_name;

## LEFT Join

- Returns all rows from the left table, and the matched rows from the right table.
- If there is no match in the right table, it returns NULL values.
- 
### Syntax:
  #### SELECT column_name1, column_name2
  #### FROM table1
  #### LEFT JOIN table2
  #### ON table1.column_name=table2.column_name;

### Example: 
``` SELECT * FROM customers c LEFT JOIN orders o ON c.customer_id = o.customer_id; ```

## RIGHT Join

- Returns all rows from the right table, and the matched rows from the left table.
- If there is no match in the right table, it returns NULL values.

### Syntax:
  #### SELECT column_name1, column_name2
  #### FROM table1
  #### RIGHT JOIN table2
  #### ON table1.column_name=table2.column_name;

### Example:

``` SELECT * FROM customers c RIGHT JOIN orders o ON c.customer_id = o.customer_id; ```

## FULL OUTER Join 

- Returns all rows when there is a match in either left or right table. If there is no match in either table, it returns NULL values.

### Syntax:
  #### SELECT column_name1, column_name2
  #### FROM table1
  #### FULL OUTER JOIN table2
  #### ON table1.column_name=table2.column_name;

### Example:

``` SELECT * FROM customers c FULL JOIN orders o ON c.customer_id = o.customer_id; ```

# Views:

- Create a variable to store the query then you use the view.
- How to use it:
  ![VIEW](https://github.com/user-attachments/assets/7468ffcb-a923-44d6-a1bd-dddfddc434ac)
- To see the View created use: 
- ``` \dv ```
- A public schema and under the list of relations 