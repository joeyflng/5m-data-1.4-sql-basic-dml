# Assignment

## Brief

Write the SQL DML statements for the following questions.

## Instructions

Paste the answer as SQL in the answer code section below each question.

### Question 1

Select the minimum and maximum price per sqm of all the flats.

```sql

  SELECT MAX(RESALE_PRICE/FLOOR_AREA_SQM) AS MAX_PRICE_SQM,  MIN(RESALE_PRICE/FLOOR_AREA_SQM) AS MIN_PRICE_SQM FROM RESALE_FLAT_PRICES;

```

### Question 2

Select the average price per sqm for flats in each town.

```sql
  SELECT TOWN, AVG(RESALE_PRICE/FLOOR_AREA_SQM) AS AVG_PRICE_SQM FROM RESALE_FLAT_PRICES GROUP BY TOWN ORDER BY TOWN;
```

### Question 3

Categorize flats into price ranges and count how many flats fall into each category:

- Under $400,000: 'Budget'
- $400,000 to $700,000: 'Mid-Range'
- Above $700,000: 'Premium'
  Show the counts in descending order.

```sql
   SELECT  COUNT(RESALE_PRICE), CASE WHEN RESALE_PRICE <400000 THEN 'BUDGET' 
   WHEN RESALE_PRICE BETWEEN 400000 AND  700000 THEN 'MID-RANGE' 
   ELSE 'PREMIUM' END AS PRICE_RANGE
   FROM RESALE_FLAT_PRICES 
   GROUP BY PRICE_RANGE; 
   
   *Alternative Solution which gives the same result ==(cross check)==*
   
   *SELECT COUNT(*), PRICE_RANGE FROM 
    (SELECT  RESALE_PRICE, CASE WHEN RESALE_PRICE <400000 THEN 'BUDGET' 
     WHEN RESALE_PRICE BETWEEN 400000 AND  700000 THEN 'MID-RANGE' 
     ELSE 'PREMIUM' END AS PRICE_RANGE 
     FROM RESALE_FLAT_PRICES ) 
   GROUP BY PRICE_RANGE;*
```

### Question 4

Count the number of flats sold in each town during the first quarter of 2017 (January to March).

```sql
   select town, count(*) from RESALE_FLAT_PRICES
   where left(month,4) ='2017' and datepart('quarter', concat(month, '-01')::date)=1
   group by town
```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
