### **Aggregate Functions in SQL**

Aggregate functions perform calculations on a set of values and return a single result.

|**Function**|**Description**|**Example**|
|---|---|---|
|**COUNT()**|Returns the number of rows matching a condition.|`COUNT(*)`|
|**SUM()**|Returns the sum of a numeric column.|`SUM(price)`|
|**AVG()**|Returns the average value of a numeric column.|`AVG(price)`|
|**MAX()**|Returns the maximum value.|`MAX(price)`|
|**MIN()**|Returns the minimum value.|`MIN(price)`|

---

### **Example of Aggregate Functions**

```
SELECT 
    COUNT(*) AS total_books, 
    AVG(price) AS avg_price, 
    MAX(year_published) AS latest_year 
FROM Books;
```

**Explanation:**  
This query calculates the total number of books, the average price, and the most recent publication year from the `Books` table.

---

### **Combining String and Aggregate Functions**

You can also combine string functions with aggregate functions.

```
SELECT 
    UPPER(genre) AS genre_name, 
    COUNT(*) AS genre_count 
FROM Books 
GROUP BY genre;
```

**Explanation:**  
This query groups books by genre, converts genre names to uppercase, and counts the number of books in each genre.