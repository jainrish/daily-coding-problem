## SubArray Sum Equals K
```java
/*
This problem was asked by Lyft.

Given a list of integers and a number K, return which contiguous elements of the list sum to K.

For example, if the list is [1, 2, 3, 4, 5] and K is 9, then it should return [2, 3, 4].

LeetCode Link(Similar Question): https://leetcode.com/problems/subarray-sum-equals-k/description/
*/

public List<List<Integer>> subarraySum(int[] nums, int k) {
    Map<Integer, List<Integer>> indexMap = new HashMap<>();
    List<List<Integer>> res = new ArrayList<>();
        
    List<Integer> temp = new ArrayList<>();
    temp.add(-1);
        
    indexMap.put(0, temp);
        
    int sum = 0, i = 0;
    for(int num :  nums) {
        sum+=num;
        if(indexMap.containsKey(sum-k)) {
            temp = new ArrayList<>();
            for(int index : indexMap.get(sum-k)) {
                for(int j=index+1;j<=i;j++) {
                    temp.add(nums[j]);
                }
            }
            res.add(temp);
        }
        if(!indexMap.containsKey(sum)) {
            indexMap.put(sum, new ArrayList<>());
        }
        indexMap.get(sum).add(i++);
    }
        
    return res;
}
```