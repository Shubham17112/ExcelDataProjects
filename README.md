Q) All of this Buiness Question has been answered 

🔸How many calls we are getting by customer?
🔸How satisfied are our customers?
![image](https://github.com/user-attachments/assets/65dad295-d1c5-46da-b69a-50cc22129fee)



🔸Who are our top 10 customers?

🔸Top 10 customers for a specific representative?
![image](https://github.com/user-attachments/assets/e64ebcf1-ee8f-4c3e-97cc-5693878bd8b8)

🔸Call duration analysis
![image](https://github.com/user-attachments/assets/218a687c-36ae-4785-bb4f-0e83952aafa5)

🔸How busy is our call centre in 2023?
![image](https://github.com/user-attachments/assets/a1280844-b021-4c2b-9777-4ceb5d4d05a7)

🔸YTD Sales Analysis
![image](https://github.com/user-attachments/assets/16b1d9a0-5fb3-42eb-9da6-8c1e3bf3c6f9)

🔸Which days of week are the busiest?
![image](https://github.com/user-attachments/assets/35105594-512f-40f2-a551-e2359809cad3)

![image](https://github.com/user-attachments/assets/40c51165-6be2-40c6-bbf7-41e6559c5702)

**🔹 Remove Duplicate Values**

➡️ Used the Remove Duplicates feature from the Data tab to eliminate repeated salary entries.

**🔸 Conditional Aggregation with Formulas**
➡️ Applied SUMIF, COUNTIF, and AVERAGEIF functions in the SalaryByDepartment table to analyze salary data by department.

🔹 Sort Function

➡️ It returns the sorted array

➡️ **=SORT(array, [sort_index], [sort_order], [by_col])**
array → the range or array you want to sort

sort_index → e.g. 1, 2, 3 — it's the column number of the array you want to sort by

sort_order → either 1 (ascending) or -1 (descending)

It will return the full table — all rows or full array you selected

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


➡️ **=VLOOKUP(lookup_value, table_array, col_index_num, [range_lookup])**

Example:
If you want to find the price based on product name, and the product name is in column A and price is in column B:


➡️ **=VLOOKUP("Product1", A2:B10, 2, FALSE)**
You can do the same thing using the INDEX function.

➡️ **=INDEX(staff,MATCH($B$5,staff[Emp ID],0),2)**



➡️ Here, from Employee ID, we extracted First Name, Last Name, Salary, and Department using both VLOOKUP and INDEX + MATCH.
![image](https://github.com/user-attachments/assets/a6775d5e-3cec-498f-a279-5b830216dc22)



➡️ INDEX + MATCH is more flexible — you can look up values in any direction and it’s also faster with large datasets.

🔸 **Xlookup**
➡️ =XLOOKUP(lookup_value, lookup_array, return_array, [if_not_found], [match_mode], [search_mode])

This lookup can search in any row or column (not limited like VLOOKUP or HLOOKUP).

➡️lookup_value → what you want to find

➡️lookup_array → the array where you want to find that value

➡️return_array → what you want to return from the corresponding row or column

✅ It automatically uses exact match by default — no need to add FALSE like in VLOOKUP.

🔸**Filter Function**

➡️ Every lookup function only provides the first matched value based on the condition.
But what if there are two rows that match the condition?

In that case, only the first one will come.

To avoid this, we use the FILTER function.

➡️ =FILTER(array, include, [if_empty])

Example:

=FILTER(staff[First Name]&" "&staff[Last Name], staff[Salary]=MAX(staff[Salary]))
This will return all staff whose salary is equal to the max salary — not just the first one.


🔸Note:

➡️ COUNTIFS, SUMIFS, and AVERAGEIFS can check more than one condition at the same time.

Example:


➡️ **=COUNTIFS(staff[salary], 200, staff[department], "Physics")**

This will count how many rows have:

Salary = 200

AND Department = "Physics"

➡️ ⚠️ Important Difference with IF:

The regular IF function can only check one condition at a time, like:



➡️ **=IF(A2=200, "Yes", "No")**
But if you want to check multiple conditions in IF, you need to use it with AND or OR, like:


➡️ **=IF(AND(A2=200, B2="Physics"), "Yes", "No")**

So technically:

IF can check more than one condition

But you must manually use AND or OR inside it
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

🔸 **Pivot Table**

Ctrl + T : tabular formate
