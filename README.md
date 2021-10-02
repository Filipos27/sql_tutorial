# sql_tutorial


# SQL tutorial - Window functions

Window functions perform calculations on a set of rows that are related together. But, unlike the aggregate functions, windowing functions do not collapse the result of the rows into a single value. Instead, all the rows maintain their original identity and the calculated result is returned for every row.


## Making view table

![view table](https://user-images.githubusercontent.com/77289083/135712335-aa342aac-7810-4083-a2fa-b0aeaab3a5ba.png)

## SQL Window Functions – Over Clause (without partition)

The OVER clause signifies a window of rows over which a window function is applied. It can be used with aggregate functions, like we have used with the SUM function here, thereby turning it into a window function. Or, it can also be used with non-aggregate functions that are only used as window functions (we will learn more about them in the later sections).

![1_without partition](https://user-images.githubusercontent.com/77289083/135712392-1e6543cd-8577-4a34-b65f-0bbd692bd9a5.png)


## Windowing with PARTITION BY

The PARTITION BY clause is used in conjunction with the OVER clause. It breaks up the rows into different partitions. These partitions are then acted upon by the window function.

![2_with partition](https://user-images.githubusercontent.com/77289083/135712492-ceb6f8d8-0c07-4403-8d5b-31380fb461ab.png)


## Arranging Rows within Partitions

We know that to arrange rows in a table, we can use the ORDER BY clause. So, to arrange rows within each partition, we have to modify the OVER clause with the ORDER BY clause.

![3_order by with partiton](https://user-images.githubusercontent.com/77289083/135712527-308beaa3-a5ff-4256-8522-fa03d653ddc8.png)


## Row_Number (without PARTITION BY)

Sometimes your dataset might not have a column depicting the sequential order of the rows, as is the case with our dataset. In that case, we can make use of the ROW_NUMBER() window function. It assigns a unique sequential number to each row of the table.

![row_num_without partition](https://user-images.githubusercontent.com/77289083/135712551-48f154bd-4ad8-4374-b90d-ef10abc4817c.png)


## Row_Number (with PARTITION BY)

![row_number with partition](https://user-images.githubusercontent.com/77289083/135712575-f0e1b237-3375-406e-93d5-618c32d1a912.png)

## Rank

The RANK() window function, as the name suggests, ranks the rows within their partition based on the given condition.Although rows with the same value are assigned the same rank, the subsequent rank skips the missing rank. This wouldn’t give us the desired results if we had to return “top N distinct” values from a table. Therefore we have a different function to resolve this issue.

![rank](https://user-images.githubusercontent.com/77289083/135712595-9455afbb-a880-46d3-9079-5f727ebb990d.png)


## Dense
The DENSE_RANK() function is similar to the RANK() except for one difference, it doesn’t skip any ranks when ranking rows.Overview
Here, all the ranks are distinct and sequentially increasing within each partition. As compared to the RANK() function, it has not skipped any rank within a partition.

![dense rank](https://user-images.githubusercontent.com/77289083/135712610-bf015752-7127-4b31-a002-5b5744fef75e.png)


## Nth_Value

If you want to retrieve the nth value from a window frame for an expression, then you can use the NTH_VALUE(expression, N) window function.

![nth_value](https://user-images.githubusercontent.com/77289083/135712621-0e322395-a3fb-4cef-9263-565e159ecf14.png)


## Ntile

Sometimes, you might want to sort the rows within the partition into a certain number of groups. This is useful when you want to determine the percentile, quartile, etc. a particular row falls into. The NTILE() function is used for such purposes. It returns the group number for each of the rows in the partition.

![qaurtile](https://user-images.githubusercontent.com/77289083/135712644-efbcc1ab-8e91-4286-9db0-2dd696fe2b7f.png)


## Lead

Often, you might want to compare the value of the current row to that of the preceding or succeeding row. It helps in the easy analysis of the data. The LEAD() and LAG() window functions are there just for this purpose.

![lead](https://user-images.githubusercontent.com/77289083/135712657-6c4986e8-a2d0-4a14-acb4-d28f2812715f.png)

## Lag

![lag](https://user-images.githubusercontent.com/77289083/135712668-bce11d4a-fab3-4973-ac3a-873788b30aef.png)
