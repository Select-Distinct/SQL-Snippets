# Group by ROLLUP in SQL

These examples show various options to use the ROLLUP function to add total and sub total rows to your group by

## 1. The base GROUP BY SQL
```sql
SELECT [Year], [quarter], [monthname], count([date]) as [no of days]
FROM  [dbo].[DimDate]
WHERE [Year] = 2022
GROUP BY [Year], [quarter], [monthname]
```

## 2. Adding the ROLLUP clause

```sql
SELECT [Year], [quarter], [monthname], count([date]) as [no of days]
FROM  [dbo].[DimDate]
WHERE [Year] = 2022
-- the rollup extension add a sub total row each field
GROUP BY ROLLUP ([Year], [quarter], [monthname])
```

![Group by ROLLUP in SQL](https://www.selectdistinct.co.uk/wp-content/uploads/2023/08/ROLLUP-2-253x300.png)

## 3. Adding the ROLLUP total names

By default the ROLLUP extension places a null value for each total, with a COALESCE we can simply add a total name

```sql
SELECT coalesce ([Year],’Total All Years’) as [Year]
, coalesce ([quarter],’Total All Quarters’) as [Quarter]
, coalesce ([monthname], ‘Total All Months’) as [Month]
, count([date]) as [no of days]
FROM  [dbo].[DimDate]
WHERE [Year] = 2022
GROUP BY ROLLUP ([Year], [quarter], [monthname])
```

![Group by ROLLUP in SQL with subtotal names](https://www.selectdistinct.co.uk/wp-content/uploads/2023/08/ROLLUP-3-300x272.png)


## Read our Blog Post
[Group by ROLLUP in SQL Server](https://www.selectdistinct.co.uk/2023/08/23/group-by-rollup-in-sql-server/)
