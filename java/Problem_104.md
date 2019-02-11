### Palindrome Linked List
```java

/*
This problem was asked by Google.

Determine whether a doubly linked list is a palindrome. What if it’s singly linked?

For example, 1 -> 4 -> 3 -> 4 -> 1 returns true while 1 -> 4 returns false.

LeetCode Link: https://leetcode.com/problems/palindrome-linked-list/description/
*/
//Method !: Using Recursion
boolean isPal = true;
    
public boolean isPalindrome(ListNode head) {
    ListNode node1 = head, node2 = head;
    helper(node1, node2);
    return isPal;
}
    
public ListNode helper(ListNode node1, ListNode head) {
    if(node1==null) {
        return head;
    }
        
    ListNode node2 = helper(node1.next, head);
        
    if(node1.val != node2.val){
        isPal = false;
    }
    return node2.next;
}
```