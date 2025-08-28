# 📘  DSA Revision Sheet + Solutions (C++)

This repository contains my solutions for **Striver's A2Z DSA Sheet**.

---

## 📑 Table of Contents
- [Question 1: Find the Largest Element in an Array](#question-1-find-the-largest-element-in-an-array)
- [Question 2: Find Second Smallest and Second Largest Element in an Array](#question-2-find-second-smallest-and-second-largest-element-in-an-array)

---

## Day 01

### Question 1: Find the Largest Element in an Array
**Link:** [Striver Link](https://takeuforward.org/data-structure/find-the-largest-element-in-an-array/)

**Example:**
```
Input: arr[] = {2, 5, 1, 3, 0}
Output: 5
```

**Intuition:**
We need to find the maximum element in the array. We can iterate through the array and keep track of the largest element seen so far.

**Brute Force:**
Sort the array and return the last element (largest)

```cpp
class Solution {
public:
    int findLargest(vector<int>& arr) {
        sort(arr.begin(), arr.end());
        return arr.back();
    }
};
```

**Better Solution:**
Sort the array and return the last element (same as brute force but more efficient sorting)

```cpp
class Solution {
public:
    int findLargest(vector<int>& arr) {
        sort(arr.begin(), arr.end());
        return arr[arr.size() - 1];
    }
};
```

**Optimal Solution:**
Linear scan through array keeping track of maximum element

```cpp
class Solution {
public:
    int findLargest(vector<int>& arr) {
        int maxElement = arr[0];
        for(int i = 1; i < arr.size(); i++) {
            if(arr[i] > maxElement) {
                maxElement = arr[i];
            }
        }
        return maxElement;
    }
};
```

**Edge Cases:**
- Empty array (handle with size check)
- Single element array
- All elements are same
- Negative numbers

**Important Notes:**
- Time Complexity: Brute/Better - O(n log n), Optimal - O(n)
- Space Complexity: All approaches - O(1)
- Optimal solution is most efficient for this problem
- Can also use max_element() function in C++ STL

---

### Question 2: Find Second Smallest and Second Largest Element in an Array
**Link:** [Striver Link](https://takeuforward.org/data-structure/find-second-smallest-and-second-largest-element-in-an-array/)

**Example:**
```
Input: arr[] = {1, 2, 4, 6, 7, 5}
Output: Second Smallest = 2, Second Largest = 6
```

**Intuition:**
We need to find both the second smallest and second largest elements. We can either sort and pick the second elements, or use a single pass to track both values.

**Brute Force:**
Sort the array and return second smallest (index 1) and second largest (index n-2)

```cpp
class Solution {
public:
    vector<int> getSecondOrderElements(vector<int>& arr) {
        sort(arr.begin(), arr.end());
        int n = arr.size();
        return {arr[1], arr[n-2]};
    }
};
```

**Better Solution:**
Sort the array and return second elements (same as brute force but more efficient)

```cpp
class Solution {
public:
    vector<int> getSecondOrderElements(vector<int>& arr) {
        sort(arr.begin(), arr.end());
        int n = arr.size();
        return {arr[1], arr[n-2]};
    }
};
```

**Optimal Solution:**
Single pass to find both second smallest and second largest

```cpp
class Solution {
public:
    vector<int> getSecondOrderElements(vector<int>& arr) {
        int n = arr.size();
        int smallest = INT_MAX, secondSmallest = INT_MAX;
        int largest = INT_MIN, secondLargest = INT_MIN;
        
        for(int i = 0; i < n; i++) {
            if(arr[i] < smallest) {
                secondSmallest = smallest;
                smallest = arr[i];
            } else if(arr[i] < secondSmallest && arr[i] != smallest) {
                secondSmallest = arr[i];
            }
            
            if(arr[i] > largest) {
                secondLargest = largest;
                largest = arr[i];
            } else if(arr[i] > secondLargest && arr[i] != largest) {
                secondLargest = arr[i];
            }
        }
        
        return {secondSmallest, secondLargest};
    }
};
```

**Edge Cases:**
- Array with less than 2 elements
- All elements are same
- Duplicate elements
- Array with only 2 elements

**Important Notes:**
- Time Complexity: Brute/Better - O(n log n), Optimal - O(n)
- Space Complexity: All approaches - O(1)
- Optimal solution handles duplicates properly
- Need to handle cases where second elements might not exist
