# 📘 DSA Revision Sheet + Solutions (C++)

This repository contains my solutions for **Striver's A2Z DSA Sheet**.

---

## 📑 Table of Contents
- [Question 1: Find the Largest Element in an Array](#question-1-find-the-largest-element-in-an-array)
- [Question 2: Find Second Smallest and Second Largest Element in an Array](#question-2-find-second-smallest-and-second-largest-element-in-an-array)
- [Question 3: Check if an Array is Sorted](#question-3-check-if-an-array-is-sorted)
- [Question 4: Rotate Array by K Elements](#question-4-rotate-array-by-k-elements)
- [Question 5: Move All Zeros to the End of the Array](#question-5-move-all-zeros-to-the-end-of-the-array)
- [Question 6: Union of Two Sorted Arrays](#question-6-union-of-two-sorted-arrays)
- [Question 7: Find the Missing Number in an Array](#question-7-find-the-missing-number-in-an-array)
- [Question 8: Count Maximum Consecutive Ones in the Array](#question-8-count-maximum-consecutive-ones-in-the-array)
- [Question 9: Find the Number that Appears Once and the Other Numbers Twice](#question-9-find-the-number-that-appears-once-and-the-other-numbers-twice)
- [Question 10: Longest Subarray with Given Sum K](#question-10-longest-subarray-with-given-sum-k)
- [Question 11: Two Sum - Check if a Pair with Given Sum Exists in Array](#question-11-two-sum-check-if-a-pair-with-given-sum-exists-in-array)
- [Question 12: Sort an Array of 0s, 1s and 2s](#question-12-sort-an-array-of-0s-1s-and-2s)
- [Question 13: Find the Majority Element that Occurs More than N/2 Times](#question-13-find-the-majority-element-that-occurs-more-than-n-2-times)
- [Question 14: Kadane's Algorithm - Maximum Subarray Sum in an Array](#question-14-kadanes-algorithm-maximum-subarray-sum-in-an-array)
- [Question 15: Stock Buy and Sell](#question-15-stock-buy-and-sell)
- [Question 16: Next Permutation - Find Next Lexicographically Greater Permutation](#question-16-next-permutation-find-next-lexicographically-greater-permutation)
- [Question 17: Longest Consecutive Sequence in an Array](#question-17-longest-consecutive-sequence-in-an-array)
- [Question 18: Spiral Traversal of Matrix](#spiral-traversal-of-matrix)
- [Question 19: Count Subarray Sum Equals K](#count-subarray-sum-equals-k)
- [Question 20: Pascal's Triangle](#pascals-triangle)
- [Question 21: Majority Elements (n/3) - Find Elements that Appear More than N/3 Times](#question-21-majority-elements-n3---find-elements-that-appear-more-than-n3-times)
- [Question 22: 3-Sum - Find Triplets that Add Up to Zero](#question-22-3-sum---find-triplets-that-add-up-to-zero)
- [Question 23: 4-Sum - Find Quads that Add Up to Target Value](#question-23-4-sum---find-quads-that-add-up-to-target-value)
- [Question 24: Length of Longest Subarray with Zero Sum](#question-24-length-of-longest-subarray-with-zero-sum)
- [Question 25: Count Subarrays with Given XOR K](#question-25-count-subarrays-with-given-xor-k)
- [Question 26: Merge Overlapping Sub-intervals](#question-26-merge-overlapping-sub-intervals)
- [Question 27: Count Reverse Pairs](#question-27-count-reverse-pairs)
- [Question 28: Count Inversions in an Array](#question-28-count-inversions-in-an-array)
- [Question 29: Maximum Product Subarray](#question-29-maximum-product-subarray)
- [Question 30: Find the Repeating and Missing Numbers](#question-30-find-the-repeating-and-missing-numbers)
- [Question 31: Merge Two Sorted Arrays Without Extra Space](#question-31-merge-two-sorted-arrays-without-extra-space)

---



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

---

### Question 6: Union of Two Sorted Arrays
**Link:** [Striver Link](https://takeuforward.org/data-structure/union-of-two-sorted-arrays/)

**Example:**
```
Input: arr1[] = {1, 2, 3, 4, 5}, arr2[] = {2, 3, 4, 4, 5}
Output: {1, 2, 3, 4, 5} (union without duplicates)

Input: arr1[] = {1, 1, 2, 3}, arr2[] = {2, 3, 4}
Output: {1, 2, 3, 4} (union without duplicates)
```

**Intuition:**
We need to find the union of two sorted arrays, which means combining all unique elements from both arrays. Since arrays are sorted, we can use two-pointer approach or merge approach.

**Brute Force:**
Use set to store all elements and convert back to vector

```cpp
class Solution {
public:
    vector<int> findUnion(int arr1[], int arr2[], int n, int m) {
        set<int> unionSet;
        
        // Add elements from first array
        for(int i = 0; i < n; i++) {
            unionSet.insert(arr1[i]);
        }
        
        // Add elements from second array
        for(int i = 0; i < m; i++) {
            unionSet.insert(arr2[i]);
        }
        
        // Convert set to vector
        vector<int> result(unionSet.begin(), unionSet.end());
        return result;
    }
};
```

**Better Solution:**
Merge approach using two pointers (since arrays are sorted)

```cpp
class Solution {
public:
    vector<int> findUnion(int arr1[], int arr2[], int n, int m) {
        vector<int> result;
        int i = 0, j = 0;
        
        while(i < n && j < m) {
            if(arr1[i] < arr2[j]) {
                if(result.empty() || result.back() != arr1[i]) {
                    result.push_back(arr1[i]);
                }
                i++;
            } else if(arr2[j] < arr1[i]) {
                if(result.empty() || result.back() != arr2[j]) {
                    result.push_back(arr2[j]);
                }
                j++;
            } else {
                if(result.empty() || result.back() != arr1[i]) {
                    result.push_back(arr1[i]);
                }
                i++;
                j++;
            }
        }
        
        // Add remaining elements from arr1
        while(i < n) {
            if(result.empty() || result.back() != arr1[i]) {
                result.push_back(arr1[i]);
            }
            i++;
        }
        
        // Add remaining elements from arr2
        while(j < m) {
            if(result.empty() || result.back() != arr2[j]) {
                result.push_back(arr2[j]);
            }
            j++;
        }
        
        return result;
    }
};
```

**Optimal Solution:**
Two-pointer merge approach with duplicate handling

```cpp
class Solution {
public:
    vector<int> findUnion(int arr1[], int arr2[], int n, int m) {
        vector<int> result;
        int i = 0, j = 0;
        
        while(i < n && j < m) {
            if(arr1[i] <= arr2[j]) {
                if(result.empty() || result.back() != arr1[i]) {
                    result.push_back(arr1[i]);
                }
                i++;
            } else {
                if(result.empty() || result.back() != arr2[j]) {
                    result.push_back(arr2[j]);
                }
                j++;
            }
        }
        
        // Add remaining elements from arr1
        while(i < n) {
            if(result.empty() || result.back() != arr1[i]) {
                result.push_back(arr1[i]);
            }
            i++;
        }
        
        // Add remaining elements from arr2
        while(j < m) {
            if(result.empty() || result.back() != arr2[j]) {
                result.push_back(arr2[j]);
            }
            j++;
        }
        
        return result;
    }
};
```

**Edge Cases:**
- One or both arrays are empty
- Arrays with all same elements
- Arrays with no common elements
- Arrays with all elements same
- Arrays with different sizes

**Important Notes:**
- Time Complexity: Brute - O((n+m) log(n+m)), Better/Optimal - O(n+m)
- Space Complexity: Brute - O(n+m), Better/Optimal - O(n+m) for result
- Optimal solution leverages sorted nature of arrays
- Always check for duplicates before adding to result
- Can also use unordered_set for better average case performance

---

### Question 7: Find the Missing Number in an Array
**Link:** [Striver Link](https://takeuforward.org/arrays/find-the-missing-number-in-an-array/)

**Example:**
```
Input: arr[] = {3, 0, 1}
Output: 2 (missing number between 0 and 3)

Input: arr[] = {0, 1}
Output: 2 (missing number between 0 and 2)

Input: arr[] = {9, 6, 4, 2, 3, 5, 7, 0, 1}
Output: 8 (missing number between 0 and 9)
```

**Intuition:**
We need to find the missing number in an array containing numbers from 0 to n (where n is array length). We can use sum formula, XOR approach, or sorting approach.

**Brute Force:**
Sort the array and find the first missing number

```cpp
class Solution {
public:
    int missingNumber(vector<int>& arr) {
        sort(arr.begin(), arr.end());
        int n = arr.size();
        
        for(int i = 0; i < n; i++) {
            if(arr[i] != i) {
                return i;
            }
        }
        return n; // If all numbers are present, return n
    }
};
```

**Better Solution:**
Use sum formula - expected sum minus actual sum

```cpp
class Solution {
public:
    int missingNumber(vector<int>& arr) {
        int n = arr.size();
        int expectedSum = (n * (n + 1)) / 2;
        int actualSum = 0;
        
        for(int i = 0; i < n; i++) {
            actualSum += arr[i];
        }
        
        return expectedSum - actualSum;
    }
};
```

**Optimal Solution:**
XOR approach - XOR all numbers from 0 to n with array elements

```cpp
class Solution {
public:
    int missingNumber(vector<int>& arr) {
        int n = arr.size();
        int result = n; // Start with n
        
        for(int i = 0; i < n; i++) {
            result ^= i ^ arr[i];
        }
        
        return result;
    }
};
```

**Edge Cases:**
- Array with single element
- Array with all numbers present (missing is n)
- Array with first number missing (0)
- Array with last number missing (n-1)
- Empty array

**Important Notes:**
- Time Complexity: Brute - O(n log n), Better - O(n), Optimal - O(n)
- Space Complexity: All approaches - O(1)
- Sum formula approach is simple and efficient
- XOR approach handles integer overflow better than sum
- Can also use hash set approach for O(n) time and space

---

### Question 8: Count Maximum Consecutive Ones in the Array
**Link:** [Striver Link](https://takeuforward.org/data-structure/count-maximum-consecutive-ones-in-the-array/)

**Example:**
```
Input: arr[] = {1, 1, 0, 1, 1, 1}
Output: 3 (maximum consecutive ones)

Input: arr[] = {1, 0, 1, 1, 0, 1}
Output: 2 (maximum consecutive ones)

Input: arr[] = {0, 0, 0, 0}
Output: 0 (no ones present)
```

**Intuition:**
We need to find the maximum count of consecutive 1s in a binary array. We can iterate through the array and keep track of current consecutive count and maximum count seen so far.

**Brute Force:**
Check all possible subarrays and count consecutive ones

```cpp
class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& arr) {
        int n = arr.size();
        int maxCount = 0;
        
        for(int i = 0; i < n; i++) {
            if(arr[i] == 1) {
                int count = 0;
                int j = i;
                while(j < n && arr[j] == 1) {
                    count++;
                    j++;
                }
                maxCount = max(maxCount, count);
                i = j - 1; // Skip the ones we already counted
            }
        }
        
        return maxCount;
    }
};
```

**Optimal Solution:**
Single pass with counter variables

```cpp
class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& arr) {
        int n = arr.size();
        int maxCount = 0;
        int currentCount = 0;
        
        for(int i = 0; i < n; i++) {
            if(arr[i] == 1) {
                currentCount++;
                maxCount = max(maxCount, currentCount);
            } else {
                currentCount = 0;
            }
        }
        
        return maxCount;
    }
};
```

**Edge Cases:**
- Array with all zeros
- Array with all ones
- Array with single element
- Array with alternating zeros and ones
- Empty array

**Important Notes:**
- Time Complexity: Brute - O(n²), Optimal - O(n)
- Space Complexity: All approaches - O(1)
- Optimal solution uses single pass with two counters
- Reset currentCount to 0 when encountering 0
- Update maxCount whenever currentCount increases

---

### Question 9: Find the Number that Appears Once and the Other Numbers Twice
**Link:** [Striver Link](https://takeuforward.org/arrays/find-the-number-that-appears-once-and-the-other-numbers-twice/)

**Example:**
```
Input: arr[] = {4, 1, 2, 1, 2}
Output: 4 (appears once, others appear twice)

Input: arr[] = {2, 2, 1}
Output: 1 (appears once, others appear twice)

Input: arr[] = {1}
Output: 1 (single element)
```

**Intuition:**
We need to find the element that appears only once in an array where all other elements appear exactly twice. We can use XOR operation since XOR of a number with itself gives 0, and XOR with 0 gives the number itself.

**Brute Force:**
Use nested loops to count frequency of each element

```cpp
class Solution {
public:
    int singleNumber(vector<int>& arr) {
        int n = arr.size();
        
        for(int i = 0; i < n; i++) {
            int count = 0;
            for(int j = 0; j < n; j++) {
                if(arr[i] == arr[j]) {
                    count++;
                }
            }
            if(count == 1) {
                return arr[i];
            }
        }
        
        return -1; // Should not reach here
    }
};
```

**Better Solution:**
Use hash map to count frequency

```cpp
class Solution {
public:
    int singleNumber(vector<int>& arr) {
        int n = arr.size();
        unordered_map<int, int> freq;
        
        for(int i = 0; i < n; i++) {
            freq[arr[i]]++;
        }
        
        for(auto it : freq) {
            if(it.second == 1) {
                return it.first;
            }
        }
        
        return -1;
    }
};
```

**Optimal Solution:**
XOR approach - XOR all elements

```cpp
class Solution {
public:
    int singleNumber(vector<int>& arr) {
        int n = arr.size();
        int result = 0;
        
        for(int i = 0; i < n; i++) {
            result ^= arr[i];
        }
        
        return result;
    }
};
```

**Edge Cases:**
- Array with single element
- Array with all elements appearing twice (should not occur)
- Array with negative numbers
- Array with zeros

**Important Notes:**
- Time Complexity: Brute - O(n²), Better - O(n), Optimal - O(n)
- Space Complexity: Brute - O(1), Better - O(n), Optimal - O(1)
- XOR approach is most efficient in both time and space
- XOR properties: a^a = 0, a^0 = a, a^b^a = b
- Works because pairs of same numbers cancel out (become 0)

---

### Question 10: Longest Subarray with Given Sum K
**Link:** [Striver Link](https://takeuforward.org/data-structure/longest-subarray-with-given-sum-k/)

**Example:**
```
Input: arr[] = {1, 2, 3, 1, 1, 1, 1}, K = 3
Output: 3 (subarray {1, 1, 1} has sum 3)

Input: arr[] = {2, 3, 5, 1, 9}, K = 10
Output: 3 (subarray {2, 3, 5} has sum 10)

Input: arr[] = {1, 4, 20, 3, 10, 5}, K = 33
Output: 3 (subarray {20, 3, 10} has sum 33)
```

**Intuition:**
We need to find the longest subarray whose sum equals K. For positive-only arrays, we can use sliding window. For arrays with negative numbers, we need to use prefix sum with hash map.

**Case 1: Only Positive Numbers (Sliding Window)**

```cpp
class Solution {
public:
    int lenOfLongSubarr(vector<int>& arr, int K) {
        int n = arr.size();
        int left = 0, right = 0;
        int sum = 0;
        int maxLen = 0;
        
        while(right < n) {
            sum += arr[right];
            
            while(sum > K && left <= right) {
                sum -= arr[left];
                left++;
            }
            
            if(sum == K) {
                maxLen = max(maxLen, right - left + 1);
            }
            
            right++;
        }
        
        return maxLen;
    }
};
```

**Case 2: Positive + Negative Numbers (Prefix Sum + Hash Map)**

```cpp
class Solution {
public:
    int lenOfLongSubarr(vector<int>& arr, int K) {
        int n = arr.size();
        unordered_map<int, int> prefixSum;
        int sum = 0;
        int maxLen = 0;
        
        for(int i = 0; i < n; i++) {
            sum += arr[i];
            
            if(sum == K) {
                maxLen = max(maxLen, i + 1);
            }
            
            if(prefixSum.find(sum - K) != prefixSum.end()) {
                maxLen = max(maxLen, i - prefixSum[sum - K]);
            }
            
            if(prefixSum.find(sum) == prefixSum.end()) {
                prefixSum[sum] = i;
            }
        }
        
        return maxLen;
    }
};
```

**Edge Cases:**
- Array with single element
- Array with all zeros
- Array with target sum K = 0
- Array with no valid subarray
- Empty array

**Important Notes:**
- **Positive-only arrays**: Use sliding window approach
  - Time Complexity: O(n), Space Complexity: O(1)
  - Shrink window when sum > K
  - Update maxLen when sum == K
  
- **Arrays with negative numbers**: Use prefix sum + hash map
  - Time Complexity: O(n), Space Complexity: O(n)
  - Store prefix sums in hash map
  - Look for (sum - K) in hash map
  - Only store first occurrence of each prefix sum
  
- Sliding window works for positive numbers because sum increases monotonically
- Hash map approach handles negative numbers by tracking all possible prefix sums

**Why Two Different Approaches:**
1. **Sliding Window**: Works only for positive numbers because sum increases monotonically
2. **Hash Map**: Works for all cases (positive, negative, zero) by tracking all prefix sums
3. **Key Difference**: With negative numbers, sum can decrease, making sliding window ineffective

---

### Question 11: Two Sum - Check if a Pair with Given Sum Exists in Array
**Link:** [Striver Link](https://takeuforward.org/data-structure/two-sum-check-if-a-pair-with-given-sum-exists-in-array/)

**Example:**
```
Input: arr[] = {2, 6, 5, 8, 11}, target = 14
Output: true (6 + 8 = 14)

Input: arr[] = {2, 6, 5, 8, 11}, target = 15
Output: false (no pair sums to 15)

Input: arr[] = {1, 4, 45, 6, 10, 8}, target = 16
Output: true (6 + 10 = 16)
```

**Intuition:**
We need to find if there exists a pair of elements in the array that sum up to the target value. We can use brute force, sorting + two pointers, or hash map approach.

**Brute Force:**
Check all possible pairs using nested loops

```cpp
class Solution {
public:
    bool twoSum(vector<int>& arr, int target) {
        int n = arr.size();
        
        for(int i = 0; i < n; i++) {
            for(int j = i + 1; j < n; j++) {
                if(arr[i] + arr[j] == target) {
                    return true;
                }
            }
        }
        
        return false;
    }
};
```

**Better Solution:**
Sort array and use two pointers

```cpp
class Solution {
public:
    bool twoSum(vector<int>& arr, int target) {
        int n = arr.size();
        vector<int> temp = arr;
        sort(temp.begin(), temp.end());
        
        int left = 0, right = n - 1;
        
        while(left < right) {
            int sum = temp[left] + temp[right];
            
            if(sum == target) {
                return true;
            } else if(sum < target) {
                left++;
            } else {
                right--;
            }
        }
        
        return false;
    }
};
```

**Optimal Solution:**
Hash map approach

```cpp
class Solution {
public:
    bool twoSum(vector<int>& arr, int target) {
        int n = arr.size();
        unordered_set<int> seen;
        
        for(int i = 0; i < n; i++) {
            int complement = target - arr[i];
            
            if(seen.find(complement) != seen.end()) {
                return true;
            }
            
            seen.insert(arr[i]);
        }
        
        return false;
    }
};
```

**Edge Cases:**
- Array with single element
- Array with duplicate elements
- Target sum equal to twice an element
- Array with negative numbers
- Empty array

**Important Notes:**
- Time Complexity: Brute - O(n²), Better - O(n log n), Optimal - O(n)
- Space Complexity: Brute - O(1), Better - O(n), Optimal - O(n)
- Hash map approach is most efficient for time complexity
- Two pointers approach requires sorting but uses O(1) extra space
- Hash map stores elements as we iterate, checking for complement
- Can also return indices of the pair if needed by storing index in hash map

---

### Question 12: Sort an Array of 0s, 1s and 2s
**Link:** [Striver Link](https://takeuforward.org/data-structure/sort-an-array-of-0s-1s-and-2s/)

**Example:**
```
Input: arr[] = {0, 1, 2, 0, 1, 2}
Output: {0, 0, 1, 1, 2, 2}

Input: arr[] = {0, 1, 1, 0, 1, 2, 1, 2, 0, 0, 0, 1}
Output: {0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 2, 2}

Input: arr[] = {2, 2, 2, 1, 1, 1, 0, 0, 0}
Output: {0, 0, 0, 1, 1, 1, 2, 2, 2}
```

**Intuition:**
We need to sort an array containing only 0s, 1s, and 2s. We can use counting sort, or the Dutch National Flag algorithm (three pointers) for in-place sorting.

**Brute Force:**
Use any sorting algorithm (e.g., sort function)

```cpp
class Solution {
public:
    void sortColors(vector<int>& arr) {
        sort(arr.begin(), arr.end());
    }
};
```

**Better Solution:**
Counting sort - count frequencies and reconstruct

```cpp
class Solution {
public:
    void sortColors(vector<int>& arr) {
        int n = arr.size();
        int count0 = 0, count1 = 0, count2 = 0;
        
        // Count frequencies
        for(int i = 0; i < n; i++) {
            if(arr[i] == 0) count0++;
            else if(arr[i] == 1) count1++;
            else count2++;
        }
        
        // Reconstruct array
        int index = 0;
        while(count0--) arr[index++] = 0;
        while(count1--) arr[index++] = 1;
        while(count2--) arr[index++] = 2;
    }
};
```

**Optimal Solution:**
Dutch National Flag Algorithm (three pointers)

```cpp
class Solution {
public:
    void sortColors(vector<int>& arr) {
        int n = arr.size();
        int low = 0, mid = 0, high = n - 1;
        
        while(mid <= high) {
            if(arr[mid] == 0) {
                swap(arr[low], arr[mid]);
                low++;
                mid++;
            } else if(arr[mid] == 1) {
                mid++;
            } else { // arr[mid] == 2
                swap(arr[mid], arr[high]);
                high--;
            }
        }
    }
};
```

**Edge Cases:**
- Array with single element
- Array with all same elements
- Array with only two types of elements
- Empty array
- Array with only 0s or only 1s or only 2s

**Important Notes:**
- Time Complexity: Brute - O(n log n), Better - O(n), Optimal - O(n)
- Space Complexity: Brute - O(1), Better - O(1), Optimal - O(1)
- Dutch National Flag algorithm is most efficient and in-place
- Three pointers: low (0s), mid (1s), high (2s)
- Mid pointer moves through array, low and high pointers mark boundaries
- Counting sort is simple but requires two passes
- Can also use Lomuto partition or Hoare partition variations

**Algorithm / Intuition:**
This problem is a variation of the popular Dutch National Flag algorithm. 

This algorithm contains 3 pointers i.e. low, mid, and high, and 3 main rules. The rules are the following:

- arr[0….low-1] contains 0. [Extreme left part]
- arr[low….mid-1] contains 1.
- arr[high+1….n-1] contains 2. [Extreme right part], n = size of the array

The middle part i.e. arr[mid….high] is the unsorted segment. So, hypothetically the array with different markers will look like the following:

```
[0, 0, 0, 0, 1, 1, 1, 1, 2, 2, 2, 2]
 l-1  l           m-1  m     h  h+1
```

In our case, we can assume that the entire given array is unsorted and so we will place the pointers accordingly. For example, if the given array is: [2,0,2,1,1,0], the array with the 3 pointers will look like the following:

```
[2, 0, 2, 1, 1, 0]
 l  m           h
```

Here, as the entire array is unsorted, we have placed the mid pointer in the first index and the high pointer in the last index. The low is also pointing to the first index as we have no other index before 0. Here, we are mostly interested in placing the 'mid' pointer and the 'high' pointer as they represent the unsorted part in the hypothetical array.

Now, let's understand how the pointers will work to make the array sorted.

**Approach:**
Note: Here in this tutorial we will work based on the value of the mid pointer.

The steps will be the following:

1. First, we will run a loop that will continue until mid <= high.
2. There can be three different values of mid pointer i.e. arr[mid]
   - If arr[mid] == 0, we will swap arr[low] and arr[mid] and will increment both low and mid. Now the subarray from index 0 to (low-1) only contains 0.
   - If arr[mid] == 1, we will just increment the mid pointer and then the index (mid-1) will point to 1 as it should according to the rules.
   - If arr[mid] == 2, we will swap arr[mid] and arr[high] and will decrement high. Now the subarray from index high+1 to (n-1) only contains 2.
3. In this step, we will do nothing to the mid-pointer as even after swapping, the subarray from mid to high(after decrementing high) might be unsorted. So, we will check the value of mid again in the next iteration.
4. Finally, our array should be sorted.

**Dry Run:**
Assume the given array is [2,0,2,1,1,0]. The algorithm will be the following:

```
Initial: [2, 0, 2, 1, 1, 0]
         l  m           h

Step 1: [0, 0, 2, 1, 1, 2]  (arr[mid] == 0, swap with low, l++, m++)
           l  m         h

Step 2: [0, 0, 2, 1, 1, 2]  (arr[mid] == 0, swap with low, l++, m++)
             l  m       h

Step 3: [0, 0, 1, 1, 2, 2]  (arr[mid] == 2, swap with high, h--)
             l  m     h

Step 4: [0, 0, 1, 1, 2, 2]  (arr[mid] == 1, m++)
             l        m  h

Final:   [0, 0, 1, 1, 2, 2]  (arr[mid] == 1, m++)
             l        m  h
```

In each iteration, if we check, the rules are always valid. This is how the algorithm works.

**Key Insights:**
1. **Three Regions**: The algorithm maintains three regions: 0s (left), 1s (middle), 2s (right)
2. **Mid Pointer**: The mid pointer traverses the unsorted region
3. **Swapping Strategy**: 
   - 0 goes to left region (swap with low, increment both)
   - 1 stays in middle region (just increment mid)
   - 2 goes to right region (swap with high, decrement high)
4. **Invariant**: After each iteration, the three regions maintain their properties

---

### Question 13: Find the Majority Element that Occurs More than N/2 Times
**Link:** [Striver Link](https://takeuforward.org/data-structure/find-the-majority-element-that-occurs-more-than-n-2-times/)

**Example:**
```
Input: arr[] = {2, 2, 1, 1, 1, 2, 2}
Output: 2 (occurs 4 times, n/2 = 3.5)

Input: arr[] = {3, 2, 3}
Output: 3 (occurs 2 times, n/2 = 1.5)

Input: arr[] = {1, 1, 1, 1, 2, 2, 2}
Output: 1 (occurs 4 times, n/2 = 3.5)
```

**Intuition:**
We need to find the element that appears more than n/2 times in the array. We can use counting approach, sorting, or Boyer-Moore Voting Algorithm for optimal solution.

**Brute Force:**
Count frequency of each element using nested loops

```cpp
class Solution {
public:
    int majorityElement(vector<int>& arr) {
        int n = arr.size();
        
        for(int i = 0; i < n; i++) {
            int count = 0;
            for(int j = 0; j < n; j++) {
                if(arr[i] == arr[j]) {
                    count++;
                }
            }
            if(count > n/2) {
                return arr[i];
            }
        }
        
        return -1;
    }
};
```

**Better Solution:**
Use hash map to count frequencies

```cpp
class Solution {
public:
    int majorityElement(vector<int>& arr) {
        int n = arr.size();
        unordered_map<int, int> freq;
        
        for(int i = 0; i < n; i++) {
            freq[arr[i]]++;
            if(freq[arr[i]] > n/2) {
                return arr[i];
            }
        }
        
        return -1;
    }
};
```

**Optimal Solution:**
Boyer-Moore Voting Algorithm

```cpp
class Solution {
public:
    int majorityElement(vector<int>& arr) {
        int n = arr.size();
        int count = 0;
        int candidate = 0;
        
        // Find candidate
        for(int i = 0; i < n; i++) {
            if(count == 0) {
                candidate = arr[i];
            }
            
            if(arr[i] == candidate) {
                count++;
            } else {
                count--;
            }
        }
        
        // Verify candidate
        count = 0;
        for(int i = 0; i < n; i++) {
            if(arr[i] == candidate) {
                count++;
            }
        }
        
        return count > n/2 ? candidate : -1;
    }
};
```

**Edge Cases:**
- Array with single element
- Array with no majority element
- Array with exactly n/2 occurrences
- Array with all same elements
- Empty array

**Important Notes:**
- Time Complexity: Brute - O(n²), Better - O(n), Optimal - O(n)
- Space Complexity: Brute - O(1), Better - O(n), Optimal - O(1)
- Boyer-Moore algorithm works because majority element appears > n/2 times
- First pass finds candidate, second pass verifies it's actually majority
- Hash map approach is simple but requires extra space
- Can also use sorting and check middle element if majority exists

---

### Question 14: Kadane's Algorithm - Maximum Subarray Sum in an Array
**Link:** [Striver Link](https://takeuforward.org/data-structure/kadanes-algorithm-maximum-subarray-sum-in-an-array/)

**Example:**
```
Input: arr[] = {-2, 1, -3, 4, -1, 2, 1, -5, 4}
Output: 6 (subarray {4, -1, 2, 1} has sum 6)

Input: arr[] = {1, 2, 3, -2, 5}
Output: 9 (subarray {1, 2, 3, -2, 5} has sum 9)

Input: arr[] = {-1, -2, -3, -4}
Output: -1 (single element {-1} has sum -1)
```

**Intuition:**
We need to find the maximum sum of a contiguous subarray. Kadane's algorithm maintains a running sum and resets it to current element when it becomes negative, ensuring we always consider the best possible subarray ending at each position.

**Brute Force:**
Check all possible subarrays and calculate their sums

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& arr) {
        int n = arr.size();
        int maxSum = INT_MIN;
        
        for(int i = 0; i < n; i++) {
            int currentSum = 0;
            for(int j = i; j < n; j++) {
                currentSum += arr[j];
                maxSum = max(maxSum, currentSum);
            }
        }
        
        return maxSum;
    }
};
```

**Optimal Solution:**
Kadane's Algorithm

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& arr) {
        int n = arr.size();
        int maxSum = arr[0];
        int currentSum = arr[0];
        
        for(int i = 1; i < n; i++) {
            // Either extend previous subarray or start new one
            currentSum = max(arr[i], currentSum + arr[i]);
            maxSum = max(maxSum, currentSum);
        }
        
        return maxSum;
    }
};
```

**Alternative Implementation:**
Kadane's with reset approach

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& arr) {
        int n = arr.size();
        int maxSum = INT_MIN;
        int currentSum = 0;
        
        for(int i = 0; i < n; i++) {
            currentSum += arr[i];
            maxSum = max(maxSum, currentSum);
            
            // Reset if current sum becomes negative
            if(currentSum < 0) {
                currentSum = 0;
            }
        }
        
        return maxSum;
    }
};
```

**Edge Cases:**
- Array with single element
- Array with all negative numbers
- Array with all positive numbers
- Array with mix of positive and negative
- Empty array

**Important Notes:**
- Time Complexity: Brute - O(n²), Optimal - O(n)
- Space Complexity: All approaches - O(1)
- Kadane's algorithm works because:
  - If current sum becomes negative, starting fresh from current element is better
  - We maintain maximum sum seen so far
  - Each element is considered as potential start of new subarray
- First implementation is more intuitive
- Second implementation is more explicit about resetting
- Can also track start and end indices of maximum subarray if needed

**Why Kadane's Algorithm Works:**
1. **Local vs Global Maximum**: At each step, we decide whether to extend the current subarray or start a new one
2. **Negative Sum Reset**: If current sum becomes negative, starting fresh from current element gives better result
3. **Optimal Substructure**: The solution to the problem can be constructed from solutions to subproblems
4. **Greedy Choice**: At each step, we make the locally optimal choice (extend or reset)

**Variations:**
1. **Circular Subarray**: Handle cases where subarray can wrap around the array
2. **K Maximum Subarrays**: Find k non-overlapping subarrays with maximum sum
3. **Subarray with Given Sum**: Find subarray with exactly given sum (different from this problem)
4. **Maximum Product Subarray**: Similar concept but with multiplication

---

### Question 15: Stock Buy and Sell
**Link:** [Striver Link](https://takeuforward.org/data-structure/stock-buy-and-sell/)

**Example:**
```
Input: arr[] = {7, 1, 5, 3, 6, 4}
Output: 5 (buy at 1, sell at 6, profit = 6-1 = 5)

Input: arr[] = {7, 6, 4, 3, 1}
Output: 0 (no profit possible, prices keep decreasing)

Input: arr[] = {1, 2, 3, 4, 5}
Output: 4 (buy at 1, sell at 5, profit = 5-1 = 4)
```

**Intuition:**
We need to find the maximum profit by buying and selling a stock once. The key insight is to find the minimum price seen so far and calculate potential profit if we sell at current price.

**Brute Force:**
Check all possible buy-sell pairs

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        int maxProfit = 0;
        
        for(int i = 0; i < n; i++) {
            for(int j = i + 1; j < n; j++) {
                int profit = prices[j] - prices[i];
                maxProfit = max(maxProfit, profit);
            }
        }
        
        return maxProfit;
    }
};
```

**Optimal Solution:**
Single pass with minimum tracking

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        int minPrice = prices[0];
        int maxProfit = 0;
        
        for(int i = 1; i < n; i++) {
            // Update minimum price seen so far
            minPrice = min(minPrice, prices[i]);
            
            // Calculate profit if we sell at current price
            int currentProfit = prices[i] - minPrice;
            maxProfit = max(maxProfit, currentProfit);
        }
        
        return maxProfit;
    }
};
```

**Alternative Approach:**
Using Kadane's algorithm concept

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        int maxProfit = 0;
        int currentProfit = 0;
        
        for(int i = 1; i < n; i++) {
            int diff = prices[i] - prices[i-1];
            currentProfit = max(diff, currentProfit + diff);
            maxProfit = max(maxProfit, currentProfit);
        }
        
        return maxProfit;
    }
};
```

**Edge Cases:**
- Array with single element
- Array with all decreasing prices
- Array with all increasing prices
- Array with equal prices
- Empty array

**Important Notes:**
- Time Complexity: Brute - O(n²), Optimal - O(n)
- Space Complexity: All approaches - O(1)
- Key insight: Buy at minimum price seen so far
- Can only buy and sell once (not multiple transactions)
- If no profit possible, return 0
- First approach is most intuitive and commonly used
- Second approach uses Kadane's concept on price differences
- Can also track buy and sell days if needed

**Why This Approach Works:**
1. **Single Transaction**: Since we can only buy and sell once, we need to find the best buy-sell pair
2. **Minimum Price Tracking**: By keeping track of minimum price seen so far, we ensure we buy at the lowest possible price
3. **Greedy Strategy**: At each step, we calculate potential profit if we sell at current price
4. **Optimal Substructure**: The solution can be built by considering each day as a potential selling day

**Variations:**
1. **Multiple Transactions**: Buy and sell multiple times to maximize profit
2. **With Transaction Fee**: Each transaction has a cost
3. **With Cooldown**: Cannot buy immediately after selling
4. **Best Time to Buy and Sell Stock IV**: At most k transactions allowed

**Interview Tips:**
- Always mention the single transaction constraint first
- Explain why tracking minimum price is optimal
- Discuss the greedy nature of the algorithm
- Be ready to handle edge cases like decreasing prices

---

### Question 16: Next Permutation - Find Next Lexicographically Greater Permutation
**Link:** [Striver Link](https://takeuforward.org/data-structure/next_permutation-find-next-lexicographically-greater-permutation/)

**Example:**
```
Input: arr[] = {1, 2, 3}
Output: {1, 3, 2} (next lexicographically greater permutation)

Input: arr[] = {3, 2, 1}
Output: {1, 2, 3} (back to first permutation, no greater exists)

Input: arr[] = {1, 1, 5}
Output: {1, 5, 1} (next lexicographically greater permutation)
```

**Intuition:**
We need to find the next lexicographically greater permutation. The algorithm involves finding the first decreasing element from right, swapping it with the next greater element, and reversing the suffix.

**Brute Force:**
Generate all permutations and find the next one

```cpp
class Solution {
public:
    void nextPermutation(vector<int>& nums) {
        // Generate all permutations and find next
        // This is not practical for large arrays
        // Time complexity: O(n! * n)
    }
};
```

**Optimal Solution:**
Three-step algorithm

```cpp
class Solution {
public:
    void nextPermutation(vector<int>& nums) {
        int i = nums.size() - 2;
        
        // Step 1: Find first decreasing element from right
        while(i >= 0 && nums[i] >= nums[i + 1]) {
            i--;
        }
        
        if(i >= 0) {
            int j = nums.size() - 1;
            
            // Step 2: Find element just greater than nums[i]
            while(nums[j] <= nums[i]) {
                j--;
            }
            
            // Swap the two elements
            swap(nums[j], nums[i]);
        }
        
        // Step 3: Reverse the suffix (elements after position i)
        reverse(nums.begin() + i + 1, nums.end());
    }
};
```

**Alternative Implementation:**
More explicit version

```cpp
class Solution {
public:
    void nextPermutation(vector<int>& nums) {
        int n = nums.size();
        
        // Find the first decreasing element from right
        int breakPoint = -1;
        for(int i = n - 2; i >= 0; i--) {
            if(nums[i] < nums[i + 1]) {
                breakPoint = i;
                break;
            }
        }
        
        // If no break point found, reverse entire array
        if(breakPoint == -1) {
            reverse(nums.begin(), nums.end());
            return;
        }
        
        // Find element just greater than nums[breakPoint]
        for(int i = n - 1; i > breakPoint; i--) {
            if(nums[i] > nums[breakPoint]) {
                swap(nums[i], nums[breakPoint]);
                break;
            }
        }
        
        // Reverse the suffix
        reverse(nums.begin() + breakPoint + 1, nums.end());
    }
};
```

**Edge Cases:**
- Array with single element
- Array with all same elements
- Array in descending order (last permutation)
- Array in ascending order
- Empty array

**Important Notes:**
- Time Complexity: O(n)
- Space Complexity: O(1)
- Algorithm works in three steps:
  1. Find first decreasing element from right (break point)
  2. Swap with next greater element
  3. Reverse the suffix after break point
- If no break point found, array is in descending order
- Reverse entire array to get first permutation
- Can also implement previous permutation by reversing the logic
- Works for any array with distinct or duplicate elements

**Why This Algorithm Works:**
1. **Lexicographic Order**: The algorithm finds the next permutation in lexicographic order
2. **Break Point**: The first decreasing element from right is the point where we can make a change
3. **Next Greater Element**: We swap with the smallest element greater than the break point
4. **Suffix Reversal**: Reversing the suffix ensures we get the smallest possible arrangement

**Key Insights:**
1. **Monotonicity**: From right to left, elements are in descending order until the break point
2. **Optimal Swap**: We swap with the smallest element that's greater than the break point
3. **Suffix Property**: After the break point, all elements are in descending order
4. **Minimal Change**: This approach ensures we get the next permutation with minimal change

**Variations:**
1. **Previous Permutation**: Find the previous lexicographically smaller permutation
2. **Kth Permutation**: Find the kth permutation in lexicographic order
3. **Permutation with Repetition**: Handle arrays with duplicate elements
4. **Circular Permutations**: Handle circular arrangements

---

### Question 17: Longest Consecutive Sequence in an Array
**Link:** [Striver Link](https://takeuforward.org/data-structure/longest-consecutive-sequence-in-an-array/)

**Example:**
```
Input: arr[] = {100, 4, 200, 1, 3, 2}
Output: 4 (longest consecutive sequence: {1, 2, 3, 4})

Input: arr[] = {0, 3, 7, 2, 5, 8, 4, 6, 0, 1}
Output: 9 (longest consecutive sequence: {0, 1, 2, 3, 4, 5, 6, 7, 8})

Input: arr[] = {1, 2, 0, 1}
Output: 3 (longest consecutive sequence: {0, 1, 2})
```

**Intuition:**
We need to find the longest sequence of consecutive numbers in the array. The key insight is to use a hash set to check if consecutive elements exist, and only start counting from the smallest element of each sequence.

**Brute Force:**
Check all possible sequences starting from each element

```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& arr) {
        int n = arr.size();
        int maxLength = 0;
        
        for(int i = 0; i < n; i++) {
            int currentNum = arr[i];
            int currentLength = 1;
            
            // Check forward sequence
            while(find(arr.begin(), arr.end(), currentNum + 1) != arr.end()) {
                currentNum++;
                currentLength++;
            }
            
            maxLength = max(maxLength, currentLength);
        }
        
        return maxLength;
    }
};
```

**Better Solution:**
Sort and find consecutive sequences

```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& arr) {
        if(arr.empty()) return 0;
        
        sort(arr.begin(), arr.end());
        int n = arr.size();
        int maxLength = 1;
        int currentLength = 1;
        
        for(int i = 1; i < n; i++) {
            if(arr[i] == arr[i-1] + 1) {
                currentLength++;
            } else if(arr[i] != arr[i-1]) {
                currentLength = 1;
            }
            maxLength = max(maxLength, currentLength);
        }
        
        return maxLength;
    }
};
```

**Optimal Solution:**
Hash set approach

```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& arr) {
        int n = arr.size();
        if(n == 0) return 0;
        
        unordered_set<int> numSet(arr.begin(), arr.end());
        int maxLength = 0;
        
        for(int num : numSet) {
            // Only start counting if this is the start of a sequence
            if(numSet.find(num - 1) == numSet.end()) {
                int currentNum = num;
                int currentLength = 1;
                
                // Count consecutive elements forward
                while(numSet.find(currentNum + 1) != numSet.end()) {
                    currentNum++;
                    currentLength++;
                }
                
                maxLength = max(maxLength, currentLength);
            }
        }
        
        return maxLength;
    }
};
```

**Edge Cases:**
- Array with single element
- Array with all same elements
- Array with no consecutive elements
- Array with negative numbers
- Empty array
- Array with duplicates

**Important Notes:**
- Time Complexity: Brute - O(n³), Better - O(n log n), Optimal - O(n)
- Space Complexity: Brute - O(1), Better - O(1), Optimal - O(n)
- Key insight: Only start counting from smallest element of each sequence
- Hash set approach avoids checking sequences multiple times
- Sorting approach is simpler but less efficient
- Duplicate elements don't affect the result
- Can handle negative numbers and large ranges
- Each element is processed at most twice in optimal solution

**Why Hash Set Approach is Optimal:**
1. **Avoids Redundant Work**: We only start counting from the smallest element of each sequence
2. **Efficient Lookup**: Hash set provides O(1) average time complexity for membership testing
3. **Single Pass**: Each element is processed at most twice (once for checking if it's start, once for counting)
4. **Handles Duplicates**: Duplicate elements don't affect the result

**Key Insights:**
1. **Sequence Start**: A number is the start of a sequence only if (num-1) is not in the set
2. **Sequence Length**: Once we find a start, we count consecutive elements forward
3. **No Overlapping**: Each sequence is counted only once from its start
4. **Optimal Processing**: Each element is considered as potential sequence start at most once

**Variations:**
1. **Longest Consecutive Subsequence**: Find longest consecutive subsequence (elements need not be adjacent)
2. **Consecutive Numbers with Sum K**: Find consecutive numbers that sum to K
3. **Longest Arithmetic Subsequence**: Find longest arithmetic progression
4. **Consecutive Characters**: Find longest consecutive characters in a string

---



### Question 18: Spiral Traversal of Matrix

**Link:** [TakeUForward - Spiral Traversal of Matrix](https://takeuforward.org/data-structure/spiral-traversal-of-matrix/)

**Problem Statement:**
Given a 2D matrix, print all elements in a spiral order.

**Example:**
```
Input: matrix = [
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12]
]
Output: [1, 2, 3, 4, 8, 12, 11, 10, 9, 5, 6, 7]
```

**Intuition:**
We need to traverse the matrix in a spiral pattern: right → down → left → up, while keeping track of boundaries and avoiding revisiting elements.

**Approach 1: Using 4 Pointers (Optimal)**
```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> result;
        if(matrix.empty() || matrix[0].empty()) return result;
        
        int rows = matrix.size();
        int cols = matrix[0].size();
        
        int top = 0, bottom = rows - 1;
        int left = 0, right = cols - 1;
        
        while(top <= bottom && left <= right) {
            // Traverse right
            for(int j = left; j <= right; j++) {
                result.push_back(matrix[top][j]);
            }
            top++;
            
            // Traverse down
            for(int i = top; i <= bottom; i++) {
                result.push_back(matrix[i][right]);
            }
            right--;
            
            // Traverse left (only if top <= bottom)
            if(top <= bottom) {
                for(int j = right; j >= left; j--) {
                    result.push_back(matrix[bottom][j]);
                }
                bottom--;
            }
            
            // Traverse up (only if left <= right)
            if(left <= right) {
                for(int i = bottom; i >= top; i--) {
                    result.push_back(matrix[i][left]);
                }
                left++;
            }
        }
        
        return result;
    }
};
```

**Approach 2: Using Direction Array (Alternative)**
```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> result;
        if(matrix.empty() || matrix[0].empty()) return result;
        
        int rows = matrix.size();
        int cols = matrix[0].size();
        
        // Direction arrays: right, down, left, up
        int dr[] = {0, 1, 0, -1};
        int dc[] = {1, 0, -1, 0};
        
        int r = 0, c = 0;
        int direction = 0;
        int visited = 0;
        int total = rows * cols;
        
        while(visited < total) {
            result.push_back(matrix[r][c]);
            visited++;
            
            int nextR = r + dr[direction];
            int nextC = c + dc[direction];
            
            // Check if next position is valid and not visited
            if(nextR < 0 || nextR >= rows || nextC < 0 || nextC >= cols || 
               matrix[nextR][nextC] == INT_MAX) {
                direction = (direction + 1) % 4;
                nextR = r + dr[direction];
                nextC = c + dc[direction];
            }
            
            r = nextR;
            c = nextC;
        }
        
        return result;
    }
};
```

**Approach 3: Recursive Solution**
```cpp
class Solution {
public:
    void spiralTraversal(vector<vector<int>>& matrix, vector<int>& result, 
                        int startRow, int endRow, int startCol, int endCol) {
        if(startRow > endRow || startCol > endCol) return;
        
        // Traverse right
        for(int j = startCol; j <= endCol; j++) {
            result.push_back(matrix[startRow][j]);
        }
        
        // Traverse down
        for(int i = startRow + 1; i <= endRow; i++) {
            result.push_back(matrix[i][endCol]);
        }
        
        // Traverse left (only if startRow != endRow)
        if(startRow != endRow) {
            for(int j = endCol - 1; j >= startCol; j--) {
                result.push_back(matrix[endRow][j]);
            }
        }
        
        // Traverse up (only if startCol != endCol)
        if(startCol != endCol) {
            for(int i = endRow - 1; i > startRow; i--) {
                result.push_back(matrix[i][startCol]);
            }
        }
        
        // Recursive call for inner matrix
        spiralTraversal(matrix, result, startRow + 1, endRow - 1, 
                       startCol + 1, endCol - 1);
    }
    
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> result;
        if(matrix.empty() || matrix[0].empty()) return result;
        
        int rows = matrix.size();
        int cols = matrix[0].size();
        
        spiralTraversal(matrix, result, 0, rows - 1, 0, cols - 1);
        return result;
    }
};
```

**Edge Cases:**
- Empty matrix
- Single row or single column matrix
- 1x1 matrix
- Matrix with all same elements

**Important Notes:**
- **Time Complexity:** O(m × n) where m is rows and n is columns
- **Space Complexity:** O(1) for Approach 1, O(m × n) for result array
- Approach 1 (4 pointers) is most efficient and commonly used in interviews
- Always check boundaries before traversing to avoid index out of bounds
- The spiral pattern follows: right → down → left → up → repeat

**Variations:**
1. **Spiral Matrix II:** Generate a matrix with numbers 1 to n² in spiral order
2. **Spiral Matrix III:** Start from a specific position and traverse in spiral order
3. **Anti-clockwise spiral:** Change the direction order to: left → up → right → down

**Practice Problems:**
- [LeetCode 54: Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)
- [LeetCode 59: Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/)
- [LeetCode 885: Spiral Matrix III](https://leetcode.com/problems/spiral-matrix-iii/)

---

### Question 19: Count Subarray Sum Equals K

**Link:** [TakeUForward - Count Subarray Sum Equals K](https://takeuforward.org/arrays/count-subarray-sum-equals-k/)

**Problem Statement:**
Given an array of integers and an integer k, return the total number of subarrays whose sum equals to k.

**Example:**
```
Input: nums = [1, 1, 1], k = 2
Output: 2
Explanation: The subarrays [1, 1] and [1, 1] have sum 2.

Input: nums = [1, 2, 3], k = 3
Output: 2
Explanation: The subarrays [1, 2] and [3] have sum 3.
```

**Intuition:**
We need to find all subarrays whose sum equals k. The key insight is that if we have a prefix sum at index i, and we find a prefix sum at index j (where j < i) such that prefixSum[i] - prefixSum[j] = k, then the subarray from j+1 to i has sum k.

**Approach 1: Brute Force (Not Recommended)**
```cpp
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        int count = 0;
        int n = nums.size();
        
        for(int start = 0; start < n; start++) {
            int sum = 0;
            for(int end = start; end < n; end++) {
                sum += nums[end];
                if(sum == k) {
                    count++;
                }
            }
        }
        
        return count;
    }
};
```

**Approach 2: Prefix Sum with Hash Map (Optimal)**
```cpp
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        int count = 0;
        int sum = 0;
        unordered_map<int, int> prefixSum;
        prefixSum[0] = 1; // Base case: empty subarray has sum 0
        
        for(int num : nums) {
            sum += num;
            
            // If (sum - k) exists in map, we found subarrays with sum k
            if(prefixSum.find(sum - k) != prefixSum.end()) {
                count += prefixSum[sum - k];
            }
            
            // Increment the count for current prefix sum
            prefixSum[sum]++;
        }
        
        return count;
    }
};
```

**Approach 3: Sliding Window (Only for Positive Numbers)**
```cpp
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        // This approach only works for arrays with positive numbers
        int count = 0;
        int sum = 0;
        int left = 0;
        
        for(int right = 0; right < nums.size(); right++) {
            sum += nums[right];
            
            while(sum > k && left <= right) {
                sum -= nums[left];
                left++;
            }
            
            if(sum == k) {
                count++;
            }
        }
        
        return count;
    }
};
```

**Key Insights:**
1. **Prefix Sum Concept:** If we have prefix sums, we can find subarray sums in O(1) time
2. **Hash Map Usage:** We store prefix sums and their frequencies to handle negative numbers
3. **Base Case:** We initialize prefixSum[0] = 1 because an empty subarray has sum 0
4. **Formula:** If current prefix sum is S, we look for (S - k) in our map

**Edge Cases:**
- Empty array
- Array with all negative numbers
- Array with all positive numbers
- k = 0 (special case)
- Array with duplicate elements
- Very large values causing overflow

**Important Notes:**
- **Time Complexity:** 
  - Brute Force: O(n²)
  - Hash Map: O(n)
  - Sliding Window: O(n) (only for positive numbers)
- **Space Complexity:** 
  - Brute Force: O(1)
  - Hash Map: O(n) in worst case
  - Sliding Window: O(1)
- Hash Map approach works for all cases (positive, negative, zero)
- Sliding Window only works for positive numbers
- Always consider integer overflow for large sums

**Why Hash Map Approach is Optimal:**
1. **Handles Negative Numbers:** Unlike sliding window, it works with negative values
2. **Single Pass:** Only requires one iteration through the array
3. **Efficient Lookup:** Hash map provides O(1) average time complexity for lookups
4. **Handles Zero:** Correctly counts subarrays with sum k even when k = 0

**Variations:**
1. **Subarray Sum Divisible by K:** Use modulo arithmetic
2. **Longest Subarray with Sum K:** Track indices instead of count
3. **Subarray with Given XOR:** Similar concept but with XOR operation
4. **Subarray with Given Product:** Handle multiplication and division

**Practice Problems:**
- [LeetCode 560: Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)
- [LeetCode 974: Subarray Sums Divisible by K](https://leetcode.com/problems/subarray-sums-divisible-by-k/)
- [LeetCode 325: Maximum Size Subarray Sum Equals k](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/)

**Interview Tips:**
- Always mention the hash map approach first
- Explain why sliding window doesn't work for negative numbers
- Discuss time and space complexity trade-offs
- Be ready to handle edge cases like k = 0
- Consider mentioning the prefix sum concept as it's fundamental

---

### Question 20: Pascal's Triangle

**Link:** [TakeUForward - Program to Generate Pascal's Triangle](https://takeuforward.org/data-structure/program-to-generate-pascals-triangle/)

**Problem Statement:**
Given an integer numRows, return the first numRows of Pascal's triangle.

**Example:**
```
Input: numRows = 5
Output: [
    [1],
    [1, 1],
    [1, 2, 1],
    [1, 3, 3, 1],
    [1, 4, 6, 4, 1]
]
```

**Intuition:**
Pascal's triangle is a triangular array where each number is the sum of the two numbers above it. Each row starts and ends with 1, and the middle numbers are calculated by adding the two numbers above them.

**Approach 1: Using Previous Row (Standard)**
```cpp
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> result;
        
        for(int i = 0; i < numRows; i++) {
            vector<int> row(i + 1, 1); // Initialize with 1s
            
            // Fill middle elements (not first and last)
            for(int j = 1; j < i; j++) {
                row[j] = result[i-1][j-1] + result[i-1][j];
            }
            
            result.push_back(row);
        }
        
        return result;
    }
};
```

**Approach 2: Using Combination Formula (Optimal)**
```cpp
class Solution {
public:
    vector<int> rowGenerate(int n) {
        vector<int> temp;
        long long ans = 1;
        temp.push_back(ans);

        for (int i = 0; i < n; i++) {
            ans = ans * (n - i);
            ans = ans / (i + 1);
            temp.push_back(ans);
        }

        return temp;
    }
    
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> ans;
        for (int i = 0; i < numRows; i++) {
            ans.push_back(rowGenerate(i));
        }
        return ans;
    }
};
```

**Approach 3: Using Dynamic Programming (Alternative)**
```cpp
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> result;
        
        if(numRows == 0) return result;
        
        // First row
        result.push_back({1});
        
        for(int i = 1; i < numRows; i++) {
            vector<int> row;
            row.push_back(1); // First element
            
            // Middle elements
            for(int j = 1; j < i; j++) {
                row.push_back(result[i-1][j-1] + result[i-1][j]);
            }
            
            row.push_back(1); // Last element
            result.push_back(row);
        }
        
        return result;
    }
};
```

**Key Insights:**
1. **Mathematical Pattern:** Each element is the sum of two elements from the previous row
2. **Combination Formula:** The nth element in the rth row is C(r, n) = r!/(n!(r-n)!)
3. **Boundary Elements:** First and last elements of each row are always 1
4. **Row Length:** The ith row has (i+1) elements

**Edge Cases:**
- numRows = 0 (empty result)
- numRows = 1 (single row with [1])
- numRows = 2 (two rows: [1], [1,1])
- Very large numRows (overflow considerations)

**Important Notes:**
- **Time Complexity:** 
  - Approach 1 & 3: O(numRows²)
  - Approach 2: O(numRows²) but more efficient for individual row generation
- **Space Complexity:** O(numRows²) for storing the result
- Approach 2 uses combination formula which is mathematically elegant
- Always handle integer overflow for large values
- Each row is symmetric (except for odd-length rows)

**Why Combination Formula Approach is Optimal:**
1. **Mathematical Efficiency:** Direct calculation without building previous rows
2. **Memory Efficient:** Generates each row independently
3. **Scalable:** Works well for generating specific rows without full triangle
4. **Mathematical Insight:** Demonstrates understanding of binomial coefficients

**Variations:**
1. **Get Specific Row:** Generate only the nth row of Pascal's triangle
2. **Get Specific Element:** Find the element at position (row, col)
3. **Modified Pascal's Triangle:** Custom rules for element calculation
4. **3D Pascal's Triangle:** Extension to higher dimensions

**Practice Problems:**
- [LeetCode 118: Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)
- [LeetCode 119: Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii/)
- [LeetCode 120: Triangle](https://leetcode.com/problems/triangle/)

**Interview Tips:**
- Start with the standard approach (building from previous row)
- Mention the mathematical relationship with combinations
- Discuss time and space complexity trade-offs
- Be ready to handle edge cases like numRows = 0
- Consider mentioning applications in probability and combinatorics

**Mathematical Applications:**
1. **Binomial Coefficients**: Each element represents C(n, r) where n is row number and r is position
2. **Probability**: Used in binomial probability distributions
3. **Combinatorics**: Counts ways to choose r items from n items
4. **Number Theory**: Related to triangular numbers and other sequences

**Implementation Details:**
1. **Integer Overflow**: Use long long for large values to avoid overflow
2. **Row Generation**: Each row can be generated independently using combination formula
3. **Symmetry**: Each row is symmetric (except for odd-length rows)
4. **Base Cases**: First row is always [1], second row is always [1, 1]

---

### Question 21: Majority Elements (n/3) - Find Elements that Appear More than N/3 Times

**Link:** [TakeUForward - Majority Elements (n/3)](https://takeuforward.org/data-structure/majority-elementsn-3-times-find-the-elements-that-appears-more-than-n-3-times-in-the-array/)

**Problem Statement:**
Given an array of size n, find all elements that appear more than ⌊n/3⌋ times.

**Example:**
```
Input: nums = [3,2,3]
Output: [3]

Input: nums = [1,1,1,3,3,2,2,2]
Output: [1,2]
```

**Intuition:**
At most 2 elements can appear more than n/3 times. We can use Boyer-Moore Voting Algorithm with 2 candidates.

**Brute Force Approach:**
Count frequency of each element using hash map

```cpp
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        vector<int> result;
        unordered_map<int, int> count;
        int n = nums.size();
        int threshold = n / 3;
        
        // Count frequency of each element
        for(int num : nums) {
            count[num]++;
        }
        
        // Check which elements appear more than n/3 times
        for(auto& pair : count) {
            if(pair.second > threshold) {
                result.push_back(pair.first);
            }
        }
        
        return result;
    }
};
```

**Optimal Solution:**
Boyer-Moore Voting Algorithm with 2 candidates

```cpp
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        vector<int> result;
        int candidate1 = 0, candidate2 = 0;
        int count1 = 0, count2 = 0;
        
        // First pass: Find 2 candidates
        for(int num : nums) {
            if(num == candidate1) {
                count1++;
            } else if(num == candidate2) {
                count2++;
            } else if(count1 == 0) {
                candidate1 = num;
                count1 = 1;
            } else if(count2 == 0) {
                candidate2 = num;
                count2 = 1;
            } else {
                count1--;
                count2--;
            }
        }
        
        // Second pass: Verify candidates
        count1 = 0, count2 = 0;
        for(int num : nums) {
            if(num == candidate1) count1++;
            else if(num == candidate2) count2++;
        }
        
        int n = nums.size();
        if(count1 > n/3) result.push_back(candidate1);
        if(count2 > n/3) result.push_back(candidate2);
        
        return result;
    }
};
```

**Key Insights:**
1. **Mathematical Limit**: At most 2 elements can appear more than n/3 times
2. **Boyer-Moore Extension**: Extend the voting algorithm to track 2 candidates
3. **Two-Pass Algorithm**: First pass finds candidates, second pass verifies
4. **Counter Management**: Decrement both counters when encountering different element

**Edge Cases:**
- Array with less than 3 elements
- All elements are same
- No majority elements
- Exactly 2 elements appearing n/3 times each

**Important Notes:**
- **Time Complexity**: O(n) - two linear passes
- **Space Complexity**: O(1) - constant extra space
- **Mathematical Proof**: At most 2 elements can have frequency > n/3
- **Verification Step**: Always verify candidates in second pass

**Why Boyer-Moore Voting Algorithm Works:**
1. **Mathematical Guarantee**: Only 2 elements can appear > n/3 times
2. **Counter Logic**: When we see a different element, we decrement both counters
3. **Candidate Replacement**: When a counter reaches 0, we replace that candidate
4. **Verification**: Final pass ensures we only return actual majority elements

**Variations:**
1. **Majority Element (n/2)**: Find element appearing more than n/2 times
2. **Majority Element (n/k)**: Find elements appearing more than n/k times
3. **K Majority Elements**: Find k elements with highest frequencies

**Practice Problems:**
- [LeetCode 229: Majority Element II](https://leetcode.com/problems/majority-element-ii/)
- [LeetCode 169: Majority Element](https://leetcode.com/problems/majority-element/)

**Interview Tips:**
- Start with hash map approach for clarity
- Explain the mathematical limit (at most 2 elements)
- Demonstrate Boyer-Moore voting algorithm step by step
- Always mention the verification step
- Discuss time and space complexity trade-offs

**Algorithm Breakdown:**
1. **First Pass**: Find 2 potential candidates using voting algorithm
2. **Second Pass**: Count actual frequency of candidates
3. **Verification**: Return only candidates with frequency > n/3

**Mathematical Foundation:**
- If an element appears > n/3 times, it must be one of the candidates
- The voting algorithm ensures we don't miss any majority elements
- Verification step eliminates false positives

---

### Question 22: 3-Sum - Find Triplets that Add Up to Zero

**Link:** [TakeUForward - 3-Sum](https://takeuforward.org/data-structure/3-sum-find-triplets-that-add-up-to-a-zero/)

**Problem Statement:**
Given an array of integers, find all unique triplets in the array which gives the sum of zero.

**Example:**
```
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]

Input: nums = []
Output: []
```

**Intuition:**
Use three pointers approach: fix one element and use two pointers to find the remaining two elements that sum to the negative of the fixed element.

**Brute Force Approach:**
Three nested loops to check all possible triplets

```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> result;
        int n = nums.size();
        
        // Sort array to handle duplicates
        sort(nums.begin(), nums.end());
        
        for(int i = 0; i < n-2; i++) {
            // Skip duplicates for i
            if(i > 0 && nums[i] == nums[i-1]) continue;
            
            for(int j = i+1; j < n-1; j++) {
                // Skip duplicates for j
                if(j > i+1 && nums[j] == nums[j-1]) continue;
                
                for(int k = j+1; k < n; k++) {
                    // Skip duplicates for k
                    if(k > j+1 && nums[k] == nums[k-1]) continue;
                    
                    if(nums[i] + nums[j] + nums[k] == 0) {
                        result.push_back({nums[i], nums[j], nums[k]});
                    }
                }
            }
        }
        
        return result;
    }
};
```

**Optimal Solution:**
Two pointers approach with sorting

```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> result;
        int n = nums.size();
        
        if(n < 3) return result;
        
        // Sort array to use two pointers
        sort(nums.begin(), nums.end());
        
        for(int i = 0; i < n-2; i++) {
            // Skip duplicates for i
            if(i > 0 && nums[i] == nums[i-1]) continue;
            
            int left = i + 1;
            int right = n - 1;
            int target = -nums[i];
            
            while(left < right) {
                int sum = nums[left] + nums[right];
                
                if(sum == target) {
                    result.push_back({nums[i], nums[left], nums[right]});
                    
                    // Skip duplicates for left
                    while(left < right && nums[left] == nums[left+1]) left++;
                    // Skip duplicates for right
                    while(left < right && nums[right] == nums[right-1]) right--;
                    
                    left++;
                    right--;
                } else if(sum < target) {
                    left++;
                } else {
                    right--;
                }
            }
        }
        
        return result;
    }
};
```

**Key Insights:**
1. **Sorting**: Essential for two pointers approach and duplicate handling
2. **Duplicate Handling**: Skip duplicates at each level (i, left, right)
3. **Two Pointers**: Use left and right pointers to find pairs efficiently
4. **Target Calculation**: Target = -nums[i] for each fixed element

**Edge Cases:**
- Array with less than 3 elements
- No valid triplets
- All elements are same
- Multiple valid triplets with duplicates

**Important Notes:**
- **Time Complexity**: O(n²) - sorting + two pointers
- **Space Complexity**: O(1) - excluding result space
- **Sorting**: Required for efficient two pointers approach
- **Duplicate Handling**: Critical to avoid duplicate triplets

**Why Two Pointers Approach Works:**
1. **Sorted Array**: Allows efficient pair finding
2. **Target Calculation**: For each nums[i], find pairs that sum to -nums[i]
3. **Duplicate Skipping**: Ensures unique triplets only
4. **Early Termination**: Can stop when left >= right

**Variations:**
1. **3-Sum Closest**: Find triplet with sum closest to target
2. **3-Sum Smaller**: Count triplets with sum less than target
3. **K-Sum**: Generalize to k elements summing to target

**Practice Problems:**
- [LeetCode 15: 3Sum](https://leetcode.com/problems/3sum/)
- [LeetCode 16: 3Sum Closest](https://leetcode.com/problems/3sum-closest/)

**Interview Tips:**
- Start with brute force for clarity
- Explain why sorting is necessary
- Demonstrate two pointers approach step by step
- Emphasize duplicate handling
- Discuss time complexity trade-offs

**Algorithm Breakdown:**
1. **Sort**: Sort array for two pointers approach
2. **Fix Element**: For each unique element nums[i]
3. **Two Pointers**: Use left and right to find pairs
4. **Duplicate Skip**: Skip duplicates at each level
5. **Result Collection**: Add valid triplets to result

**Mathematical Foundation:**
- For each nums[i], we need nums[left] + nums[right] = -nums[i]
- Sorting allows O(n) pair finding instead of O(n²)
- Duplicate handling ensures unique solutions

---

### Question 23: 4-Sum - Find Quads that Add Up to Target Value

**Link:** [TakeUForward - 4-Sum](https://takeuforward.org/data-structure/4-sum-find-quads-that-add-up-to-a-target-value/)

**Problem Statement:**
Given an array of integers and a target value, find all unique quadruplets in the array which gives the sum of target.

**Example:**
```
Input: nums = [1,0,-1,0,-2,2], target = 0
Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]

Input: nums = [2,2,2,2,2], target = 8
Output: [[2,2,2,2]]
```

**Intuition:**
Extend 3-Sum approach: fix two elements and use two pointers to find the remaining two elements.

**Brute Force Approach:**
Four nested loops to check all possible quadruplets

```cpp
class Solution {
public:
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        vector<vector<int>> result;
        int n = nums.size();
        
        if(n < 4) return result;
        
        // Sort array to handle duplicates
        sort(nums.begin(), nums.end());
        
        for(int i = 0; i < n-3; i++) {
            // Skip duplicates for i
            if(i > 0 && nums[i] == nums[i-1]) continue;
            
            for(int j = i+1; j < n-2; j++) {
                // Skip duplicates for j
                if(j > i+1 && nums[j] == nums[j-1]) continue;
                
                for(int k = j+1; k < n-1; k++) {
                    // Skip duplicates for k
                    if(k > j+1 && nums[k] == nums[k-1]) continue;
                    
                    for(int l = k+1; l < n; l++) {
                        // Skip duplicates for l
                        if(l > k+1 && nums[l] == nums[l-1]) continue;
                        
                        if(nums[i] + nums[j] + nums[k] + nums[l] == target) {
                            result.push_back({nums[i], nums[j], nums[k], nums[l]});
                        }
                    }
                }
            }
        }
        
        return result;
    }
};
```

**Optimal Solution:**
Two nested loops + two pointers approach

```cpp
class Solution {
public:
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        vector<vector<int>> result;
        int n = nums.size();
        
        if(n < 4) return result;
        
        // Sort array to use two pointers
        sort(nums.begin(), nums.end());
        
        for(int i = 0; i < n-3; i++) {
            // Skip duplicates for i
            if(i > 0 && nums[i] == nums[i-1]) continue;
            
            for(int j = i+1; j < n-2; j++) {
                // Skip duplicates for j
                if(j > i+1 && nums[j] == nums[j-1]) continue;
                
                int left = j + 1;
                int right = n - 1;
                long long targetSum = (long long)target - nums[i] - nums[j];
                
                while(left < right) {
                    long long sum = (long long)nums[left] + nums[right];
                    
                    if(sum == targetSum) {
                        result.push_back({nums[i], nums[j], nums[left], nums[right]});
                        
                        // Skip duplicates for left
                        while(left < right && nums[left] == nums[left+1]) left++;
                        // Skip duplicates for right
                        while(left < right && nums[right] == nums[right-1]) right--;
                        
                        left++;
                        right--;
                    } else if(sum < targetSum) {
                        left++;
                    } else {
                        right--;
                    }
                }
            }
        }
        
        return result;
    }
};
```

**Key Insights:**
1. **Sorting**: Essential for two pointers approach and duplicate handling
2. **Two Fixed Elements**: Fix i and j, then use two pointers for remaining pair
3. **Overflow Handling**: Use long long to avoid integer overflow
4. **Duplicate Handling**: Skip duplicates at each level (i, j, left, right)

**Edge Cases:**
- Array with less than 4 elements
- No valid quadruplets
- Integer overflow in sum calculations
- Multiple valid quadruplets with duplicates

**Important Notes:**
- **Time Complexity**: O(n³) - two nested loops + two pointers
- **Space Complexity**: O(1) - excluding result space
- **Overflow Prevention**: Use long long for sum calculations
- **Duplicate Handling**: Critical to avoid duplicate quadruplets

**Why Two Pointers Approach Works:**
1. **Sorted Array**: Allows efficient pair finding
2. **Target Calculation**: For each nums[i] and nums[j], find pairs that sum to target - nums[i] - nums[j]
3. **Duplicate Skipping**: Ensures unique quadruplets only
4. **Overflow Handling**: Prevents integer overflow in large arrays

**Variations:**
1. **4-Sum Closest**: Find quadruplet with sum closest to target
2. **K-Sum**: Generalize to k elements summing to target
3. **4-Sum with Constraints**: Additional constraints on elements

**Practice Problems:**
- [LeetCode 18: 4Sum](https://leetcode.com/problems/4sum/)
- [LeetCode 454: 4Sum II](https://leetcode.com/problems/4sum-ii/)

**Interview Tips:**
- Start with brute force for clarity
- Explain the extension from 3-Sum
- Emphasize overflow handling with long long
- Demonstrate two pointers approach step by step
- Discuss time complexity trade-offs

**Algorithm Breakdown:**
1. **Sort**: Sort array for two pointers approach
2. **Fix Two Elements**: For each unique pair (nums[i], nums[j])
3. **Two Pointers**: Use left and right to find remaining pair
4. **Duplicate Skip**: Skip duplicates at each level
5. **Overflow Handling**: Use long long for sum calculations
6. **Result Collection**: Add valid quadruplets to result

**Mathematical Foundation:**
- For each nums[i] and nums[j], we need nums[left] + nums[right] = target - nums[i] - nums[j]
- Sorting allows O(n) pair finding instead of O(n²)
- Duplicate handling ensures unique solutions
- Overflow handling prevents incorrect results

---

### Question 27: Count Reverse Pairs

**Link:** [TakeUForward - Count Reverse Pairs](https://takeuforward.org/data-structure/count-reverse-pairs/)

**Problem Statement:**
Given an array of integers, count the number of reverse pairs. A reverse pair is a pair (i, j) where 0 <= i < j < n and nums[i] > 2 * nums[j].

**Example:**
```
Input: nums = [1,3,2,3,1]
Output: 2
Explanation: The reverse pairs are (1,4) where nums[1] = 3 > 2 * nums[4] = 2, and (3,4) where nums[3] = 3 > 2 * nums[4] = 2.

Input: nums = [2,4,3,5,1]
Output: 3
```

**Intuition:**
Use merge sort approach to count reverse pairs efficiently. During the merge step, count pairs where left element > 2 * right element.

**Brute Force Approach:**
Check all possible pairs

```cpp
class Solution {
public:
    int reversePairs(vector<int>& nums) {
        int count = 0;
        int n = nums.size();
        
        for(int i = 0; i < n; i++) {
            for(int j = i + 1; j < n; j++) {
                if(nums[i] > 2 * (long long)nums[j]) {
                    count++;
                }
            }
        }
        
        return count;
    }
};
```

**Optimal Solution:**
Merge sort with reverse pair counting

```cpp
class Solution {
public:
    int reversePairs(vector<int>& nums) {
        return mergeSort(nums, 0, nums.size() - 1);
    }
    
private:
    int mergeSort(vector<int>& nums, int start, int end) {
        if(start >= end) return 0;
        
        int mid = start + (end - start) / 2;
        int count = mergeSort(nums, start, mid) + mergeSort(nums, mid + 1, end);
        
        // Count reverse pairs
        int j = mid + 1;
        for(int i = start; i <= mid; i++) {
            while(j <= end && nums[i] > 2 * (long long)nums[j]) {
                j++;
            }
            count += j - (mid + 1);
        }
        
        // Merge sorted arrays
        merge(nums, start, mid, end);
        
        return count;
    }
    
    void merge(vector<int>& nums, int start, int mid, int end) {
        vector<int> temp(end - start + 1);
        int i = start, j = mid + 1, k = 0;
        
        while(i <= mid && j <= end) {
            if(nums[i] <= nums[j]) {
                temp[k++] = nums[i++];
            } else {
                temp[k++] = nums[j++];
            }
        }
        
        while(i <= mid) temp[k++] = nums[i++];
        while(j <= end) temp[k++] = nums[j++];
        
        for(int idx = 0; idx < k; idx++) {
            nums[start + idx] = temp[idx];
        }
    }
};
```

**Key Insights:**
1. **Merge Sort**: Use divide and conquer approach
2. **Reverse Pair Counting**: Count during merge step when left > 2 * right
3. **Overflow Handling**: Use long long to prevent integer overflow
4. **Two Pointers**: Use two pointers to count reverse pairs efficiently

**Edge Cases:**
- Array with no reverse pairs
- Array with all same elements
- Large numbers causing overflow
- Single element array

**Important Notes:**
- **Time Complexity**: O(n log n) - merge sort complexity
- **Space Complexity**: O(n) - temporary array for merging
- **Overflow Prevention**: Use long long for multiplication
- **Stable Sort**: Merge sort maintains relative order

**Why Merge Sort Approach Works:**
1. **Divide and Conquer**: Break problem into smaller subproblems
2. **Sorted Subarrays**: After sorting, reverse pair counting becomes efficient
3. **Two Pointers**: Use two pointers to count pairs in O(n) time
4. **Recursive Solution**: Combine results from left and right halves

**Variations:**
1. **Count Inversions**: Count pairs where nums[i] > nums[j]
2. **Count Pairs with Sum K**: Count pairs with given sum
3. **Count Pairs with XOR K**: Count pairs with given XOR

**Practice Problems:**
- [LeetCode 493: Reverse Pairs](https://leetcode.com/problems/reverse-pairs/)
- [LeetCode 315: Count of Smaller Numbers After Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/)

**Interview Tips:**
- Start with brute force for clarity
- Explain merge sort approach step by step
- Emphasize overflow handling with long long
- Demonstrate reverse pair counting during merge
- Discuss time and space complexity trade-offs

**Algorithm Breakdown:**
1. **Divide**: Split array into two halves
2. **Conquer**: Recursively sort and count reverse pairs in each half
3. **Count**: Count reverse pairs between left and right halves
4. **Merge**: Merge sorted halves while maintaining count

**Mathematical Foundation:**
- Reverse pair condition: nums[i] > 2 * nums[j] where i < j
- Merge sort ensures sorted subarrays for efficient counting
- Two pointers approach counts pairs in O(n) time during merge

---

### Question 28: Count Inversions in an Array

**Link:** [TakeUForward - Count Inversions](https://takeuforward.org/data-structure/count-inversions-in-an-array/)

**Problem Statement:**
Given an array of integers, count the number of inversions. An inversion is a pair (i, j) where 0 <= i < j < n and nums[i] > nums[j].

**Example:**
```
Input: arr[] = {3, 1, 2}
Output: 2
Explanation: The inversions are (3,1) and (3,2).

Input: arr[] = {2, 4, 1, 3, 5}
Output: 3
```

**Intuition:**
Use merge sort approach to count inversions efficiently. During the merge step, count pairs where left element > right element.

**Brute Force Approach:**
Check all possible pairs

```cpp
class Solution {
public:
    int countInversions(vector<int>& arr) {
        int count = 0;
        int n = arr.size();
        
        for(int i = 0; i < n; i++) {
            for(int j = i + 1; j < n; j++) {
                if(arr[i] > arr[j]) {
                    count++;
                }
            }
        }
        
        return count;
    }
};
```

**Optimal Solution:**
Merge sort with inversion counting

```cpp
class Solution {
public:
    int countInversions(vector<int>& arr) {
        return mergeSort(arr, 0, arr.size() - 1);
    }
    
private:
    int mergeSort(vector<int>& arr, int start, int end) {
        if(start >= end) return 0;
        
        int mid = start + (end - start) / 2;
        int count = mergeSort(arr, start, mid) + mergeSort(arr, mid + 1, end);
        
        // Count inversions during merge
        count += merge(arr, start, mid, end);
        
        return count;
    }
    
    int merge(vector<int>& arr, int start, int mid, int end) {
        vector<int> temp(end - start + 1);
        int i = start, j = mid + 1, k = 0;
        int count = 0;
        
        while(i <= mid && j <= end) {
            if(arr[i] <= arr[j]) {
                temp[k++] = arr[i++];
            } else {
                // Count inversions: all elements from i to mid are greater than arr[j]
                count += mid - i + 1;
                temp[k++] = arr[j++];
            }
        }
        
        while(i <= mid) temp[k++] = arr[i++];
        while(j <= end) temp[k++] = arr[j++];
        
        for(int idx = 0; idx < k; idx++) {
            arr[start + idx] = temp[idx];
        }
        
        return count;
    }
};
```

**Key Insights:**
1. **Merge Sort**: Use divide and conquer approach
2. **Inversion Counting**: Count during merge step when left > right
3. **Bulk Counting**: When arr[i] > arr[j], count all inversions with arr[j]
4. **Sorted Subarrays**: After sorting, inversion counting becomes efficient

**Edge Cases:**
- Array with no inversions (sorted array)
- Array with all same elements
- Single element array
- Reverse sorted array (maximum inversions)

**Important Notes:**
- **Time Complexity**: O(n log n) - merge sort complexity
- **Space Complexity**: O(n) - temporary array for merging
- **Bulk Counting**: Count all inversions at once during merge
- **Stable Sort**: Merge sort maintains relative order

**Why Merge Sort Approach Works:**
1. **Divide and Conquer**: Break problem into smaller subproblems
2. **Sorted Subarrays**: After sorting, inversion counting becomes efficient
3. **Bulk Counting**: Count all inversions with current element in one step
4. **Recursive Solution**: Combine results from left and right halves

**Variations:**
1. **Count Reverse Pairs**: Count pairs where nums[i] > 2 * nums[j]
2. **Count Smaller Numbers**: Count smaller numbers after each element
3. **Minimum Swaps**: Find minimum swaps to sort array

**Practice Problems:**
- [LeetCode 315: Count of Smaller Numbers After Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/)
- [GeeksforGeeks: Count Inversions](https://www.geeksforgeeks.org/counting-inversions/)

**Interview Tips:**
- Start with brute force for clarity
- Explain merge sort approach step by step
- Emphasize bulk counting during merge
- Demonstrate inversion counting with examples
- Discuss time and space complexity trade-offs

**Algorithm Breakdown:**
1. **Divide**: Split array into two halves
2. **Conquer**: Recursively sort and count inversions in each half
3. **Count**: Count inversions between left and right halves during merge
4. **Merge**: Merge sorted halves while maintaining count

**Mathematical Foundation:**
- Inversion condition: nums[i] > nums[j] where i < j
- Merge sort ensures sorted subarrays for efficient counting
- Bulk counting reduces time complexity from O(n²) to O(n log n)

---

### Question 29: Maximum Product Subarray

**Link:** [TakeUForward - Maximum Product Subarray](https://takeuforward.org/data-structure/maximum-product-subarray-in-an-array/)

**Problem Statement:**
Given an array of integers, find the maximum product of a contiguous subarray.

**Example:**
```
Input: nums = [2,3,-2,4]
Output: 6
Explanation: The maximum product subarray is [2,3] with product 6.

Input: nums = [-2,0,-1]
Output: 0
Explanation: The maximum product subarray is [0] with product 0.
```

**Intuition:**
Track both maximum and minimum products ending at each position, as negative numbers can turn minimum into maximum.

**Brute Force Approach:**
Check all possible subarrays

```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int maxProduct = INT_MIN;
        int n = nums.size();
        
        for(int i = 0; i < n; i++) {
            int product = 1;
            for(int j = i; j < n; j++) {
                product *= nums[j];
                maxProduct = max(maxProduct, product);
            }
        }
        
        return maxProduct;
    }
};
```

**Optimal Solution:**
Dynamic programming with max and min tracking

```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int n = nums.size();
        if(n == 0) return 0;
        
        int maxProduct = nums[0];
        int currentMax = nums[0];
        int currentMin = nums[0];
        
        for(int i = 1; i < n; i++) {
            // Store previous values
            int prevMax = currentMax;
            int prevMin = currentMin;
            
            // Update current max and min
            currentMax = max({nums[i], prevMax * nums[i], prevMin * nums[i]});
            currentMin = min({nums[i], prevMax * nums[i], prevMin * nums[i]});
            
            // Update global maximum
            maxProduct = max(maxProduct, currentMax);
        }
        
        return maxProduct;
    }
};
```

**Key Insights:**
1. **Negative Numbers**: Negative numbers can turn minimum into maximum
2. **Zero Handling**: Reset to current number when encountering zero
3. **Max/Min Tracking**: Track both maximum and minimum products
4. **Dynamic Programming**: Use previous results to compute current results

**Edge Cases:**
- Array with all negative numbers
- Array with zeros
- Single element array
- Array with alternating positive/negative numbers

**Important Notes:**
- **Time Complexity**: O(n) - single pass through array
- **Space Complexity**: O(1) - constant extra space
- **Negative Handling**: Track minimum to handle negative numbers
- **Zero Handling**: Reset product when encountering zero

**Why Dynamic Programming Approach Works:**
1. **Optimal Substructure**: Maximum product ending at i depends on previous results
2. **Negative Numbers**: Minimum product can become maximum with negative number
3. **Zero Reset**: Zero resets the product chain
4. **Single Pass**: Process array once to find maximum product

**Variations:**
1. **Maximum Sum Subarray**: Kadane's algorithm for sum
2. **Minimum Product Subarray**: Find minimum product subarray
3. **Product of All Subarrays**: Find product of all possible subarrays

**Practice Problems:**
- [LeetCode 152: Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)
- [LeetCode 53: Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

**Interview Tips:**
- Start with brute force for clarity
- Explain why tracking min and max is necessary
- Demonstrate with negative numbers
- Emphasize zero handling
- Discuss time and space complexity trade-offs

**Algorithm Breakdown:**
1. **Initialize**: Set current max and min to first element
2. **Iterate**: Process each element starting from second
3. **Update**: Update current max and min using previous values
4. **Track**: Keep track of global maximum product
5. **Return**: Return the maximum product found

**Mathematical Foundation:**
- Product of subarray ending at i: max(nums[i], max[i-1] * nums[i], min[i-1] * nums[i])
- Negative numbers can turn minimum into maximum
- Zero resets the product chain
- Dynamic programming ensures optimal solution

---

### Question 30: Find the Repeating and Missing Numbers

**Link:** [TakeUForward - Find Repeating and Missing Numbers](https://takeuforward.org/data-structure/find-the-repeating-and-missing-numbers/)

**Problem Statement:**
Given an array of size N containing numbers from 1 to N, find the repeating and missing numbers.

**Example:**
```
Input: arr[] = {3, 1, 2, 5, 3}
Output: Repeating = 3, Missing = 4
Explanation: 3 appears twice and 4 is missing.

Input: arr[] = {1, 2, 2, 4}
Output: Repeating = 2, Missing = 3
```

**Intuition:**
Use mathematical approach with sum and sum of squares to find both numbers simultaneously.

**Brute Force Approach:**
Use hash map to count frequencies

```cpp
class Solution {
public:
    vector<int> findTwoElement(vector<int> arr, int n) {
        vector<int> result(2);
        vector<int> count(n + 1, 0);
        
        // Count frequencies
        for(int i = 0; i < n; i++) {
            count[arr[i]]++;
        }
        
        // Find repeating and missing
        for(int i = 1; i <= n; i++) {
            if(count[i] == 0) {
                result[1] = i; // Missing
            } else if(count[i] == 2) {
                result[0] = i; // Repeating
            }
        }
        
        return result;
    }
};
```

**Optimal Solution:**
Mathematical approach using sum and sum of squares

```cpp
class Solution {
public:
    vector<int> findTwoElement(vector<int> arr, int n) {
        vector<int> result(2);
        
        // Calculate sum and sum of squares
        long long sum = 0, sumSq = 0;
        long long expectedSum = (long long)n * (n + 1) / 2;
        long long expectedSumSq = (long long)n * (n + 1) * (2 * n + 1) / 6;
        
        for(int i = 0; i < n; i++) {
            sum += arr[i];
            sumSq += (long long)arr[i] * arr[i];
        }
        
        // Calculate differences
        long long diff = sum - expectedSum; // repeating - missing
        long long diffSq = sumSq - expectedSumSq; // repeating² - missing²
        
        // Solve equations
        long long sumBoth = diffSq / diff; // repeating + missing
        long long repeating = (diff + sumBoth) / 2;
        long long missing = sumBoth - repeating;
        
        result[0] = (int)repeating;
        result[1] = (int)missing;
        
        return result;
    }
};
```

**Alternative Solution:**
Using XOR approach

```cpp
class Solution {
public:
    vector<int> findTwoElement(vector<int> arr, int n) {
        vector<int> result(2);
        
        // XOR all numbers from 1 to n and array elements
        int xorResult = 0;
        for(int i = 0; i < n; i++) {
            xorResult ^= arr[i];
            xorResult ^= (i + 1);
        }
        
        // Find rightmost set bit
        int rightmostSetBit = xorResult & ~(xorResult - 1);
        
        // Separate numbers into two groups
        int x = 0, y = 0;
        for(int i = 0; i < n; i++) {
            if(arr[i] & rightmostSetBit) {
                x ^= arr[i];
            } else {
                y ^= arr[i];
            }
            
            if((i + 1) & rightmostSetBit) {
                x ^= (i + 1);
            } else {
                y ^= (i + 1);
            }
        }
        
        // Check which is repeating and which is missing
        for(int i = 0; i < n; i++) {
            if(arr[i] == x) {
                result[0] = x; // Repeating
                result[1] = y; // Missing
                break;
            } else if(arr[i] == y) {
                result[0] = y; // Repeating
                result[1] = x; // Missing
                break;
            }
        }
        
        return result;
    }
};
```

**Key Insights:**
1. **Mathematical Approach**: Use sum and sum of squares to solve equations
2. **XOR Approach**: Use XOR properties to find both numbers
3. **Overflow Handling**: Use long long to prevent integer overflow
4. **Equation Solving**: Solve simultaneous equations to find both numbers

**Edge Cases:**
- Array with size 1
- Array with all same numbers
- Large numbers causing overflow
- Array with no missing number

**Important Notes:**
- **Time Complexity**: O(n) - single pass through array
- **Space Complexity**: O(1) - constant extra space
- **Overflow Prevention**: Use long long for calculations
- **Mathematical Formulas**: Use sum and sum of squares formulas

**Why Mathematical Approach Works:**
1. **Sum Difference**: repeating - missing = actual_sum - expected_sum
2. **Square Sum Difference**: repeating² - missing² = actual_square_sum - expected_square_sum
3. **Equation Solving**: Solve simultaneous equations to find both numbers
4. **Single Pass**: Process array once to find both numbers

**Variations:**
1. **Find Single Missing Number**: Find only missing number
2. **Find Single Repeating Number**: Find only repeating number
3. **Find Multiple Missing Numbers**: Find multiple missing numbers

**Practice Problems:**
- [LeetCode 645: Set Mismatch](https://leetcode.com/problems/set-mismatch/)
- [GeeksforGeeks: Find Missing and Repeating](https://www.geeksforgeeks.org/find-a-repeating-and-a-missing-number/)

**Interview Tips:**
- Start with hash map approach for clarity
- Explain mathematical approach step by step
- Emphasize overflow handling with long long
- Demonstrate XOR approach as alternative
- Discuss time and space complexity trade-offs

**Algorithm Breakdown:**
1. **Calculate Sums**: Find actual sum and sum of squares
2. **Calculate Expected**: Find expected sum and sum of squares
3. **Find Differences**: Calculate differences between actual and expected
4. **Solve Equations**: Solve simultaneous equations to find both numbers

**Mathematical Foundation:**
- Expected sum: n * (n + 1) / 2
- Expected sum of squares: n * (n + 1) * (2n + 1) / 6
- repeating - missing = actual_sum - expected_sum
- repeating² - missing² = actual_square_sum - expected_square_sum

---

### Question 31: Merge Two Sorted Arrays Without Extra Space

**Link:** [TakeUForward - Merge Two Sorted Arrays](https://takeuforward.org/data-structure/merge-two-sorted-arrays-without-extra-space/)

**Problem Statement:**
Given two sorted arrays arr1[] and arr2[] of sizes n and m in non-decreasing order. Merge them in sorted order without using any extra space.

**Example:**
```
Input: arr1[] = {1, 4, 7, 8, 10}, arr2[] = {2, 3, 9}
Output: arr1[] = {1, 2, 3, 4, 7}, arr2[] = {8, 9, 10}

Input: arr1[] = {1, 3, 5, 7}, arr2[] = {0, 2, 6, 8, 9}
Output: arr1[] = {0, 1, 2, 3}, arr2[] = {5, 6, 7, 8, 9}
```

**Intuition:**
Use insertion sort approach or gap method to merge arrays in-place without extra space.

**Brute Force Approach:**
Use insertion sort technique

```cpp
class Solution {
public:
    void merge(int arr1[], int arr2[], int n, int m) {
        // Compare elements from end of arr1 with start of arr2
        for(int i = n - 1; i >= 0; i--) {
            // Find correct position for arr1[i] in arr2
            int last = arr2[m - 1];
            int j;
            for(j = m - 2; j >= 0 && arr2[j] > arr1[i]; j--) {
                arr2[j + 1] = arr2[j];
            }
            
            if(j != m - 2 || last > arr1[i]) {
                arr2[j + 1] = arr1[i];
                arr1[i] = last;
            }
        }
    }
};
```

**Optimal Solution:**
Gap method (Shell sort variation)

```cpp
class Solution {
public:
    void merge(int arr1[], int arr2[], int n, int m) {
        int gap = (n + m + 1) / 2;
        
        while(gap > 0) {
            // Compare elements in first array
            int i = 0;
            while(i + gap < n) {
                if(arr1[i] > arr1[i + gap]) {
                    swap(arr1[i], arr1[i + gap]);
                }
                i++;
            }
            
            // Compare elements between two arrays
            int j = gap > n ? gap - n : 0;
            while(i < n && j < m) {
                if(arr1[i] > arr2[j]) {
                    swap(arr1[i], arr2[j]);
                }
                i++;
                j++;
            }
            
            // Compare elements in second array
            if(j < m) {
                j = 0;
                while(j + gap < m) {
                    if(arr2[j] > arr2[j + gap]) {
                        swap(arr2[j], arr2[j + gap]);
                    }
                    j++;
                }
            }
            
            gap = gap == 1 ? 0 : (gap + 1) / 2;
        }
    }
};
```

**Alternative Solution:**
Using Euclidean division lemma

```cpp
class Solution {
public:
    void merge(int arr1[], int arr2[], int n, int m) {
        // Use Euclidean division lemma
        // Store all elements in arr1 using formula: arr1[i] = arr1[i] + arr2[j] * max_val
        int max_val = 1e9 + 1;
        
        for(int i = 0; i < n; i++) {
            arr1[i] = arr1[i] + arr2[i] * max_val;
        }
        
        for(int i = n; i < n + m; i++) {
            arr1[i] = arr2[i - n] + arr2[i] * max_val;
        }
        
        // Sort the combined array
        sort(arr1, arr1 + n + m);
        
        // Extract original elements
        for(int i = 0; i < n; i++) {
            arr1[i] = arr1[i] % max_val;
        }
        
        for(int i = 0; i < m; i++) {
            arr2[i] = arr1[n + i] % max_val;
        }
    }
};
```

**Key Insights:**
1. **Gap Method**: Use gap-based comparison similar to Shell sort
2. **In-place Merging**: Merge without using extra space
3. **Gap Reduction**: Reduce gap by half in each iteration
4. **Three Comparisons**: Compare within arr1, between arrays, and within arr2

**Edge Cases:**
- One array is empty
- Arrays have same size
- All elements in one array are smaller than other
- Arrays have same elements

**Important Notes:**
- **Time Complexity**: O((n + m) log(n + m)) - gap method
- **Space Complexity**: O(1) - no extra space used
- **Gap Calculation**: Start with (n + m + 1) / 2
- **Gap Reduction**: Reduce by (gap + 1) / 2

**Why Gap Method Works:**
1. **Shell Sort Principle**: Use gap-based comparisons for efficient sorting
2. **In-place Operation**: No extra space required
3. **Gap Reduction**: Gradually reduce gap to achieve sorted order
4. **Three-phase Comparison**: Handle all possible comparisons

**Variations:**
1. **Merge K Sorted Arrays**: Merge multiple sorted arrays
2. **Merge with Extra Space**: Use extra space for simpler solution
3. **Merge Linked Lists**: Merge sorted linked lists

**Practice Problems:**
- [LeetCode 88: Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)
- [GeeksforGeeks: Merge Without Extra Space](https://www.geeksforgeeks.org/merge-two-sorted-arrays-o1-extra-space/)

**Interview Tips:**
- Start with insertion sort approach for clarity
- Explain gap method step by step
- Emphasize in-place merging requirement
- Demonstrate gap reduction process
- Discuss time complexity analysis

**Algorithm Breakdown:**
1. **Initialize Gap**: Start with (n + m + 1) / 2
2. **Compare Within Arrays**: Compare elements with gap distance
3. **Compare Between Arrays**: Compare elements across arrays
4. **Reduce Gap**: Reduce gap by (gap + 1) / 2
5. **Repeat**: Continue until gap becomes 0

**Mathematical Foundation:**
- Gap method is based on Shell sort algorithm
- Gap reduction: gap = (gap + 1) / 2
- Time complexity: O((n + m) log(n + m))
- Space complexity: O(1) - constant extra space

---

## 📊 Summary

This DSA revision sheet contains **31 comprehensive problems** covering fundamental array and matrix concepts:

### **Array Problems (Questions 1-17)**
- **Basic Array Operations**: Finding largest element, second order elements, checking sorted arrays
- **Array Manipulation**: Rotation, moving zeros, union of arrays
- **Search & Counting**: Missing numbers, consecutive ones, single numbers
- **Subarray Problems**: Longest subarray with sum K, subarray sum equals K
- **Advanced Algorithms**: Two sum, Dutch National Flag, Majority Element, Kadane's Algorithm
- **Stock Problems**: Buy and sell optimization
- **Permutation & Sequences**: Next permutation, longest consecutive sequence in`

### **Matrix & Advanced Array Problems (Questions 18-31)**
- **Matrix Traversal**: Spiral traversal with multiple approaches
- **Advanced Array Concepts**: Count subarray sum equals K with prefix sum
- **Mathematical Patterns**: Pascal's triangle with combination formula
- **Voting Algorithms**: Majority elements (n/3) using Boyer-Moore algorithm
- **Sum Problems**: 3-Sum and 4-Sum using two pointers approach
- **Subarray Problems**: Longest subarray with zero sum, count subarrays with XOR K
- **Interval Problems**: Merge overlapping intervals
- **Counting Problems**: Count reverse pairs and inversions using merge sort
- **Product Problems**: Maximum product subarray using dynamic programming
- **Mathematical Problems**: Find repeating and missing numbers using mathematical approach
- **Merging Problems**: Merge sorted arrays without extra space using gap method

### **Key Features:**
✅ **Multiple Approaches**: Each problem includes brute force, better, and optimal solutions  
✅ **Complete C++ Implementations**: Ready-to-use code for all problems  
✅ **Time & Space Complexity**: Detailed analysis for each approach  
✅ **Edge Cases**: Comprehensive coverage of boundary conditions  
✅ **Interview Tips**: Practical advice for coding interviews  
✅ **Practice Problems**: Links to related LeetCode problems  
✅ **Mathematical Insights**: Deep understanding of algorithms  

### **Problem Categories:**
- **Easy**: Questions 1-8 (Basic array operations)
- **Medium**: Questions 9-17 (Advanced algorithms and concepts)
- **Hard**: Questions 18-31 (Matrix and complex array problems)

### **Learning Path:**
1. Start with basic array operations (Questions 1-8)
2. Move to intermediate concepts (Questions 9-17)
3. Master advanced topics (Questions 18-31)
4. Practice variations and related problems

---

**Happy Coding! 🚀**
