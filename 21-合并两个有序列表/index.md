# 21 合并两个有序列表




将两个升序链表合并为一个新的升序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。

#### 示例：

```
输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
方法 2：迭代
想法

我们可以用迭代的方法来实现上述算法。我们假设 l1 元素严格比 l2元素少，我们可以将 l2 中的元素逐一插入 l1 中正确的位置。

算法

首先，我们设定一个哨兵节点 "prehead" ，这可以在最后让我们比较容易地返回合并后的链表。我们维护一个 prev 指针，我们需要做的是调整它的 next 指针。然后，我们重复以下过程，直到 l1 或者 l2 指向了 null ：如果 l1 当前位置的值小于等于 l2 ，我们就把 l1 的值接在 prev 节点的后面同时将 l1 指针往后移一个。否则，我们对 l2 做同样的操作。不管我们将哪一个元素接在了后面，我们都把 prev 向后移一个元素。

在循环终止的时候， l1 和 l2 至多有一个是非空的。由于输入的两个链表都是有序的，所以不管哪个链表是非空的，它包含的所有元素都比前面已经合并链表中的所有元素都要大。这意味着我们只需要简单地将非空链表接在合并链表的后面，并返回合并链表。
```

![image](https://pic.leetcode-cn.com/f6a8a3f573188706887808ef769ce3dc496e1bc3ef9b737e24498bd740442bb4-image.png?ynotemdtimestamp=1593701291427)

```
# -*- coding: utf-8 -*-
# @Time     : 2020/3/27 23:37
# @Author   : affectalways
# @Site     : 
# @Contact  : affectalways@gmail.com
# @File     : 21_.py
# @Software : PyCharm 

# Definition for singly-linked list.
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None


class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode):
        # head = ListNode(-1)
        head = ListNode(-1)
        cur = head

        while l1 and l2:
            if l1.val <= l2.val:
                cur.next = l1
                l1 = l1.next
            else:
                cur.next = l2
                l2 = l2.next
            cur = cur.next

        cur.next = l1 if l2 is None else l2
        return head.next


if __name__ == '__main__':
    solution = Solution()
    head_1 = ListNode(1)
    node_2 = ListNode(2)
    node_4 = ListNode(4)
    head_1.next = node_2
    node_2.next = node_4

    head_2 = ListNode(1)
    node_3 = ListNode(3)
    node_4_copy = ListNode(4)
    head_2.next = node_3
    node_3.next = node_4_copy

    result = solution.mergeTwoLists(head_1, head_2)
    while result:
        print(result.val)
        result = result.next
```
