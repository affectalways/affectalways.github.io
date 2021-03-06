# 23 合并K个排序链表




合并 k 个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。

#### 示例:

```
输入:
[
  1->4->5,
  1->3->4,
  2->6
]
输出: 1->1->2->3->4->4->5->6
```

#### 暴力解法

```
遍历所有链表，将所有节点的值放到一个数组中。
将这个数组排序，然后遍历所有元素得到正确顺序的值。
用遍历得到的值，创建一个新的有序链表。
# -*- coding: utf-8 -*-
# @Time     : 2020/3/29 1:14
# @Author   : affectalways
# @Site     : 
# @Contact  : affectalways@gmail.com
# @File     : 23.py
# @Software : PyCharm 


# Definition for singly-linked list.
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None


class Solution:
    def mergeKLists(self, lists):
        # head = ListNode(-1)
        result = []
        for cur in lists:
            while cur:
                result.append(cur.val)
                cur = cur.next
        head = ListNode(-1)
        cur = head
        result.sort()
        for i in result:
            cur.next = ListNode(i)
            cur = cur.next

        return head.next


if __name__ == '__main__':
    solution = Solution()
    head_1 = ListNode(1)
    node_2 = ListNode(4)
    node_4 = ListNode(5)
    head_1.next = node_2
    node_2.next = node_4

    head_2 = ListNode(1)
    node_3 = ListNode(3)
    node_4_copy = ListNode(4)
    head_2.next = node_3
    node_3.next = node_4_copy

    head_3 = ListNode(2)
    node_6 = ListNode(6)
    head_3.next = node_6

    tmp = [head_1, head_2, head_3]
    result = solution.mergeKLists(tmp)
    while result:
        print(result.val)
        result = result.next
```
