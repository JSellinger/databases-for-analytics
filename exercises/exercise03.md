# Exercise 03: MongoDB – Document Queries and Analysis

- Name:
- Course: Database for Analytics
- Module: 3
- Database Used: MongoDB
- Dataset: `restaurants-json.json`

---

## Instructions

- Import the provided `restaurants-json.json` file into MongoDB.
- All commands must be **executed by you** in the MongoDB shell or MongoDB Compass.
- For each query:
  - Include the MongoDB command in a fenced code block
  - Include a **screenshot** showing the command and its result
- Store screenshots in the `screenshots/` folder and embed them below each answer.

---

## Question 1

When importing the documents from `restaurants-json.json`, **how many documents were imported into your collection**?

### Answer
25,358 documents.

### Screenshot
The funny part is that you do not even need a command with MongoDB compass. It is at the top but I did insert the query below

```javascript
db.restaurants.find().count()
```

![Q1 Screenshot](screenshots/exercise%203%20Q1.png)
![Q1-1 Screenshot](screenshots/exercise%203%20Q1-1.png)


---

## Question 2

Before writing queries on the data, **what command do you use to set the MongoDB shell to operate on the `44661` database**?

### MongoDB Command

```javascript
use 4461
```

### Screenshot

![Q2 Screenshot](screenshots/exercise%203%20Q2.png)

---

## Question 3

Using your `restaurants` collection in the `44661` database, write the MongoDB query needed to **locate all documents in the `"Queens"` borough**.

### MongoDB Query

```javascript
db.restaurants.find({ "borough": "Queens" })
```

### Screenshot

![Q3 Screenshot](screenshots/exercise%203%20Q3.png)

---

## Question 4

Using your `restaurants` collection in the `44661` database, write the MongoDB query needed to **find the number of restaurants in the `"Queens"` borough**.

### MongoDB Query

```javascript
db.restaurants.find({ "borough": "Queens" }).count()
```

### Screenshot

![Q4 Screenshot](screenshots/exercise%203%20Q4.png)

---

## Question 5

Using your `restaurants` collection in the `44661` database, write the MongoDB query needed to **find the number of restaurants in the `"Queens"` borough whose cuisine is `"Hamburgers"`**.

### MongoDB Query

```javascript
db.restaurants.find({ "borough": "Queens", "cuisine": "Hamburgers" }).count()
```

### Screenshot

![Q5 Screenshot](screenshots/exercise%203%20Q5.png)

---

## Question 6

Using your `restaurants` collection in the `44661` database, write the MongoDB query needed to **find the number of restaurants in Zipcode `10460`**.

*Hint: Look up how to query **embedded documents**.*

### MongoDB Query

```javascript
db.restaurants.find({ "address.zipcode": "10460" }).count()
```

### Screenshot

![Q6 Screenshot](screenshots/exercise%203%20Q6.png)

---

## Question 7

Using your `restaurants` collection in the `44661` database, write the MongoDB query needed to **display only the names of restaurants in Zipcode `10460`**.

*Hint: Look up how to **project fields** in MongoDB.*

Your output should resemble:

```
{ name: "Wild Asia" }
{ name: "Terrace Cafe" }
{ name: "African Terrace" }
{ name: "Cool Zone" }
{ name: "Beaver Pond" }
...
```

### MongoDB Query

```javascript
db.restaurants.find(
   { "address.zipcode": "10460" }, 
   { "name": 1, "_id": 0 }
)
```

### Screenshot

![Q7 Screenshot](screenshots/exercise%203%20Q7.png)

---

## Question 8

Using your `restaurants` collection in the `44661` database, write the MongoDB query needed to **display only the names of restaurants whose name contains `"IHOP"`**, ignoring case.

Your results should include:
- `"Ihop"`
- `"Ihop Restaurant"`

### MongoDB Query

```javascript
db.restaurants.find(
   { "name": { $regex: /IHOP/i } },
   { "name": 1, "_id": 0 }
)
```

### Screenshot

![Q8 Screenshot](screenshots/exercise%203%20Q8.png)
