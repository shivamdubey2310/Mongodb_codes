# MongoDB Practice Questions and Solutions Based on Business Inspection Dataset

## 🟢 Easy Questions (1–30)

### 1. Retrieve all documents from the `businesses` collection.
```javascript
db.businesses.find({})
```

### 2. Show only `business_name` for all businesses.
```javascript
db.businesses.find({}, { business_name: 1, _id: 0 })
```

### 3. Show `business_name` and `certificate_number` for all businesses.
```javascript
db.businesses.find({}, { business_name: 1, certificate_number: 1, _id: 0 })
```

### 4. Find all businesses where a violation was issued.
```javascript
db.businesses.find({ result: "Violation Issued" })
```

### 5. Find all businesses where no violation was issued.
```javascript
db.businesses.find({ result: "No Violation Issued" })
```

### 6. Get all unique sector names.
```javascript
db.businesses.distinct("sector")
```

### 7. Find all businesses located in "QUEENS VLG".
```javascript
db.businesses.find({ "address.city": "QUEENS VLG" })
```

### 8. Find all businesses with zip code 11428.
```javascript
db.businesses.find({ "address.zip": 11428 })
```

### 9. Find businesses in the "Cigarette Retail Dealer - 127" sector.
```javascript
db.businesses.find({ sector: "Cigarette Retail Dealer - 127" })
```

### 10. Find the business with certificate number 5381180.
```javascript
db.businesses.find({ certificate_number: 5381180 })
```

### 11. List the `business_name` and `date` for all businesses.
```javascript
db.businesses.find({}, { business_name: 1, date: 1, _id: 0 })
```

### 12. Find all businesses located in "NEW YORK".
```javascript
db.businesses.find({ "address.city": "NEW YORK" })
```

### 13. Find all businesses issued a violation in "QUEENS VLG".
```javascript
db.businesses.find({ result: "Violation Issued", "address.city": "QUEENS VLG" })
```

### 14. Find businesses with a certificate number greater than 6000000.
```javascript
db.businesses.find({ certificate_number: { $gt: 6000000 } })
```

### 15. Find businesses on the street "MENAHAN ST".
```javascript
db.businesses.find({ "address.street": "MENAHAN ST" })
```

### 16. List all unique cities.
```javascript
db.businesses.distinct("address.city")
```

### 17. Find businesses whose name contains "CONSTRUCTION".
```javascript
db.businesses.find({ business_name: /CONSTRUCTION/ })
```

### 18. Count the number of businesses in "STATEN ISLAND".
```javascript
db.businesses.find({ "address.city": "STATEN ISLAND" }).count()
```

### 19. Sort businesses by `certificate_number` in ascending order.
```javascript
db.businesses.find({}).sort({ certificate_number: 1 })
```

### 20. Sort businesses by `date` in descending order.
```javascript
db.businesses.find({}).sort({ date: -1 })
```

### 21. Find businesses with a zip code not equal to 10030.
```javascript
db.businesses.find({ "address.zip": { $ne: 10030 } })
```

### 22. Count how many businesses received a "No Violation Issued" result.
```javascript
db.businesses.find({ result: "No Violation Issued" }).count()
```

### 23. Retrieve the first 3 businesses sorted by `certificate_number` descending.
```javascript
db.businesses.find({}).sort({ certificate_number: -1 }).limit(3)
```

### 24. Retrieve distinct street names.
```javascript
db.businesses.distinct("address.street")
```

### 25. Find businesses where the business name starts with "A".
```javascript
db.businesses.find({ business_name: /^A/ })
```

### 26. Find businesses whose `address.number` is greater than 9000.
```javascript
db.businesses.find({ "address.number": { $gt: 9000 } })
```

### 27. Count businesses whose `sector` contains "Home Improvement".
```javascript
db.businesses.find({ sector: /Home Improvement/ }).count()
```

### 28. Find businesses in "STATEN ISLAND" or "NEW YORK".
```javascript
db.businesses.find({ "address.city": { $in: ["STATEN ISLAND", "NEW YORK"] } })
```

### 29. Retrieve the `business_name` of businesses with violations issued.
```javascript
db.businesses.find({ result: "Violation Issued" }, { business_name: 1, _id: 0 })
```

### 30. Count total number of documents in the collection.
```javascript
db.businesses.countDocuments()
```

---

## 🟠 Medium Questions (31–50)

### 31. Find businesses with a certificate number between 6000000 and 8000000.
```javascript
db.businesses.find({ certificate_number: { $gte: 6000000, $lte: 8000000 } })
```

### 32. Count how many businesses had violations issued.
```javascript
db.businesses.countDocuments({ result: "Violation Issued" })
```

