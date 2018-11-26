### Product of Array Except Self
```java

/*
This problem was asked by Uber.

Given an array of integers, return a new array such that each element at index i of the new array is the product of all the numbers in the original array except the one at i.

For example, if our input was [1, 2, 3, 4, 5], the expected output would be [120, 60, 40, 30, 24]. If our input was [3, 2, 1], the expected output would be [2, 3, 6].

Follow-up: what if you can't use division?

LeetCode Link: https://leetcode.com/problems/product-of-array-except-self/description/
*/


//O(1) space complexity, O(n) time complexity
 public int[] productExceptSelf(int[] arr) {
    int[] res = new int[arr.length];
    if(arr.length==0) return res;
    int n = arr.length;
    res[n-1] = 1;
        
    for(int i=n-2;i>=0;i--) {
        res[i] = res[i+1]*arr[i+1];
    }

    int num = arr[0];
    for(int i=1;i<n;i++) {
        res[i]*=num;
        num*=arr[i];
    }
    return res;
}

```