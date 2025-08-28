# 📘 Striver A2Z DSA Sheet – Solutions (C++)

This repository contains my notes + C++ solutions for **Striver's A2Z DSA Sheet**.  
Each problem includes:  
✅ Intuition  
✅ Brute / Better / Optimal Approaches  
✅ Edge Cases  
✅ Code snippets  

---

## 📑 Table of Contents  
- [Day 01 – Find the Largest Element in an Array](#-day-01--find-the-largest-element-in-an-array)  
- [Day 02 – Remove Outermost Parentheses](#-day-02--remove-outermost-parentheses)  
(Will keep updating…)

---

## 📂 Day 01 – Find the Largest Element in an Array  
**URL:** [Take U Forward](https://takeuforward.org/data-structure/find-the-largest-element-in-an-array/)

### 💡 Intuition  
The largest element is simply the maximum among all array elements.  
We can track it while scanning linearly.

---

### 🟠 Brute Force  
- Sort the array and return the last element.  
- **Time Complexity:** `O(n log n)`  
- **Space Complexity:** `O(1)`  

```cpp
int findLargestBrute(vector<int>& arr) {
    sort(arr.begin(), arr.end());
    return arr.back();
}
```
### 🟠 Better Solution  
- Sort the array and return the last element.  
- **Time Complexity:** `O(n log n)`  
- **Space Complexity:** `O(1)`  

```cpp
int findLargestBrute(vector<int>& arr) {
    sort(arr.begin(), arr.end());
    return arr.back();
}
```

### 🟠 Optimal Solution 
- Sort the array and return the last element.  
- **Time Complexity:** `O(n log n)`  
- **Space Complexity:** `O(1)`  

```cpp
int findLargestBrute(vector<int>& arr) {
    sort(arr.begin(), arr.end());
    return arr.back();
}
```


