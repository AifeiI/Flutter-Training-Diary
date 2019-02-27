# Flutter Coding Diary
First knowledge: Everything's a Widget

## Commonly used Widget(Layout/UI)

### Scaffold

### BottomNavigationBar

### PageView

### ListView

### TextField and TextFormField
set keyboard next action not available? see the [solution](https://stackoverflow.com/a/52151733/7368747)

### Custom Widget

### Various combinations

- (BottomNavigationBar + PageView) on Scaffold

- (Tab + PageView) on Scaffold

- ListView behind the CustomView(TextField/Buttom/Other)

    Do not use Column as the parent container of the ListView. Otherwise↓
  
    Error code:
    ```dart
      @override
      Widget build(BuildContext context) {
        return Column(
          children: <Widget>[
            Card(
              child: Text('Search View'),
            ),
            ListView.builder(
              itemCount: list.length,
              itemBuilder: (context, index) {
                return _SearchListItem(
                  content: list[index].toString(),
                );
              },
            ),
          ],
        );
      }
    ```
    
    Will get the error Log:
    ```
    ...
    ... Vertical viewport was given unbounded height.
    ...
    ```
    
    Solution: Use Flexible as the parent container for the ListView
    ```dart
      @override
      Widget build(BuildContext context) {
        return Column(
          children: <Widget>[
            Card(
              child: Text('Search View'),
            ),
            // Use Expanded, Because Expanded extends Flexible
            Expanded(
              child: ListView.builder(
                itemCount: list.length,
                itemBuilder: (context, index) {
                  return _SearchListItem(
                    content: list[index].toString(),
                  );
                },
              ),
            ),
          ],
        );
      }
    ```

### Knowledge points
StatefulWidget(Life Cycle) and StatelessWidget


## Util

### RxDart

### json_serializable

### Dio

### crypto
