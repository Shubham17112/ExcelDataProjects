Remove Duplicate Values
Used the Remove Duplicates feature from the Data tab to eliminate repeated salary entries.

Conditional Aggregation with Formulas
Applied SUMIF, COUNTIF, and AVERAGEIF functions in the SalaryByDepartment table to analyze salary data by department.

Filter High-Salary Staff
In the Staff>100K sheet, used the Filter function to display only employees with salaries above 100,000.

INDEX Function
Used the INDEX function to retrieve specific columns and rows as needed for dynamic referencing.

SEQUENCE with COLUMNS
Combined SEQUENCE with COLUMNS to generate a dynamic range of rows and columns.

Match Function (will give u row number or column number)
I have used the MATCH function with the INDEX function along with MINIFS.
Here, MINIFS gets the minimum value from an array based on a condition, and I used INDEX to get more than one column, because MINIFS only provides one column.

But to use the INDEX function, I need to follow this format:
INDEX(array, row_num, [column_num])

So in array, I will pass the whole table.
In row_num, I have to pass the row number I want — but I don’t know in which row the minimum salary is. So I will use the MATCH function for this.

sql
Copy
Edit
=INDEX(staff, MATCH(MINIFS(staff[Salary], staff[Gender], "Male"), staff[Salary], 0), 0)
This will return the entire row of the male employee who has the minimum salary.
