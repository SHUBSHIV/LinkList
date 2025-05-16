LinkList DSA Problem
📌 Remove Duplicates from Sorted List
This repository contains Java solutions for two common Linked List problems:

Remove Duplicates from Sorted List (Leetcode 83)

Remove Duplicates from Sorted List II (Leetcode 82)

🧠 Problem Statements
✅ Problem 1: Remove Duplicates from Sorted List (Leetcode 83)
Given the head of a sorted linked list, delete all duplicates such that each element appears only once.

🔸 Example:
rust
Copy
Edit
Input:  1 -> 1 -> 2 -> 3 -> 3  
Output: 1 -> 2 -> 3
✅ Problem 2: Remove Duplicates from Sorted List II (Leetcode 82)
Given the head of a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.

🔸 Example:
rust
Copy
Edit
Input:  1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5  
Output: 1 -> 2 -> 5
🧾 Approach
🟩 For Problem 1:
Use a single pointer current.

If current.val == current.next.val, skip the duplicate node by linking to current.next.next.

🟦 For Problem 2:
Use a dummy node and two pointers (prev and current).

If duplicates are found, skip the entire group of nodes with the same value.

Link prev.next to the node after the last duplicate.

🧑‍💻 Code (Java)
🔹 Problem 1 (Leetcode 83)
java
Copy
Edit
public ListNode deleteDuplicates(ListNode head) {
    ListNode current = head;
    while (current != null && current.next != null) {
        if (current.val == current.next.val) {
            current.next = current.next.next;
        } else {
            current = current.next;
        }
    }
    return head;
}
🔹 Problem 2 (Leetcode 82)
java
Copy
Edit
public ListNode deleteDuplicates(ListNode head) {
    ListNode dummy = new ListNode(0);
    dummy.next = head;
    ListNode prev = dummy;
    ListNode current = head;

    while (current != null) {
        if (current.next != null && current.val == current.next.val) {
            while (current.next != null && current.val == current.next.val) {
                current = current.next;
            }
            prev.next = current.next;
        } else {
            prev = prev.next;
        }
        current = current.next;
    }

    return dummy.next;
}
🧪 Test Cases
Test Case 1:
rust
Copy
Edit
Input: 1 -> 1 -> 2  
Output: 1 -> 2
Test Case 2:
rust
Copy
Edit
Input: 1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5  
Output: 1 -> 2 -> 5
