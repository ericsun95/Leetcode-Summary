# Binary Search

- [LeetCode Explore Card](https://leetcode.com/explore/learn/card/binary-search/)
- [一亩三分地的总结](https://www.1point3acres.com/bbs/thread-747061-1-1.html)

## Template 1
```java
public int binarySearch(int[] nums, int target){
  if(nums == null || nums.length == 0)
    return -1;

  int left = 0, right = nums.length - 1;
  while(left <= right){
    // Prevent (left + right) overflow
    int mid = left + (right - left) / 2;
    if(nums[mid] == target){ return mid; }
    else if(nums[mid] < target) { left = mid + 1; }
    else { right = mid - 1; }
  }

  // End Condition: left > right
  return -1;
}
```
Template #1 is the most basic and elementary form of Binary Search. It is the standard Binary Search Template that most high schools or universities use when they first teach students computer science. 
Template #1 is used to search for an element or condition which can be determined by accessing a single index in the array.
Distinguishing Syntax:
- Initial Condition: `left = 0, right = length-1`
- Termination: `left > right`
- Searching Left: `right = mid-1`
- Searching Right: `left = mid+1`

### Key Attributes:
Most basic and elementary form of Binary Search
Search Condition can be determined without comparing to the element's neighbors (or use specific elements around it)
No post-processing required because at each step, you are checking to see if the element has been found. If you reach the end, then you know the element is not found

## Template 2
```java
int binarySearch(int[] nums, int target){
  if(nums == null || nums.length == 0)
    return -1;

  int left = 0, right = nums.length - 1;
  while(left < right){
    // Prevent (left + right) overflow
    int mid = left + (right - left) / 2;
    if(nums[mid] == target){ return mid; }
    else if(nums[mid] < target) { left = mid + 1; }
    else { right = mid; }
  }

  // Post-processing:
  // End Condition: left == right
  if(nums[left] == target) return left;
  return -1;
}
```
### Key Attributes
An advanced way to implement Binary Search.
Use the element's right neighbor to determine if the condition is met and decide whether to go left or right
Guarantees Search Space is at least 2 in size at each step
Post-processing required. 
Loop/Recursion ends when you have 1 element left. Need to assess if the remaining element meets the condition.

### Distinguishing Syntax
- Initial Condition: `left = 0, right = length - 1`
- Termination: `left == right`
- Searching Left: `right = mid`
- Searching Right: `left = mid+1`

## Template #3

```java
int binarySearch(int[] nums, int target) {
    if (nums == null || nums.length == 0)
        return -1;

    int left = 0, right = nums.length - 1;
    while (left + 1 < right){
        // Prevent (left + right) overflow
        int mid = left + (right - left) / 2;
        if (nums[mid] == target) {
            return mid;
        } else if (nums[mid] < target) {
            left = mid;
        } else {
            right = mid;
        }
    }

    // Post-processing:
    // End Condition: left + 1 == right
    if(nums[left] == target) return left;
    if(nums[right] == target) return right;
    return -1;
}
```

### Key Attributes

An alternative way to implement Binary Search
Use the element's neighbors to determine if the condition is met and decide whether to go left or right
Guarantees Search Space is at least 3 in size at each step
Post-processing required. Loop/Recursion ends when you have 2 elements left. Need to assess if the remaining elements meet the condition.

### Distinguishing Syntax

- Initial Condition: `left = 0, right = length-1`
- Termination: `left + 1 == right`
- Searching Left: `right = mid`
- Searching Right: `left = mid`