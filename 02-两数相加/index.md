# 02 两数相加


给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。

如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。

您可以假设除了数字 0 之外，这两个数都不会以 0 开头。

示例：

```
输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807
```

代码

```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        list_1 = ""
        list_2 = ""
        if not l1 and not l2:
            return 0

        while l1:
            list_1 += str(l1.val)
            l1 = l1.next
        num_1 = int(list_1[::-1]) if list_1 else 0
        while l2:
            list_2 += str(l2.val)
            l2 = l2.next
        num_2 = int(list_2[::-1]) if list_2 else 0
        sum = list(str(num_1 + num_2)[::-1])
        head = ListNode(sum[0])
        cur = head
        for i in range(1, len(sum)):
            cur.next = ListNode(sum[i])
            cur = cur.next
        return head
            
        
    
```
