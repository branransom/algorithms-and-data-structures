# Algorithms and Data Structures

Companion repo to Algorithms and Data Structures course by Stephen Grider on Udemy.com

## Array Chunking
### First possible solution:

1. Create empty array to hold chunks
2. For each element in the unchunked array:
    a. Retrieve the last element in 'chunked'
    b. If last element does not exist, or if its length is equal to chunk size
1. Push a new chunk into 'chunked' with the current element
    c. Else add the current element into the chunk

### Alternative solution:

1. Create empty 'chunked' array
2. Create 'index' start at 0
3. While index is less than array.length
    a. Push a slice of length 'size' from 'array' into 'chunked'
    b. Add 'size' to index

---

## Anagrams
- Tip: can use regular expression to replace non-characters:
```javascript
    word.replace(/[^\w]/g, "").toLowerCase()
```

- First solution: Use character maps to compare number of occurrences of each letter
- Second solution: Use array.sort() to sort the strings and then compare the two
- Interviewers like to see helper functions when applicable
- When iterating over an array, use for OF
- When iterating over an object, use for IN

---

## Sentence Capitalization
### First solution:

1. Make an empty array 'words'
2. Split the input string by spaces to get an array
3. For each word in the array
    a. Uppercase the first letter of the word
    b. Join first letter with rest of the string
    c. Push result into 'words' array
4. Join 'words' into a string and return it

### Alternative Solution:
- This solution is weak because it has to treat the first character differently

1. Create 'result' which is the first character of the input string capitalized
2. For each character in string
    a. IF the character to the left is a space
        1. Capitalize it and add to 'result'
    b. ELSE
        1. Add it to 'result'

## Printing Steps
### First solution (recommended in interview setting):

1. From 0 to n (iterate through rows)
    a. Create an empty string named 'stair'
    b. From 0 to n (iterate through columns)
        1. IF the current column is equal to or less than the current row
            a. Add '#' to 'stair'
        2. ELSE
            a. Add a space to 'stair'
    c. Console log 'stair'

### Alternative solution (uses recursion... a bit trickier)
#### Recursion tips
- Figure out the bare minimum pieces of information to represent your problem
- Give reasonable default to the bare minimum pieces of info
- Check the base case. Is there any work left to do? If not, return
- Do some work. Call your function again, making sure the arguments have changed in some fashion

## Pyramid
- Should use a very similar algorithm to the Steps problem, just changing the bounds
- Equation for finding the midpoint of the array = (2 * n - 1) / 2

## Vowels
- `word.includes()` returns a boolean if a string includes the specified substring
- `array.includes()` also works. Would be more appropriate for this problem, since the order does not matter
- Alternative solution uses regular expression: `str.match(/[aeiou]/gi)`
    - if matches are found, this will return an array
    - the 'g' flag tells the regular expression to not stop after the first match
    - the 'i' flag tells the regular expression to be case-insensitive

## Spiral
### First solution

1. Create an empty array of arrays called 'results'
2. Create a counter variable, starting at 1
3. As long as (start column <= end column) AND (start row <= end row)
    a. Loop from start column to end column
        1. At results[start_row][i] assign counter variable
        2. Increment counter
    b. Increment start row
    c. Loop from start row to end row
        1. At results[i][end_column] assign counter variable
        2. Increment counter
    d. Decrement end column
    ... repeat for other two sides

## Runtime Complexity
- Describes the performance of an algorithm
- How much more processing power/time is required to run your algorithm if we double the inputs?

- For example:
    - Reverse String problem => O(n) or linear runtime
    - Steps problem => O(n^2) or quadratic runtime

### Runtime Definitions
- Constant time [O(1)]
    - No matter how many elements we're working with, the algorithm/operation/whatever will always take the same amount of time
- Logarithmic time [O(log(n))]
    - You have this if doubling the number of elements you are iterating over doesn't double the amount of work
    - Always assume searching algorithms are log(n)
- Linear time [n]
    - Iterating through all elements in a collection of data. If you have a for loop spanning from '0' to 'array.length', you probably have 'n' or linear runtime
- Quasilinear time [O(n * log(n))]
    - You have this if doubling the number of elements you are iterating over doesn't double the amount of work.
    - Always assuming that any sorting operation is n * log(n)
- Quadratic time [O(n^2)]
    - Every element in a collection has to be compared to every other element.
    - 'The handshake problem'
- Exponential time [(2^n)]
    - If you add a *single* element to a collection, the processing power required doubles

### Identifying Runtime Complexity
- Iterating with a simple for loop through a single collection => O(n)
- Iterating through half a collection => Still O(n). There are no constants in runtime
- Iterating through two *different* collections with separate for loops => O(n + m)
- Two nested for loops iterating over the same collection => O(n^2)
- Two nested loops iterating over different collections => O(n * m)
- Sorting => O(n * log(n))
- Searching a sorted array => O(log(n))

### Space Complexity
- Very similar to performance/runtime complexity
- How much more memory is required by doubling the problem set?

## Fibonacci Series
- Classic interview problem when discussing runtime complexity
- Study the recursive solution!
```javascript
function fib(n) {
  if (n < 2) {
    return n;
  }

  return fib(n - 1) + fib(n - 2);
}
```
- The recursive solution is in exponential time [O(2^n)]
- Memoization: Store the arguments of each function call along with the result. If the function is called again with the same arguments, return the precomputed result, rather than running the function again

## Data Structures
- Ways of organizing information with optimal 'runtime complexity' for adding or removing records
- JavaScript natively implements several data structures. You will still be asked about 'inferior' data structures

### Queue
- First In, First Out (FIFO)
- Interviewers may ask to implement a queue from scratch

### Weave
- Implement a peek method in queue to see whether it has values remaining
- Alternate adding values from two queues (as long as they are not undefined)

### Stack
- Use array `push()` and `pop()`

### Stack from Queue
- Use two stacks to create a queue - implement `add()`, `remove()`, and `peek()`
- Most common interview question with stacks and queues

## Linked Lists
- *Very common interview topic!!*
- LinkedList links together a list of 'nodes'
- Node has two properties - by convention, named 'data' and 'next'
- LinkedList has one property - by convention, named 'head'. 'head references the first node in the list

