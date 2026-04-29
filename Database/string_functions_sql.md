### **String Functions in SQL**

Here are some commonly used SQL string functions:

|**Function**|**Description**|**Example**|
|---|---|---|
|**UPPER()**|Converts text to uppercase.|`UPPER('sql')` → `'SQL'`|
|**LOWER()**|Converts text to lowercase.|`LOWER('SQL')` → `'sql'`|
|**LENGTH()**|Returns the length of a string.|`LENGTH('hello')` → `5`|
|**SUBSTRING()**|Extracts a portion of a string.|`SUBSTRING('database', 1, 4)` → `'data'`|
|**TRIM()**|Removes leading and trailing spaces.|`TRIM(' hello ')` → `'hello'`|
|**CONCAT()**|Concatenates two or more strings.|`CONCAT('SQL', 'Tutorial')` → `'SQLTutorial'`|
|**POSITION()**|Finds the position of parameter specified.|`POSITION('FIRST_NAME', 'A')`|

---

### **Example of String Functions**

```
SELECT 
    UPPER(title) AS upper_title, 
    LOWER(author) AS lower_author, 
    LENGTH(title) AS title_length 
FROM Books;
```

**Explanation:**  
This query retrieves the book titles in uppercase, authors in lowercase, and the length of each title from the `Books` table.