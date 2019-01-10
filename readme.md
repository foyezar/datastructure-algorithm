# Data Structure & Algorithm

# 07_06 Radix Sort
```
Radix sort is a special sorting algorithm that works on lists of numbers
```

* It never makes comparisons between elements!
* It exploits the fact that information about the size of a number is encoded in the number of digits.
* More digit means a bigger number!

## Radix Sort Helpers
In order to implement radix sort, it's helpful to build a few helper functions first:
* getDigit(num, place) - returns the digit in num at the given place value

```js
function getDigit(num, i) {
  return Math.floor(Math.abs(num) / Math.pow(10, i)) % 10;
}

getDigit(12345, 0)  // 5
getDigit(12345, 1)  // 4
getDigit(12345, 2)  // 3
getDigit(12345, 3)  // 2
getDigit(12345, 4)  // 1
getDigit(12345, 5)  // 0
```

* digitCount(num) - returns the number of digits in num

```js
function digitCount(num) {
  if(num === 0) return 1;
  return Math.floor(Math.log10(Math.abs(num))) + 1;
}

digitCount(1) // 1
digitCount(25) // 2
digitCount(314) // 3
```

* mostDigits(nums) - given an array of numbers, returns the number of digits in the largest numbers in the list

```js
function mostDigits(nums) {
  let maxDigits = 0

  for (let i = 0; i < nums.length; i++) {
    maxDigits = Math.max(maxDigits, digitCount(nums[i]))
  }

  return maxDigits
}

mostDigits([1234, 56, 7]) // 4
mostDigits([1, 1, 11111, 1]) // 5
mostDigits([12, 34, 56, 78]) // 2
```

## Radix Sort Pseudocode
* Define a function that accepts list of numbers
* Figure out how many digits the largest number has
* Loop from k = 0 up to this largest number of digits
* For each iteration of the loop:
  * Create buckets for each digit (0 to 9)
  * Place each number in the corresponding bucket based on its kth digit
* Replace our existing array with values in our buckets, starting with 0 and going up to 9
* Return list at the end!

## Big O of Radix Sort

Best    | Average | Worst   | Space Complexity
----------------------------------------------
O(nk)   | O(nk)   | O(nk)   | O(n + k)

```
* n - length of array
* k - number of digits(average)
```