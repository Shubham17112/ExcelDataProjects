**🔹 Remove Duplicate Values**

➡️ Used the Remove Duplicates feature from the Data tab to eliminate repeated salary entries.

**🔸 Conditional Aggregation with Formulas**
➡️ Applied SUMIF, COUNTIF, and AVERAGEIF functions in the SalaryByDepartment table to analyze salary data by department.

**🔹 Filter High-Salary Staff**
➡️ In the Staff>100K sheet, used the Filter function to display only employees with salaries above 100,000.

**🔸 INDEX Function**
➡️ Used the INDEX function to retrieve specific columns and rows as needed for dynamic referencing.
🔧 Syntax: INDEX(array, row_num, [column_num])

**🔹 SEQUENCE with COLUMNS**
➡️ Combined SEQUENCE with COLUMNS to generate a dynamic range of rows and columns.

**🔸 Match Function (will give u row number or column number)**
➡️ I have used the MATCH function with the INDEX function along with MINIFS.
🧠 Here’s how it works:

MINIFS gets the minimum value from an array based on a condition

INDEX is used to get more than one column, because MINIFS only provides one column

To use INDEX, I follow this format:
INDEX(array, row_num, [column_num])

➡️ So in array, I pass the whole table.
➡️ In row_num, I need the row that has the minimum salary — but I don’t know it directly.
➡️ So I use MATCH to find that row number.

✅ Final formula:

**=INDEX(staff, MATCH(MINIFS(staff[Salary], staff[Gender], "Male"), staff[Salary], 0), 0)**
📌 This will return the entire row of the male employee who has the minimum salary.

**🔸Count vs COUNTA**

COUNT just counts the numeric values.

COUNTA counts everything except blank cells.

**🔸Absolute Reference Vs Normal Reference**

➡️ We use absolute reference when we need a fixed cell that doesn't change when we drag the formula.

Example:
Let’s suppose you have a column A (quantity) and another column B (price).
To calculate the total price, you normally do: A1 * B1 — but if you want to use the same price in B1 for every row in column A, and calculate net price, instead of writing B1 value manually again and again...

Just use absolute reference like this: A1 * $B$1
(Shortcut key: F4 to apply the $ signs)

🔸VLOOKUP

This helps to find out values in another column based on the first column.
(Same as INDEX, where you pass row number and column number — but here, you just pass the lookup value.)

Formula:

excel
Copy
Edit
=VLOOKUP(lookup_value, table_array, col_index_num, [range_lookup])
Example:
If you want to find the price based on product name, and the product name is in column A and price is in column B:

excel
Copy
Edit
=VLOOKUP("Product1", A2:B10, 2, FALSE)
You can do the same thing using the INDEX function.



Here, from Employee ID, we extracted First Name, Last Name, Salary, and Department using both VLOOKUP and INDEX + MATCH.
![image](https://github.com/user-attachments/assets/a6775d5e-3cec-498f-a279-5b830216dc22)



INDEX + MATCH is more flexible — you can look up values in any direction and it’s also faster with large datasets.
