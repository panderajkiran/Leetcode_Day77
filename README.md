# Leetcode_Day77
# Day 77: Longest Harmonious Subsequence

**LeetCode Problem:** 594. Longest Harmonious Subsequence  
**Difficulty:** Easy  
**Topic:** Arrays, Sorting, Sliding Window  
**Language:** Java

## Problem Statement

A harmonious array is an array in which the difference between the maximum and minimum values is exactly `1`.

Given an integer array `nums`, find the length of its longest harmonious subsequence.

A subsequence can be created by removing some elements without changing the relative order of the remaining elements.

## Approach: Sorting and Sliding Window

I solved this problem by sorting the array and using the sliding window technique.

### Steps

1. Sort the array in ascending order.
2. Initialize two pointers, `left` and `right`, to maintain a window.
3. Move the `right` pointer through the array.
4. If the difference between `nums[right]` and `nums[left]` is greater than `1`, move `left` forward until the difference becomes at most `1`.
5. If the difference is exactly `1`, update the maximum length using `right - left + 1`.
6. Return the maximum length found.

Sorting places equal values together, making it easier to find a subsequence containing two distinct values that differ by exactly `1`.

## Java Solution

```java
import java.util.Arrays;

class Solution {
    public int findLHS(int[] nums) {
        Arrays.sort(nums);

        int left = 0;
        int ans = 0;

        for (int right = 0; right < nums.length; right++) {
            while (nums[right] - nums[left] > 1) {
                left++;
            }

            if (nums[right] - nums[left] == 1) {
                ans = Math.max(ans, right - left + 1);
            }
        }

        return ans;
    }
}
```

## Example

**Input:**
```text
nums = [1,3,2,2,5,2,3,7]
```

**Output:**
```text
5
```

**Explanation:**

After sorting, the array becomes:

`[1,2,2,2,3,3,5,7]`

The longest harmonious subsequence contains three occurrences of `2` and two occurrences of `3`.

The difference between the maximum and minimum values is:

`3 - 2 = 1`

Therefore, the length of the longest harmonious subsequence is `5`.

## Complexity Analysis

- **Time Complexity:** O(n log n), because sorting takes O(n log n), followed by a linear sliding window traversal.
- **Space Complexity:** O(log n) auxiliary space for sorting, depending on the sorting implementation and input.

## What I Learned

- How sorting can simplify array problems.
- How to use two pointers to maintain a valid window.
- How to identify a valid subsequence using a specific difference condition.
- How `Math.max()` helps track the longest valid result.
- Why the window must contain values whose difference is exactly `1`, not merely at most `1`.

## Takeaway

Today's problem reminded me that organizing information before analyzing it can make a problem easier to solve.

Sometimes, a little preparation helps us see patterns that were difficult to notice before.

**Day 77 complete — one problem, one lesson, and one more step forward!**
