# 24 两两交换链表中的节点






```
给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。

你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。
```

#### 示例:

```
给定 1->2->3->4, 你应该返回 2->1->4->3.
# -*- coding: utf-8 -*-
# @Time     : 2020/3/29 14:34
# @Author   : affectalways
# @Site     : 
# @Contact  : affectalways@gmail.com
# @File     : 24.py
# @Software : PyCharm 

class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None


class Solution:
    def swapPairs(self, head):
        cur = head
        if cur is None or cur.next is None:
            return cur

        tmp = list()
        while cur:
            tmp.append(cur)
            cur = cur.next

        pre = ListNode(None)
        cur = pre
        length = len(tmp)
        final_node = None
        if length % 2 == 1:
            final_node = tmp[-1]
        for node_index in range(1, length, 2):
            cur.next = tmp[node_index]
            cur = cur.next
            cur.next = tmp[node_index - 1]
            cur = cur.next
        cur.next = final_node
        return pre.next


if __name__ == '__main__':
    solution = Solution()
    head_1 = ListNode(1)
    node_2 = ListNode(2)
    node_3 = ListNode(3)
    node_4 = ListNode(4)
    head_1.next = node_2
    node_2.next = node_3
    node_3.next = node_4
    result = solution.swapPairs(head_1)

    while result:
        print(result.val)
        result = result.next
```
