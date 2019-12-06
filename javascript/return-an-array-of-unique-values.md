### Return an array of unique values

Javascript `set()`s are usable for more than you might think.
```
let duplicatesArray = ['red', 'blue', 'green', 'green', 'yellow', 'red'];
let uniqueArray = [...new Set(duplicatesArray)];

// uniqueArray now equals ["red", "blue", "green", "yellow"]
```
