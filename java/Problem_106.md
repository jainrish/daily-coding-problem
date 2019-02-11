### Jump Game
```java

/*
This problem was asked by Pinterest.

Given an integer list where each number represents the number of hops you can make, determine whether you can reach to the last index starting at index 0.

For example, [2, 0, 1, 0] returns true while [1, 1, 0, 1] returns false.

LeetCode Link: https://leetcode.com/problems/jump-game/description/
*/

public boolean canJump(int[] nums) {
    int max = 0;
    for(int i=0;i<=max&&i<nums.length;i++) {
        max = Math.max(max, nums[i]+i);
    }       
    return max>=(nums.length-1);
}
```