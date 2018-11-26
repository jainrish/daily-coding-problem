### Two Sum
```java

/*
Given a list of numbers and a number k, return whether any two numbers from the list add up to k.

For example, given [10, 15, 3, 7] and k of 17, return true since 10 + 7 is 17.

Bonus: Can you do this in one pass?

LeetCode Link: https://leetcode.com/problems/two-sum/description/

*/

//O(1) space complexity, O(nlogn) time complexity
 public boolean twoSum(int[] nums, int target) {
	Arrays.sort(nums);
	int start = 0, end = nums.length-1;
        
	while(start<end) {
		int sum = nums[start]+nums[end];
		if(sum>target) {
			end--;
		} else if(sum<target) {
			start++;
		} else if(sum==target) {
			return true;
			break;
		}
	}    
	return false;
}

//O(n) space complexity, O(n) time complexity
public boolean twoSum(int[] nums, int target) {
	Map<Integer, Integer> map = new HashMap<>();

	for(int i=0;i<nums.length;i++) {
		if(map.containsKey(target-nums[i])) {
			return true;
		} else {
			map.put(nums[i], i);
		}
	}	        
	return false;
}
```