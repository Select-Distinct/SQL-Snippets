# Handling Divide by Zero errors in SQL

Here are some of the key ways to avoid being tripped up by Divide by zero errors


-- ==========================================
-- Select Distinct SQL Library
-- Pattern: case statement to fix Divide by zero in SQL
-- Function: CASE()
-- ==========================================

select Numerator, Denominator,
Case  
  When Denominator = 0 then 0
  else Numerator / Denominator



  -- ==========================================
-- Select Distinct DAX Library
-- Pattern: Percentage of Total (Specific Filter)
-- Function: CALCULATE() & DIVIDE()
-- ==========================================

select Numerator, Denominator, 
Numerator / NULLIF(Denominator,0) as Measure 
from       
  (SELECT 10 as Numerator, 0 as Denominator
