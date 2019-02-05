## Non-decreasing Array
```java
/*
This problem was asked by Facebook.

Given an array of integers, write a function to determine whether the array could become non-decreasing by modifying at most 1 element.

For example, given the array [10, 5, 7], you should return true, since we can modify the 10 into a 1 to make the array non-decreasing.

Given the array [10, 5, 1], you should return false, since we can't modify any one element to get a non-decreasing array.

LeetCode Link: https://leetcode.com/problems/non-decreasing-array/description/
*/

public boolean checkPossibility(int[] nums) {
        if (nums.length <= 2)
            return true;
        boolean mod = false, tryAgain = false;
        int curr = nums[0];

        for (int i = 0; i < nums.length - 1; i++) {
            if (curr > nums[i + 1]) {
                if (mod) {
                    tryAgain = true;
                    break;
                }
                ;
                curr = nums[i];
                mod = true;
            } else {
                curr = nums[i + 1];
            }
        }

        if (tryAgain) {
            curr = nums[nums.length - 1];
            mod = false;
            for (int i = nums.length - 1; i > 0; i--) {
                if (nums[i - 1] > curr) {
                    if (mod)
                        return false;
                    mod = true;
                    curr = nums[i];
                } else {
                    curr = nums[i - 1];
                }
            }
        }

        return true;
    }
```