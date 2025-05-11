📊 Excel Data Analysis Techniques
🔹 Remove Duplicate Values
➡️ Used the Remove Duplicates feature from the Data tab to eliminate repeated salary entries.
🔸 Conditional Aggregation with Formulas
➡️ Applied SUMIF, COUNTIF, and AVERAGEIF functions in the SalaryByDepartment table to analyze salary data by department.
🔹 Sort Function
➡️ Returns a sorted array.

📌 Formula:
=SORT(array, [sort_index], [sort_order], [by_col])

- array → the range or array you want to sort
- sort_index → e.g. 1, 2, 3 — column number to sort by
- sort_order → 1 (ascending) or -1 (descending)

✅ Returns the full table or array selected.
🔹 Filter High-Salary Staff
➡️ In the Staff>100K sheet, used the Filter function to display employees with salaries above 100,000.
🔸 INDEX Function
➡️ Retrieves specific rows/columns dynamically.
🔧 Syntax:
=INDEX(array, row_num, [column_num])
🔹 SEQUENCE with COLUMNS
➡️ Combined SEQUENCE with COLUMNS to generate a dynamic range of rows and columns.
🔸 Match Function
➡️ Used with INDEX and MINIFS.

🧠 Here's how:
- MINIFS gets the minimum value based on a condition
- MATCH finds the row number of that value
- INDEX pulls the full row based on that row number

✅ Final Formula:
=INDEX(staff, MATCH(MINIFS(staff[Salary], staff[Gender], "Male"), staff[Salary], 0), 0)

📌 Returns the entire row of the male employee with the minimum salary.
🔸 Count vs COUNTA
- COUNT → counts only numbers
- COUNTA → counts non-empty cells (everything except blanks)
🔸 Absolute Reference vs Normal Reference
➡️ Use absolute reference to keep a fixed cell (won’t change on drag).

💡 Example:
=A1 * $B$1
Use F4 to add $ signs automatically.
🔸 VLOOKUP Function
➡️ Finds a value from another column using the first column.

📌 Formula:
=VLOOKUP(lookup_value, table_array, col_index_num, [range_lookup])

Example:
=VLOOKUP("Product1", A2:B10, 2, FALSE)

You can do the same thing using INDEX + MATCH:
=INDEX(staff, MATCH($B$5, staff[Emp ID], 0), 2)

➡️ Here, from Employee ID, we extracted First Name, Last Name, Salary, and Department using both VLOOKUP and INDEX + MATCH.
➡️ INDEX + MATCH is more flexible and faster with large datasets.
🔸 XLOOKUP
➡️ =XLOOKUP(lookup_value, lookup_array, return_array, [if_not_found], [match_mode], [search_mode])

- lookup_value → what you want to find
- lookup_array → the array where you want to find that value
- return_array → what you want to return from the corresponding row or column

✅ Automatically uses exact match — no need for FALSE like in VLOOKUP.
🔸 Filter Function
➡️ Lookup functions return only the first matched value.
To return multiple rows, use FILTER.

📌 Formula:
=FILTER(array, include, [if_empty])

Example:
=FILTER(staff[First Name]&" "&staff[Last Name], staff[Salary]=MAX(staff[Salary]))
➡️ Returns all staff with the max salary.
🔸 Note
➡️ COUNTIFS, SUMIFS, and AVERAGEIFS support multiple conditions.

📌 Example:
=COUNTIFS(staff[salary], 200, staff[department], "Physics")

➡️ IF can also check multiple conditions using AND or OR:
=IF(AND(A2=200, B2="Physics"), "Yes", "No")
🔸 Pivot Table
➡️ Ctrl + T: tabular format
