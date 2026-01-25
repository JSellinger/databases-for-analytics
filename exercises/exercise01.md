# Exercise 01: World Database SQL Practice

- Name: Jacob Sellinger
- Course: Database for Analytics
- Module: 1
- Database Used: World Database

---

## Instructions

- Answer each question below.
- All SQL commands **must be executed** against the World database.
- For each SQL command:
  - Include the SQL in a fenced code block
  - Include a **screenshot** showing the command and results
- Store screenshots in the `screenshots/` folder and embed them below each answer.

---

## Question 1

**Compare and contrast the data types used for:**
- `country.Population`
- `country.LifeExpectancy`

Why were these data types selected?

### Answer
I assume that these were chosen as they are both quantitiativve data but with different types. Population is an expected integer and LifeExpectancy is a decimal.

### Screenshot

```sql
DESCRIBE country;
```
![Question 1 Screenshot](screenshots/Question%201.png)
---

## Question 2

**What is the data type of `country.IndepYear`?**
Why do you think this data type was selected?

### Answer
This was likely chosen because it is a smallint not an int. The difference is between how many bytes it uses. smallint is for whole integers that can fit within 2 bytes while int can store whole integers within 4 bytes.

### Screenshot

```sql
DESCRIBE country;
```

![Question 2 Screenshot (Same as 1)](screenshots/Question%201.png)

---

## Question 3

**Make a case for a different data type for `country.IndepYear`.**
Explain why your proposed data type might be better in some situations.

### Answer
Personally, I see no reason to switch from Smallint, maybe you could go up to int or down to tinyint but this assumes that for int we need years that long and for tinyint we can jsut abbreviate years. For example, "1997" as "97". Although, I would advise against both.

The only thing I could potentially see is a char, but that would only be useful and really not that useful if we maybe had to incorporate AD or BC or maybe use them categorically but it is not as if we could not convert the ints to chars and then use them categorically in most instances. 

---

## Question 4

Write a SQL command to **list the names of all cities in alphabetical order**.

### SQL

```sql
SELECT Name
FROM city
ORDER BY Name;
```

### Screenshot

![Question 4 Screenshot](screenshots/Question%204.png)

---

## Question 5

Write a SQL command to **list all forms of government from the `country` table**, showing **each only once**, sorted alphabetically.

### SQL

```sql
SELECT DISTINCT GovernmentForm
FROM country
ORDER BY GovernmentForm;
```

### Screenshot

![Question 5 Screenshot](screenshots/Question%205.png)

---

## Question 6

Write a SQL command to **list all countries in the `Oceania` continent**.

### SQL

```sql
SELECT Name
FROM country
WHERE Continent = 'Oceania';
```

### Screenshot

![Question 6 Screenshot](screenshots/Question%206.png)

---

## Question 7

Write a SQL command to **list the names and country code of all cities**.

### SQL

```sql
SELECT Name, CountryCode
FROM city;
```

### Screenshot

![Question 7 Screenshot](screenshots/Question%207.png)

---

## Question 8

Write a SQL command to **update the city named `"Nashville-Davidson"` to `"Nashville"`**.

### SQL

```sql
UPDATE city
SET Name = 'Nashville'
WHERE Name = 'Nashville-Davidson';
```

### Screenshot

![Question 8 Screenshot](screenshots/Question%208.png)

---

## Question 9

Write a SQL command to **insert a new country named `"Narnia"`** with a country code of `"NAR"`.
Use reasonable values for the remaining columns.

### SQL

```sql
INSERT INTO country (Code, Name, Continent, Region, Population)
VALUES ('NAR', 'Narnia', 'Europe', 'Fantasy', 1000000);
```

### Screenshot

![Q10 Screenshot - I named the screenshot wrong](screenshots/Question%2010.png)

---https://nwmissouri.instructure.com/courses

## Question 10

Write a SQL command to **delete the country with the country code `"NAR"`**.

### SQL

```sql
DELETE FROM country
WHERE Code = 'NAR';
```

### Screenshot

![Q11 Screenshot](screenshots/Question%2011.png)
