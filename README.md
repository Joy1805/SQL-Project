# SQL-Project
Adventureworks_customers database Queries
## Using MySQL for Database Querying

Code is written utilizing Workbench Software.

### Queries

4. Create a query to calculate the average annual income of customers.
    ```sql
    SELECT AVG(AnnualIncome) AS AverageAnnualIncome
    FROM customers;
    ```

5. Write a query to find customers who were born in the year 1980.
    ```sql
    SELECT *
    FROM customers
    WHERE YEAR(BirthDate) = 1980;
    ```

6. Create a query that counts the number of customers with a specific marital status (e.g., Single).
    ```sql
    SELECT COUNT(*) AS NumberOfSingleCustomers
    FROM customers
    WHERE MaritalStatus = 'Single';
    ```

7. Write a query to update the marital status of customers with a specific prefix (e.g., Mr.) to 'Married'.
    ```sql
    UPDATE adventureworks_customers
    SET MaritalStatus = 'Married'
    WHERE Prefix = 'MR.';
    ```

8. Create a query to calculate the total number of customers with a specific education level (e.g., Bachelor's degree).
    ```sql
    SELECT COUNT(*) AS NumberOfBachelorsDegree
    FROM customers
    WHERE EducationLevel = 'Bachelor\'s degree';
    ```

9. Write a query that counts the number of customers in each occupation category.
    ```sql
    SELECT Occupation, COUNT(*) AS NumberOfCustomers
    FROM customers
    GROUP BY Occupation;
    ```

10. Create a query to find the oldest customer in the dataset based on their birthdate.
    Due to the Birthdate column being in Text format, added a new column for the new date format:
    
    ```sql
    ALTER TABLE customers ADD COLUMN BirthDateFormatted DATE;
    ```

    Updated the new column in date format:
    
    ```sql
    UPDATE customers
    SET BirthDateFormatted = STR_TO_DATE(BirthDate, '%Y-%m-%d');
    ```

    Below query showing the oldest customer:
    
    ```sql
    SELECT *
    FROM customers
    ORDER BY BirthDateFormatted ASC
    LIMIT 1;
    ```
