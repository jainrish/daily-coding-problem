## Longest Consecutive Sequence
```java
/*
This problem was asked by Microsoft.

Given an unsorted array of integers, find the length of the longest consecutive elements sequence.

For example, given [100, 4, 200, 1, 3, 2], the longest consecutive element sequence is [1, 2, 3, 4]. Return its length: 4.

Your algorithm should run in O(n) complexity.

LeetCode Link: https://leetcode.com/problems/longest-consecutive-sequence/description/
*/

//Solution 1: Using two Sets
public int longestConsecutive(int[] nums) {
        if(nums.length==0) return 0;
        Set<Integer> set = new HashSet<>(), visited = new HashSet<>();
        
        for(int num : nums) set.add(num);
        
        int count = 0, ans = 0;
        
        for(int num : set) {
            if(visited.contains(num)) continue;
            visited.add(num);
            count = 0;
            int temp = num+1;
            while(set.contains(temp)) {
                count++;
                temp++;
                visited.add(temp);
            }
            
            temp = num-1;
            while(set.contains(temp)) {
                count++;
                temp--;
                visited.add(temp);
            }
            ans = Math.max(ans, count);
        }
        
        return ans+1;
}


//Solution 2: Using one Set
public int longestConsecutive(int[] nums) {
        if(nums.length==0) return 0;
        Set<Integer> set = new HashSet<>();
        
        for(int num : nums) set.add(num);
        
        int count = 0, ans = 0;
        
        for(int num : set) {
            if(set.contains(num-1)) continue;
            count = 0;
            
            while(set.contains(num)) {
                count++;
                num++;
            }
            ans = Math.max(ans, count);
        }
        
        return ans;
}

```