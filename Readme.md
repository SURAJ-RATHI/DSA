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
This problem is a variation of the popular Dutch National flag algorithm. 

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
