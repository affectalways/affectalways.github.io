# 02.02. 返回倒数第 k 个节点




#### [面试题 02.02. 返回倒数第 k 个节点](https://leetcode-cn.com/problems/kth-node-from-end-of-list-lcci/)



#### 实现一种算法，找出单向链表中倒数第 k 个节点。返回该节点的值。

注意：本题相对原题稍作改动

**示例：**

```
输入： 1->2->3->4->5 和 k = 2
输出： 4
说明：
```

给定的 k 保证是有效的。



**思路**

**经典的快慢指针问题**

```

反向思考，既然是寻找倒数第K个，那么计算机只能循环后移，不如我们先将位置确定，让其同步后移到链尾。
设置前后指针都先指向头结点，后指针先移动到第K个结点，那么前后指针此时相距K个位置。同步后移，当后指针指向链尾时，前指针就自然指向倒数第K个结点
```



```
class Solution(object):
    def kthToLast(self, head, k):
        """
        :type head: ListNode
        :type k: int
        :rtype: int
        """
        if head is None:
            return None

        left = head
        right = head
        count = 0
        while count < k:
            right = right.next
            count += 1
        while right:
            left = left.next
            right = right.next
        return left.val
```


