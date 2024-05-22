# Add Two Numbers

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

### Steps
1. Create a placeholder node `dummyHead` with value = 0 , this will hold the resulting linked list.
2. Creata a pointer `tail` that will kepp track of the last node in the result list.
3. Create variable `carry` = 0, to store carry value during addition.
4. Start the loop until there is no value in `l1`, or `l2`.
5. Inside the loop:
    - Check  if there is a digit in the current node in `l1`, if it exists assign its value to variable `digit1` else set it to 0.
    - Check  if there is a digit in the current node in `l2`, if it exists assign its value to variable `digit2` else set it to 0.
    - Add the two along with thw carry from the previous iteration and store in `sum`.
    - Calculate `sum` by taking `%` of sum by 10 and the digit will be placed in a new node for the result.
    - Update the `carry` variable by dividing `sum` by 10 amd taking the integer division part `/` , giving us carry value for the netxt iteration.
    - Create a new node with the calculated digit as its value.
    - Attach the new node to the `tail` node of the result list.
    - Move the `tail` pointer to a newly added node
    - Move the next nodes in both `l1` and `l2`, if they exist, if lists are exhausted, set pointer to `nullptr`
6. After loop, get actual result by skipping `dummyHead` node.
7. Delete `dummyHead`
8. Return the resulting list.


- Time Complexity -> O(n)
- Space Complexity -> O(n)
```
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        dummyHead = ListNode(0)
        tail = dummyHead
        carry = 0

        while l1 is not None or l2 is not None or carry != 0:
            digit1 = l1.val if l1 is not None else 0
            digit2 = l2.val if l2 is not None else 0

            sum = digit1 + digit2 + carry
            digit = sum % 10
            carry = sum //10

            newNode = ListNode(digit)
            tail.next = newNode
            tail = tail.next

            l1 = l1.next if is not None else 0
            l2 = l2.next if is not None else 0
        
        result = dummyHead.next
        dummyHead.next = None
        return result

```