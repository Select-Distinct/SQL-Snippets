# Handling Divide by Zero Errors in SQL

## 1. The CASE Statement Pattern
```sql
SELECT 
    Numerator, 
    Denominator, 
    CASE 
        WHEN Denominator = 0 THEN 0 
        ELSE Numerator / Denominator 
    END AS CalculatedRatio 
FROM your_table;
```

## 2. The NULLIF Pattern

```sql
SELECT 
    Numerator, 
    Denominator, 
    Numerator / NULLIF(Denominator, 0) AS Measure 
FROM (SELECT 10 AS Numerator, 0 AS Denominator) AS example;