### 33. Find businesses that were inspected after March 1, 2015.
```javascript
db.businesses.find({ date: { $gt: "Mar 1 2015" } })
```

### 34. List distinct street names.
```javascript
db.businesses.distinct("address.street")
```

### 35. Find businesses in either "QUEENS VLG" or "NEW YORK".
```javascript
db.businesses.find({ "address.city": { $in: ["QUEENS VLG", "NEW YORK"] } })
```

### 36. Find businesses where the street number is greater than 2000.
```javascript
db.businesses.find({ "address.number": { $gt: 2000 } })
```

### 37. Find businesses with names starting with the letter 'A'.
```javascript
db.businesses.find({ business_name: /^A/ })
```

### 38. Find businesses whose sector includes the word "Contractor".
```javascript
db.businesses.find({ sector: /Contractor/ })
```

### 39. Sort businesses by `business_name` alphabetically.
```javascript
db.businesses.find({}).sort({ business_name: 1 })
```

### 40. Sort businesses by `address.zip` in descending order.
```javascript
db.businesses.find({}).sort({ "address.zip": -1 })
```

### 41. Project only `business_name` and `sector`, rename `sector` to `category`.
```javascript
db.businesses.aggregate([
  {
    $project: {
      business_name: 1,
      category: "$sector",
      _id: 0
    }
  }
])
```

### 42. Find businesses on "FREDERICK DOUGLASS BLVD".
```javascript
db.businesses.find({ "address.street": "FREDERICK DOUGLASS BLVD" })
```

### 43. Find businesses inspected in February 2015.
```javascript
db.businesses.find({ date: /Feb .*2015/ })
```

### 44. Group businesses by `result` and count them.
```javascript
db.businesses.aggregate([
  {
    $group: {
      _id: "$result",
      count: { $sum: 1 }
    }
  }
])
```

### 45. List businesses with 'GROCERY' in their name.
```javascript
db.businesses.find({ business_name: /GROCERY/ })
```

### 46. List businesses in zip codes starting with '11'.
```javascript
db.businesses.find({ "address.zip": /^11/ })
```

### 47. Find businesses whose names contain either 'INC' or 'CORP'.
```javascript
db.businesses.find({ business_name: /INC|CORP/ })
```

### 48. Find the number of businesses per city.
```javascript
db.businesses.aggregate([
  {
    $group: {
      _id: "$address.city",
      count: { $sum: 1 }
    }
  }
])
```

### 49. Find businesses with certificate numbers ending with '4'.
```javascript
db.businesses.find({ certificate_number: /4$/ })
```

### 50. Find businesses with names longer than 20 characters.
```javascript
db.businesses.find({ $expr: { $gt: [{ $strLenCP: "$business_name" }, 20] } })
```

---

## 🔴 Hard Questions (51–60)

### 51. Group businesses by city and count the number of violations issued.
```javascript
db.businesses.aggregate([
  { $match: { result: "Violation Issued" } },
  { $group: { _id: "$address.city", count: { $sum: 1 } } }
])
```

### 52. Find the average certificate number per city.
```javascript
db.businesses.aggregate([
  { $group: { _id: "$address.city", avgCertificate: { $avg: "$certificate_number" } } }
])
```

### 53. Get the earliest inspection date for each city.
```javascript
db.businesses.aggregate([
  { $group: { _id: "$address.city", earliestDate: { $min: "$date" } } }
])
```

### 54. Find the top 3 cities with the most businesses.
```javascript
db.businesses.aggregate([
  { $group: { _id: "$address.city", count: { $sum: 1 } } },
  { $sort: { count: -1 } },
  { $limit: 3 }
])
```

### 55. List businesses sorted by street number in ascending order.
```javascript
db.businesses.find({}).sort({ "address.number": 1 })
```

### 56. Find the business with the maximum certificate number.
```javascript
db.businesses.find().sort({ certificate_number: -1 }).limit(1)
```

### 57. Calculate the total number of businesses.
```javascript
db.businesses.countDocuments({})
```

### 58. List businesses grouped by sector, sorted by count.
```javascript
db.businesses.aggregate([
  { $group: { _id: "$sector", count: { $sum: 1 } } },
  { $sort: { count: -1 } }
])
```

### 59. Find businesses whose name includes both 'CONSTRUCTION' and 'INC'.
```javascript
db.businesses.find({ business_name: /CONSTRUCTION.*INC/ })
```

### 60. List businesses with violations sorted by date descending.
```javascript
db.businesses.find({ result: "Violation Issued" }).sort({ date: -1 })
```

