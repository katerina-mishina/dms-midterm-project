# DBMS Mid-Term Project 

### Due July 17, 2020.

See Projects tab for step-wise project workflow.


## Normalisation Rules for Relational Databases (ACID rules)

**First Normal Form (1NF):** A table is 1NF if every cell contains a single value, not a list of values. This properties is known as atomic. 1NF also prohibits repeating group of columns such as item1, item2,.., itemN. Instead, you should create another table using one-to-many relationship.

**Second Normal Form (2NF):** A table is 2NF, if it is 1NF and every non-key column is fully dependent on the primary key. Furthermore, if the primary key is made up of several columns, every non-key column shall depend on the entire set and not part of it.

For example, the primary key of the Tweets table comprising _id_ and _user_id_. If _username_ is dependent only on _user_id_, it shall not be kept in the Tweets table (but in the User table). On the other hand, if the _location_ is dependent on the tweet as well as the particular user, then it shall be kept in the Tweets table.

**Third Normal Form (3NF):** A table is 3NF, if it is 2NF and the non-key columns are independent of each others. In other words, the non-key columns are dependent on primary key, only on the primary key and nothing else. A column shall not belong to a particular table if it is dependent on the primary key AND another column inthe table, which is not part of the primary key.

**Higher Normal Form:** 3NF has its inadequacies, which leads to higher Normal form, such as Boyce/Codd Normal form, Fourth Normal Form (4NF) and Fifth Normal Form (5NF), which is beyond the scope of this project.

We may decide to break some of the normalisation rules, for performance reason (e.g., create a column called totalTweets in User table which can be derived from another table's records); or because the end-user 'requested' for it. But make sure to properly document the decision.


### Integrity Rules
You should also apply the integrity rules to check the integrity of your design:

**Entity Integrity Rule:** The primary key cannot contain NULL. Otherwise, it cannot uniquely identify the row. For composite key made up of several columns, none of the column can contain NULL. Most of the RDBMS check and enforce this rule.

**Referential Integrity Rule:** Each foreign key value must be matched to a primary key value in the table referenced (or parent table).

* You can insert a row with a foreign key in the child table only if the value exists in the parent table.
* If the value of the key changes in the parent table (e.g., the row updated or deleted), all rows with this foreign key in the child table(s) must be handled accordingly. You could either (a) disallow the changes; (b) cascade the change (or delete the records) in the child tables accordingly; (c) set the key value in the child tables to NULL.
Most RDBMS can be setup to perform the check and ensure the referential integrity, in the specified manner.

**Business logic Integrity:** Beside the above two general integrity rules, there could be integrity (validation) pertaining to the business logic, e.g., zip code shall be 5-digit within a certain ranges, delivery date and time shall fall in the business hours; quantity ordered shall be equal or less than quantity in stock, etc. These could be carried out in validation rule (for the specific column) or programming logic.
