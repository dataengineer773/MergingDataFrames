You want to merge two DataFrames, To inner join, use merge with the on parameter to specify the column to merge on, merge defaults to inner joins. If we want to do an outer join, we can specify that with the how parameter
The same parameter can be used to specify left and right joins, We can also specify the column name in each DataFrame to merge on, If instead of merging on two columns we want to merge on the indexes of each DataFrame, we can
replace the left_on and right_on parameters with right_index=True and left_index=True, Oftentimes, the data we need to use is complex; it doesn’t always come in one piece. Instead in the real
world, we’re usually faced with disparate datasets, from multiple database queries or files. To get all
that data into one place, we can load each data query or data file into pandas as individual DataFrames
and then merge them together into a single DataFrame.
This process might be familiar to anyone who has used SQL, a popular language for doing merging
operations (called joins). While the exact parameters used by pandas will be different, they follow the
same general patterns used by other software languages and tools.
There are three aspects to specify with any merge operation. First, we have to specify the two
DataFrames we want to merge together. In the solution we named them dataframe_employees and
dataframe_sales. Second, we have to specify the name(s) of the columns to merge on—that is, the
columns whose values are shared between the two DataFrames. For example, in our solution both
DataFrames have a column named employee_id. To merge the two DataFrames we will match up the
values in each DataFrame’s employee_id column with each other. If these two columns use the same
name, we can use the on parameter. However, if they have different names we can use left_on and
right_on.
What is the left and right DataFrame? The simple answer is that the left DataFrame is the first one we
specified in merge and the right DataFrame is the second one. This language comes up again in the next
sets of parameters we will need.
The last aspect, and most difficult for some people to grasp, is the type of merge operation we want to
conduct. This is specified by the how parameter. merge supports the four main types of joins:
Inner
Return only the rows that match in both DataFrames (e.g., return any row with an employee_id
value appearing in both dataframe_employees and dataframe_sales).
Outer
Return all rows in both DataFrames. If a row exists in one DataFrame but not in the other
DataFrame, fill NaN values for the missing values (e.g., return all rows in both
dataframe_employee and dataframe_sales).
Left
Return all rows from the left DataFrame but only rows from the right DataFrame that matched with
the left DataFrame. Fill NaN values for the missing values (e.g., return all rows from
dataframe_employees but only rows from dataframe_sales that have a value for employee_id
that appears in dataframe_employees).
Right
Return all rows from the right DataFrame but only rows from the left DataFrame that matched with
the right DataFrame. Fill NaN values for the missing values (e.g., return all rows from
dataframe_sales but only rows from dataframe_employees that have a value for employee_id
that appears in dataframe_sales).
If you did not understand all of that right now, I encourage you to play around with the how parameter in
your code and see how it affects what merge returns
