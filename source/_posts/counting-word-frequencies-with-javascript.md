---
title: Counting Word Frequencies with JavaScript
date: 2016-04-21 19:44:52
tags:
---

Creating a word frequency counter is a fun programming exercise. This exercise involves reading from a text file, counting the occurrences of each word, and then sorting by count in descending order. I will use Node.js for this exercise.

<!--more-->

## Step 1 - Read file from file system

With the Node.js `fs` module we can read files from the file system. We can import node modules using the `require` keyword. The `fs.readFile()` method asynchronously reads a file and a callback function is used to access the file contents. If an error occurs while reading from the file, then we throw an error which stops the execution of the program.

```js
var fs = require('fs');
var file = 'file_name.txt';

// read file from current directory
fs.readFile(file, 'utf8', function (err, data) {
  if (err) throw err;
  // the "data" variable contains the contents of the file
  ...
});
```

## Step 2 - Split text by spaces

In this step we will take the file text and split it by spaces. A file could also use tabs and new line characters to separate words so we need to support those as well. Using the JavaScript String `split()` method we can split text into an array based on a regular expression. The split method returns an array containing the separated words.

```js
function splitByWords (text) {
  // split string by spaces (including spaces, tabs, and newlines)
  var wordsArray = text.split(/\s+/);
  return wordsArray;
}
```

## Step 3 - Count the frequency of each word

We can use a JavaScript object as a map for counting the number of times each word occurs in the file. The `forEach()` method is used to iterate over an array and then perform an operation on each word in the array. Then we check if the word exists in the map and if it does we increment its count. If the word doesn't exist, then we add it to the map and give it an initial value of 1. The words are used as the object keys and the `hasOwnProperty()` method is used to check if the word exists as a key.

```js
function createWordMap (wordsArray) {

  // create map for word counts
  var wordsMap = {};
  /*
    wordsMap = {
      'Oh': 2,
      'Feelin': 1,
      ...
    }
  */
  wordsArray.forEach(function (key) {
    if (wordsMap.hasOwnProperty(key)) {
      wordsMap[key]++;
    } else {
      wordsMap[key] = 1;
    }
  });

  return wordsMap;

}
```

## Step 4 - Sort by count in descending order

The wordsMap object can tell us the count of each word but it cannot be used to maintain order because it is not possible to sort objects. Instead, we can use an array to store the words sorted in order by count. Using the `map()` method we can iterate over our words array and transform each item into a manageable object and then store it in a new array. Finally using the array `sort()` method we can sort the items in descending order.

```js
function sortByCount (wordsMap) {

  // sort by count in descending order
  var finalWordsArray = [];
  finalWordsArray = Object.keys(wordsMap).map(function (key) {
    return {
      name: key,
      total: wordsMap[key]
    };
  });

  finalWordsArray.sort(function (a, b) {
    return b.total - a.total;
  });

  return finalWordsArray;

}
```

## Step 5 - Printing out the results

Using the `console.log()` function we can print out the array of results. Since the array is sorted in descending order we know that the first item in the array has the highest count.

```js
console.log(finalWordsArray);
console.log('The word "' + finalWordsArray[0].name + '" appears the most in the file ' +
  finalWordsArray[0].total + ' times');
  
  
```


## End Result

Here is the final program that counts the word frequency of a text file.

```js
var fs = require('fs');
var file = 'evenflow_lyrics.txt';

// read file from current directory
fs.readFile(file, 'utf8', function (err, data) {

  if (err) throw err;

  var wordsArray = splitByWords(data);
  var wordsMap = createWordMap(wordsArray);
  var finalWordsArray = sortByCount(wordsMap);

  console.log(finalWordsArray);
  console.log('The word "' + finalWordsArray[0].name + '" appears the most in the file ' +
    finalWordsArray[0].total + ' times');

  /*
    output:
    [ { name: 'he', total: 10 },
      { name: 'again', total: 7 },
      { name: 'away', total: 7 },
      ... ]
    The word "he" appears the most in the file 10 times
  */

});


function splitByWords (text) {
  // split string by spaces (including spaces, tabs, and newlines)
  var wordsArray = text.split(/\s+/);
  return wordsArray;
}


function createWordMap (wordsArray) {

  // create map for word counts
  var wordsMap = {};
  /*
    wordsMap = {
      'Oh': 2,
      'Feelin': 1,
      ...
    }
  */
  wordsArray.forEach(function (key) {
    if (wordsMap.hasOwnProperty(key)) {
      wordsMap[key]++;
    } else {
      wordsMap[key] = 1;
    }
  });

  return wordsMap;

}


function sortByCount (wordsMap) {

  // sort by count in descending order
  var finalWordsArray = [];
  finalWordsArray = Object.keys(wordsMap).map(function(key) {
    return {
      name: key,
      total: wordsMap[key]
    };
  });

  finalWordsArray.sort(function(a, b) {
    return b.total - a.total;
  });

  return finalWordsArray;

}
```
