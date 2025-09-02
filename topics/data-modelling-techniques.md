# Data Modelling Techniques (ERD, Normalization)

## 1. Relational Model and ERD Diagram

- **Relational Model**: A way to structure data using tables (relations), where each table consists of rows and columns. Each row represents a record, and each column represents an attribute of the data.

- **Entity-Relationship Diagram (ERD)**: A visual representation of entities (tables) and the relationships between them. ERDs help in designing databases by showing how data is connected and how it should be organized.

## 2. Normalization and Its Benefits

- **Normalization**: The process of organizing data in a database to reduce redundancy and improve data integrity. It involves dividing large tables into smaller, related tables and defining relationships between them.
- **Benefits of Normalization**:
	- Eliminates duplicate data.
	- Ensures data consistency.
	- Makes it easier to maintain and update the database.
	- Improves query performance by structuring data efficiently.

## 3. De-normalization

- **De-normalization**: The process of combining tables to reduce the number of joins and improve read performance. It is sometimes used to optimize databases for specific queries, at the cost of introducing some redundancy.
- **When to Use**: De-normalization is useful in read-heavy systems where performance is critical and some redundancy is acceptable.
