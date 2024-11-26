## 2 type of data structure
In retriving the data form the supabase database, it has two types either in a form of a **single map** or in a form of **list of maps**. typically when you perform a query on supabase it returns in a form of **list of maps**, which each item of the list represents as the row from your database, and it looks like this:
```dart
[
  {"id": 1, "name": "Item 1", "description": "Description 1"},
  {"id": 2, "name": "Item 2", "description": "Description 2"}
]
```
On the other hand, when your query retrives a single row to the supabase database, in your query you have **.single()** which commonly found at the end of your query. **.single()** ensures only one row is retrived, it can be a result to a aggregation, such as count, sum, etc. If **list of maps** structured as array of JSON object, a **single map** structre represents as single Json Object, which looks like this:
```dart 
{"count": 2}
```

See the difference? **List of maps** is a array of json object while a **single map** is a json object.

---
## What is the Query Structure?
Supabase query depends on what do you want to retrive, in querying you retrive a **single data**, **aggregated Data**, **an array of data**, and more. earlier, i explain the 2 types of data structure when retriving a data form the supabase. In querying, you have some choices on how are you going to retrive the data, but in this guide, ill teach you 2 approach, a query that retrives a array of Json object and a single Json object.

In this guide, I use 2 approach, the one that i store it to a variable and the one that i put it on a function.

### Query that retrives an Array of JSON Object

**Varibale Approach**
```dart
  final response = await supabase.from('your_table').select();
```

**Function Approach**
```dart
Future<List<Map<String, dynamic>>> fetchData() async {
  final response = await supabase.from('your_table').select();
  if (response.error != null) {
    throw Exception(response.error!.message);
  }
  return response.data as List<Map<String, dynamic>>;
}
```



### Query that retrives a single JSON Object

**Variable Approach**
```dart 
final response = await supabase
    .from('your_table')
    .select()
    .eq('id', 1)
    .single();

final data = response.data;
```

**Function Approach**
```dart
Future<Map<String, dynamic>> fetchSingleRowById(int id) async {
  final response = await supabase
      .from('your_table')
      .select()
      .eq('id', id)
      .single(); 

  return response.data as Map<String, dynamic>;
}
```
**Variable Aggregation Approach**

```dart
final response = await supabase
    .from('orders')
    .select('sum(price)')
    .eq('status', 'completed');

final sum = response.data['sum'];
```

**Agregation Appraoch**
```dart
Future<int> fetchActiveCount() async {
  final response = await supabase
      .from('your_table')
      .select('count')
      .eq('status', 'active');

  return response.data['count'] ?? 0;
}
```
