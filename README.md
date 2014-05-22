# Database Drill One To Many Schema 
 
##Learning Competencies 

* Design database schema from problem data
* Model a one-to-many relationship in a relational database

##Summary 

 A database with a single table is not that useful &mdash; a database of any complexity will have more than one kind of "thing" it wants to keep track of.
A classroom database, for example, could have separate tables for students, teachers, classes, sections, homework assignments, grades, etc.

These tables are all related to each other through one of three types of **relations**.  One-to-many relations are the easiest to understand.

An Amazon user has many orders, but an order belongs to exactly one user.  A movie theater has multiple screens, but each screen belongs to only that movie theater.  A street has many houses on it, but a house belongs to only one street.

We design this by having a **foreign key** on the "many" table which stores the **primary key** of the "one" table.  Remember that a table's primary key uniquely identifies a row.  The <code>users</code> and <code>orders</code> table would be designed this way:

<pre>
+------------+        +-------------+
| users      |        | orders      |
+------------+        +-------------+
| id         |&lt;---\   | id          |
| first_name |     \--| user_id     |
| last_name  |        | total       |
| email      |        | address     |
| created_at |        | created_at  |
| updated_at |        | updated_at  |
+------------+        +-------------+
</pre>

The **convention** is that the **foreign key** (<code>user_id</code>, here) contains the singular version of the foreign table.  Because <tt>user_id</tt> contains an integer that corresponds to a one and only one row in the <code>users</code> table, we see that every order only has one users.  However, there could be two rows in the <code>orders</code> table with the same values in the <code>user_id</code> field.

One user has many orders, but an order has exactly one user.


##Releases

###Release 0 Design the schema

Link the <code>users</code> and <code>orders</code> tables together by clicking 'connect foreign key', pointing the <code>user_id</code> field in the <code>orders</code> table to the <code>id</code> field in the <code>users</code> table.

When you are done, take a screenshot of your schema, commit it, and issue a pull request.

<!-- ##Optimize Your Learning  -->

##Resources

* [SQL Designer](https://socrates.devbootcamp.com//sql.html)
