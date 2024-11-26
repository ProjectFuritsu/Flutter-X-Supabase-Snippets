In Retriving the data form the supabase database, it has two types either in a form of a **single map** or in a form of **list of maps**. typically when you perform a query on supabase it returns in a form of **list of maps**, which each item of the list represents as the row from your database, and it looks like this:
```dart
[
  {"id": 1, "name": "Item 1", "description": "Description 1"},
  {"id": 2, "name": "Item 2", "description": "Description 2"}
]
```
on the other hand, when your query retrives a single row to your database, in your query you have **.single()** commonly found at the end of your query. **.single()** ensures only one row is retrived. if **list of maps** structured as JSON object, a **single map** structre represents as map, which looks like this:
```dart 
{"count": 42}
```

See the difference? **List of maps** is a array of json object while a **single map** is a json object.

