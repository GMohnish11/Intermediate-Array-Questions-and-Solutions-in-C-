# Intermediate Array Questions and Solutions in C++

This repository contains intermediate-level array problems and their solutions in C++, designed for learning and practice. Each problem includes a description, a C++ solution, and an explanation. These are ideal for students, developers, or anyone preparing for coding interviews or competitive programming.

## Table of Contents
1. [Rotate Array by K Positions](#rotate-array-by-k-positions)
2. [Find Maximum Subarray Sum (Kadane’s Algorithm)](#find-maximum-subarray-sum-kadanes-algorithm)
3. [Search in a Sorted and Rotated Array](#search-in-a-sorted-and-rotated-array)
4. [Merge Two Sorted Arrays Without Extra Space](#merge-two-sorted-arrays-without-extra-space)
5. [Find the Missing Number in an Array](#find-the-missing-number-in-an-array)

---

## Rotate Array by K Positions

### Problem
Given an array of integers and an integer `k`, rotate the array to the right by `k` positions. For example, if `arr = [1, 2, 3, 4, 5]` and `k = 2`, the result is `[4, 5, 1, 2, 3]`.

### Solution
```cpp
#include <vector>
void rotateArray(std::vector<int>& arr, int k) {
    int n = arr.size();
    if (n == 0 || k == 0) return;
    k = k % n; // Normalize k to handle cases where k > n

    // Helper function to reverse a portion of the array
    auto reverse = [&](int start, int end) {
        while (start < end) {
            std::swap(arr[start++], arr[end--]);
        }
    };

    // Reverse the entire array
    reverse(0, n - 1);
    // Reverse first k elements
    reverse(0, k - 1);
    // Reverse remaining elements
    reverse(k, n - 1);
}
```

### Explanation
- **Approach**: Use the reversal algorithm to rotate the array. Reverse the entire array, then reverse the first `k` elements, and finally reverse the remaining `n-k` elements.
- **Time Complexity**: O(n), where `n` is the array size.
- **Space Complexity**: O(1), as it modifies the array in-place.
- **Edge Cases**: Handle `k > n` by using `k % n`, and empty arrays or `k = 0`.

---

## Find Maximum Subarray Sum (Kadane’s Algorithm)

### Problem
Given an array of integers (positive or negative), find the maximum sum of any contiguous subarray. For example, if `arr = [-2, 1, -3, 4, -1, 2, 1, -5, 4]`, the result is `6` (subarray `[4, -1, 2, 1]`).

### Solution
```cpp
#include <vector>
int maxSubArraySum(std::vector<int>& arr) {
    int max_so_far = arr[0], curr_max = arr[0];
    for (int i = 1; i < arr.size(); i++) {
        curr_max = std::max(arr[i], curr_max + arr[i]);
        max_so_far = std::max(max_so_far, curr_max);
    }
    return max_so_far;
}
```

### Explanation
- **Approach**: Use Kadane’s algorithm. Track the maximum sum ending at each index (`curr_max`) and update the global maximum (`max_so_far`).
- **Time Complexity**: O(n), single pass through the array.
- **Space Complexity**: O(1), uses only two variables.
- **Edge Cases**: Works for arrays with all negative numbers or single elements.

---

## Search in a Sorted and Rotated Array

### Problem
Given a sorted array that has been rotated at an unknown pivot, search for a target element. For example, if `arr = [4, 5, 6, 7, 0, 1, 2]` and `target = 0`, return index `4`. Return `-1` if the target is not found.

### Solution
```cpp
#include <vector>
int searchRotatedArray(std::vector<int>& arr, int target) {
    int n = arr.size(), left = 0, right = n - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target) return mid;

        // Check if left half is sorted
        if (arr[left] <= arr[mid]) {
            // Check if target lies in left half
            if (target >= arr[left] && target < arr[mid]) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        // Right half is sorted
        else {
            // Check if target lies in right half
            if (target > arr[mid] && target <= arr[right]) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
    }
    return -1;
}
```

### Explanation
- **Approach**: Use binary search, modified for rotated arrays. Determine which half is sorted and check if the target lies within it.
- **Time Complexity**: O(log n), binary search.
- **Space Complexity**: O(1), constant space.
- **Edge Cases**: Handles single-element arrays, no rotation, or target not present.

---

## Merge Two Sorted Arrays Without Extra Space

### Problem
Given two sorted arrays `arr1` and `arr2` of sizes `m` and `n`, merge them into a single sorted array without using extra space. `arr1` has enough space to hold `m + n` elements (extra space at the end).

### Solution
```cpp
#include <vector>
void mergeArrays(std::vector<int>& arr1, int m, std::vector<int>& arr2, int n) {
    int i = m - 1; // Last element of arr1's initial content
    int j = n - 1; // Last element of arr2
    int k = m + n - 1; // Last index of arr1's total space

    while (j >= 0) {
        if (i >= 0 && arr1[i] > arr2[j]) {
            arr1[k--] = arr1[i--];
        } else {
            arr1[k--] = arr2[j--];
        }
    }
}
```

### Explanation
- **Approach**: Start from the end of both arrays and fill `arr1` backwards by comparing elements from `arr1` and `arr2`.
- **Time Complexity**: O(m + n), single pass through both arrays.
- **Space Complexity**: O(1), no extra space used.
- **Edge Cases**: Handles empty `arr2` or `arr1` with space for `arr2`.

---

## Find the Missing Number in an Array

### Problem
Given an array of `n` integers from `0` to `n` with one missing number, find the missing number. For example, if `arr = [3, 0, 1]`, the missing number is `2` (since `n = 3`).

### Solution
```cpp
#include <vector>
int findMissingNumber(std::vector<int>& arr) {
    int n = arr.size(); // n is size, but n+1 is the range (0 to n)
    int expected_sum = (n * (n + 1)) / 2; // Sum of numbers 0 to n
    int actual_sum = 0;
    for (int num : arr) actual_sum += num;
    return expected_sum - actual_sum;
}
```

### Explanation
- **Approach**: Calculate the expected sum of numbers from `0` to `n` using the formula `n * (n + 1) / 2`, subtract the actual sum of the array, and the difference is the missing number.
- **Time Complexity**: O(n), single pass to compute the sum.
- **Space Complexity**: O(1), constant space.
- **Edge Cases**: Handles arrays where the missing number is `0` or `n`.

---

## How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/GMohnish11/CPP-Array-Questions.git
   cd CPP-Array-Questions
   ```
2. Compile and run any solution:
   ```bash
     g++ solution1_rotate_array.cpp -o rotate_array
     ./rotate_array
   ```
3. Modify `main.cpp` (included in the repo) to test different inputs or integrate solutions.

## Directory Structure
```
├── solutions/
│   ├── solution1_rotate_array.cpp
│   ├── solution2_max_subarray_sum.cpp
│   ├── solution3_search_rotated.cpp
│   ├── solution4_merge_arrays.cpp
│   ├── solution5_missing_number.cpp
├── main.cpp                    # Driver code to test solutions
├── cpp_array_questions.md      # This file
└── LICENSE                     # MIT License
```

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a branch: `git checkout -b feature/new-question`.
3. Add your problem and solution in `solutions/`.
4. Update this Markdown file with the new problem.
5. Submit a Pull Request.

Report issues via the [Issues](https://github.com/GMohnish11/CPP-Array-Questions/issues) tab.

## License
Licensed under the MIT License. See [LICENSE](LICENSE) for details.

## Acknowledgments
- **Author**: Mohnish Gupta
- **Inspiration**: Competitive programming platforms like LeetCode and GeeksforGeeks.
- **Institution**: St. Peter's Engineering College, Hyderabad.

## Contact
For inquiries, contact Mohnish Gupta via GitHub issues.
