# Day 7
## [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        if(head == null || head.next == null)
            return false;
        ListNode slowPtr = head;
        ListNode fastPtr = head;
        while(slowPtr != null && fastPtr != null) {
            slowPtr = slowPtr.next;
            fastPtr = fastPtr.next;
            if(fastPtr != null)
                fastPtr = fastPtr.next;
            if(slowPtr == fastPtr)
                return true;
        }
        return false;
    }
}
```
## [21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if(l1 == null) return l2;
        if(l2 == null) return l1;
        ListNode tmp =  new ListNode(0);
        ListNode curr = tmp;
        while(l1 != null && l2 != null){
            if(l1.val < l2.val) {
                curr.next = l1;
                l1 = l1.next;
            } else {
                curr.next = l2;
                l2 = l2.next;
            }
            curr = curr.next;
        }
        curr.next = l1==null?l2:l1;
        return tmp.next;
    }
}
```
## [203. Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/)
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        if(head == null) return head;
        ListNode fakeHead = new ListNode(-1);
        fakeHead.next = head;
        ListNode curr = fakeHead;
        while(curr.next != null) {
            if(curr.next.val == val) {
                curr.next = curr.next.next;
            } else {
                curr = curr.next;
            }
        }
        return fakeHead.next;
    }
}
```
