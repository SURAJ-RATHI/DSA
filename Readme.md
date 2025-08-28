# 📘  DSA Revision Sheet + Solutions (C++)

This repository contains my solutions for **Striver's A2Z DSA Sheet**.

---

## 📑 Table of Contents
- [Question 1: Find the Largest Element in an Array](#question-1-find-the-largest-element-in-an-array)
- [Question 2: Find Second Smallest and Second Largest Element in an Array](#question-2-find-second-smallest-and-second-largest-element-in-an-array)
- [Question 3: Check if an Array is Sorted](#question-3-check-if-an-array-is-sorted)
- [Question 4: Rotate Array by K Elements](#question-4-rotate-array-by-k-elements)
- [Question 5: Move All Zeros to the End of the Array](#question-5-move-all-zeros-to-the-end-of-the-array)

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

---

### Question 3: Check if an Array is Sorted
**Link:** [Striver Link](https://takeuforward.org/data-structure/check-if-an-array-is-sorted/)

**Example:**
```
Input: arr[] = {1, 2, 3, 4, 5}
Output: true (sorted in ascending order)

Input: arr[] = {5, 4, 3, 2, 1}
Output: false (not sorted in ascending order)
```

**Intuition:**
We need to check if the array is sorted in ascending order. We can iterate through the array and check if each element is greater than or equal to the previous element.

**Brute Force:**
Create a copy, sort it, and compare with original array

```cpp
class Solution {
public:
    bool isSorted(vector<int>& arr) {
        vector<int> sortedArr = arr;
        sort(sortedArr.begin(), sortedArr.end());
        return arr == sortedArr;
    }
};
```

**Better Solution:**
Check if array is sorted by comparing adjacent elements

```cpp
class Solution {
public:
    bool isSorted(vector<int>& arr) {
        for(int i = 1; i < arr.size(); i++) {
            if(arr[i] < arr[i-1]) {
                return false;
            }
        }
        return true;
    }
};
```

**Optimal Solution:**
Single pass checking if each element is >= previous element

```cpp
class Solution {
public:
    bool isSorted(vector<int>& arr) {
        int n = arr.size();
        for(int i = 1; i < n; i++) {
            if(arr[i] < arr[i-1]) {
                return false;
            }
        }
        return true;
    }
};
```

**Edge Cases:**
- Empty array (return true)
- Single element array (return true)
- Array with all same elements (return true)
- Array with negative numbers
- Array with duplicates

**Important Notes:**
- Time Complexity: Brute - O(n log n), Better/Optimal - O(n)
- Space Complexity: Brute - O(n), Better/Optimal - O(1)
- Optimal solution is most efficient and space-saving
- Can also check for descending order by changing comparison operator
- For strictly ascending: use `arr[i] <= arr[i-1]` instead of `<`

---

### Question 4: Rotate Array by K Elements
**Link:** [Striver Link](https://takeuforward.org/data-structure/rotate-array-by-k-elements/)

**Example:**
```
Input: arr[] = {1, 2, 3, 4, 5}, k = 2
Output: {4, 5, 1, 2, 3} (rotated right by 2 positions)

Input: arr[] = {1, 2, 3, 4, 5}, k = 3
Output: {3, 4, 5, 1, 2} (rotated right by 3 positions)
```

**Intuition:**
We need to rotate the array by k positions. We can use multiple approaches: extra space, reversal algorithm, or juggling algorithm. The reversal algorithm is most efficient.

**Brute Force:**
Use extra space to store rotated elements

```cpp
class Solution {
public:
    void rotate(vector<int>& arr, int k) {
        int n = arr.size();
        k = k % n; // Handle k > n
        
        vector<int> temp(n);
        for(int i = 0; i < n; i++) {
            temp[(i + k) % n] = arr[i];
        }
        arr = temp;
    }
};
```

**Better Solution:**
Rotate one element at a time (inefficient but simple)

```cpp
class Solution {
public:
    void rotate(vector<int>& arr, int k) {
        int n = arr.size();
        k = k % n;
        
        for(int i = 0; i < k; i++) {
            int last = arr[n-1];
            for(int j = n-1; j > 0; j--) {
                arr[j] = arr[j-1];
            }
            arr[0] = last;
        }
    }
};
```

**Optimal Solution:**
Reversal algorithm - reverse whole array, then reverse first k and last n-k elements

```cpp
class Solution {
public:
    void rotate(vector<int>& arr, int k) {
        int n = arr.size();
        k = k % n;
        
        // Reverse whole array
        reverse(arr.begin(), arr.end());
        // Reverse first k elements
        reverse(arr.begin(), arr.begin() + k);
        // Reverse remaining elements
        reverse(arr.begin() + k, arr.end());
    }
};
```

**Edge Cases:**
- k = 0 (no rotation needed)
- k > n (use modulo operation)
- k = n (array remains same)
- Empty array
- Single element array

**Important Notes:**
- Time Complexity: Brute - O(n), Better - O(n*k), Optimal - O(n)
- Space Complexity: Brute - O(n), Better - O(1), Optimal - O(1)
- Optimal solution uses reversal algorithm
- Always use `k = k % n` to handle k > n cases
- Can rotate left or right by adjusting the reversal order

**Remembering Task - Reversal Algorithm:**
- **Right Rotation:** Reverse whole array → Reverse first k → Reverse last n-k
  ```cpp
  // Right rotation by k positions
  reverse(arr.begin(), arr.end());        // Reverse whole array
  reverse(arr.begin(), arr.begin() + k);  // Reverse first k elements
  reverse(arr.begin() + k, arr.end());    // Reverse last n-k elements
  ```

- **Left Rotation:** Reverse first k → Reverse last n-k → Reverse whole array
  ```cpp
  // Left rotation by k positions
  reverse(arr.begin(), arr.begin() + k);  // Reverse first k elements
  reverse(arr.begin() + k, arr.end());    // Reverse last n-k elements
  reverse(arr.begin(), arr.end());        // Reverse whole array
  ```

---

### Question 5: Move All Zeros to the End of the Array
**Link:** [Striver Link](https://takeuforward.org/data-structure/move-all-zeros-to-the-end-of-the-array/)

**Example:**
```
Input: arr[] = {1, 0, 2, 3, 0, 4, 0, 1}
Output: {1, 2, 3, 4, 1, 0, 0, 0} (zeros moved to end, non-zeros maintain order)

Input: arr[] = {0, 0, 0, 1, 2, 3}
Output: {1, 2, 3, 0, 0, 0} (all zeros moved to end)
```

**Intuition:**
We need to move all zeros to the end while maintaining the relative order of non-zero elements. We can use two-pointer approach or count non-zeros first.

**Brute Force:**
Create new array, fill non-zeros first, then fill zeros

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& arr) {
        int n = arr.size();
        vector<int> result(n, 0);
        int index = 0;
        
        // Fill non-zeros first
        for(int i = 0; i < n; i++) {
            if(arr[i] != 0) {
                result[index++] = arr[i];
            }
        }
        
        arr = result;
    }
};
```

**Better Solution:**
Count non-zeros and fill array accordingly

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& arr) {
        int n = arr.size();
        int nonZeroCount = 0;
        
        // Count non-zeros
        for(int i = 0; i < n; i++) {
            if(arr[i] != 0) {
                nonZeroCount++;
            }
        }
        
        // Fill non-zeros first
        int index = 0;
        for(int i = 0; i < n; i++) {
            if(arr[i] != 0) {
                arr[index++] = arr[i];
            }
        }
        
        // Fill remaining with zeros
        while(index < n) {
            arr[index++] = 0;
        }
    }
};
```

**Optimal Solution:**
Two-pointer approach - one for non-zero elements, one for current position

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& arr) {
        int n = arr.size();
        int nonZeroIndex = 0;
        
        // Move all non-zeros to front
        for(int i = 0; i < n; i++) {
            if(arr[i] != 0) {
                arr[nonZeroIndex++] = arr[i];
            }
        }
        
        // Fill remaining with zeros
        while(nonZeroIndex < n) {
            arr[nonZeroIndex++] = 0;
        }
    }
};
```

**Edge Cases:**
- Array with no zeros
- Array with all zeros
- Array with single element
- Empty array
- Array with only one non-zero element

**Important Notes:**
- Time Complexity: All approaches - O(n)
- Space Complexity: Brute - O(n), Better/Optimal - O(1)
- Optimal solution modifies array in-place
- Maintains relative order of non-zero elements
- Can also use swap approach for in-place modification
