# Basic Structure of FutureBuilder Widget

When using a FutureBuilder in Flutter to display data from a Supabase query that returns a list, there are typically three main types of widgets to consider depending on the state of the FutureBuilder.

This is the full Future Builder Structure:
  ```dart
  
  FutureBuilder {
    future: _yourFuture
    builder: (context, snapshot) {
      // Loading State
      // Write your loading state code here
  
      // Error state
      // Write your Error state code here
  
      // Data state
      // Write your Data state code here
    }
  
  }
  
  ```

1. Loading State
    #### This is displayed while the Future is still loading. You can use a loading indicator or a placeholder widget.
    ```dart 
    builder: (context, snapshot) {
      if (snapshot.connectionState == ConnectionState.waiting) {
        return Center(child: CircularProgressIndicator()); // Or any loading widget
      }
    }
    ```
    
2. Error State
    #### This is displayed while the Future is still loading. You can use a loading indicator or a placeholder widget.
    ```dart
    if (snapshot.hasError) {
      return Center(
        child: Text('Error: ${snapshot.error}'), // Handle errors gracefully
      );
    }
    ```
3. Data State
    #### This is displayed while the Future is still loading. You can use a loading indicator or a placeholder widget.
    ``` dart
    if (snapshot.hasData) {
      final List data = snapshot.data ?? [];
  
      if (data.isEmpty) {
        return Center(
          child: Text('No data available'), // Handle empty list case
        );
      }
  
        return ListView.builder(
          itemCount: data.length,
          itemBuilder: (context, index) {
            final item = data[index];
            return ListTile(
              title: Text(item['name']), // Replace with your data structure
              subtitle: Text(item['description']),
            );
          },
        );
    }
    ```
  
