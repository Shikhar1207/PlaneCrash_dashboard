
# SQL Queries for Plane Crash Dashboard

This markdown file contains all the SQL queries used to extract and summarize data from the `planecrash` table to support visualizations in the Power BI dashboard.

---

## 1. Total Summary KPIs

- Total number of crashes:
```sql
SELECT COUNT(*) AS total_crashes FROM planecrash;
```

- Total fatalities:
```sql
SELECT SUM(`Total fatalities`) AS total_fatalities FROM planecrash;
```

- Total number of people onboard (crew + passengers):
```sql
SELECT SUM(`Crew on board`) + SUM(CAST(`Pax on board` AS UNSIGNED)) AS total_onboard FROM planecrash;
```

- Most common crash cause:
```sql
SELECT `Crash cause`, COUNT(*) AS count
FROM planecrash
GROUP BY `Crash cause`
ORDER BY count DESC
LIMIT 1;
```

---

## 2. Crashes Over Time (Year-wise Trend)

```sql
SELECT YEAR(Date) AS year, COUNT(*) AS crash_count
FROM planecrash
GROUP BY year
ORDER BY year;
```

---

## 3. Crashes by Location

- Crashes by country:
```sql
SELECT Country, COUNT(*) AS crashes
FROM planecrash
GROUP BY Country
ORDER BY crashes DESC;
```

- Crashes by region:
```sql
SELECT Region, COUNT(*) AS crashes
FROM planecrash
GROUP BY Region
ORDER BY crashes DESC;
```

---

## 4. Crashes by Flight Phase

```sql
SELECT `Flight phase`, COUNT(*) AS crash_count
FROM planecrash
GROUP BY `Flight phase`
ORDER BY crash_count DESC;
```

---

## 5. Top Aircraft Models by Number of Crashes

```sql
SELECT Aircraft, COUNT(*) AS crash_count
FROM planecrash
GROUP BY Aircraft
ORDER BY crash_count DESC
LIMIT 10;
```

---

## 6. Fatality Breakdown

```sql
SELECT 
    SUM(`Crew fatalities`) AS total_crew_fatalities,
    SUM(`PAX fatalities`) AS total_pax_fatalities,
    SUM(CAST(`Other fatalities` AS UNSIGNED)) AS total_other_fatalities
FROM planecrash;
```

---

## 7. Crashes by Cause

```sql
SELECT `Crash cause`, COUNT(*) AS crash_count
FROM planecrash
GROUP BY `Crash cause`
ORDER BY crash_count DESC;
```

---

## 8. Top 10 Most Fatal Crashes

```sql
SELECT Date, Aircraft, Operator, Country, `Total fatalities`, `Crash cause`
FROM planecrash
ORDER BY `Total fatalities` DESC
LIMIT 10;
```

---

## 9. Crashes by Decade

```sql
SELECT 
  CONCAT(FLOOR(YEAR(Date)/10)*10, 's') AS decade, 
  COUNT(*) AS crashes
FROM planecrash
GROUP BY decade
ORDER BY decade;
```

---

## 10. Survivability Analysis

```sql
SELECT Survivors, COUNT(*) AS crash_count
FROM planecrash
GROUP BY Survivors;
```

---

## 11. Year-wise Fatalities Trend

```sql
SELECT 
  YEAR(Date) AS year, 
  SUM(`Total fatalities`) AS fatalities
FROM planecrash
GROUP BY year
ORDER BY year;
```

---

## 12. Crashes by Crash Site Type

```sql
SELECT `Crash site`, COUNT(*) AS crash_count
FROM planecrash
GROUP BY `Crash site`
ORDER BY crash_count DESC;
```

---
