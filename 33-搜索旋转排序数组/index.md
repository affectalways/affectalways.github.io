# 33 搜索旋转排序数组




```
搜索旋转排序数组假设按照升序排序的数组在预先未知的某个点上进行了旋转。

( 例如，数组 [0,1,2,4,5,6,7] 可能变为 [4,5,6,7,0,1,2] )。

搜索一个给定的目标值，如果数组中存在这个目标值，则返回它的索引，否则返回 -1 。

你可以假设数组中不存在重复的元素。

你的算法时间复杂度必须是 O(log n) 级别。
```

#### 示例 1:

```
输入: nums = [4,5,6,7,0,1,2], target = 0
输出: 4
```

#### 示例 2:

```
输入: nums = [4,5,6,7,0,1,2], target = 3
输出: -1
```

#### 解题思路：

```
题目要求 O(logN)O(logN) 的时间复杂度，基本可以断定本题是需要使用二分查找，怎么分是关键。
由于题目说数字了无重复，举个例子：
1 2 3 4 5 6 7 可以大致分为两类，
第一类 2 3 4 5 6 7 1 这种，也就是 nums[start] <= nums[mid]。此例子中就是 2 <= 5。
这种情况下，前半部分有序。因此如果 nums[start] <=target<nums[mid]，则在前半部分找，否则去后半部分找。
第二类 6 7 1 2 3 4 5 这种，也就是 nums[start] > nums[mid]。此例子中就是 6 > 2。
这种情况下，后半部分有序。因此如果 nums[mid] <target<=nums[end]，则在后半部分找，否则去前半部分找。

此题有个存在重复数字的变形题，可参考 此题解 。
```

#### 代码：

```
class Solution:
    def search(self, nums, target: int) -> int:
        if not nums:
            return -1
        if len(nums) == 1:
            if target in nums:
                return 0
            else:
                return -1
        length = len(nums)
        start = 0
        end = length - 1

        while start <= end:
            mid = start + (end - start) // 2
            if nums[mid] == target:
                return mid

            if nums[start] <= nums[mid]:
            #     前半部分有序
                if target >= nums[start] and target < nums[mid]:
                    end = mid - 1
                else:
                    start = mid + 1
            else:
                if target <= nums[end] and target > nums[mid]:
                    start = mid + 1
                else:
                    end = mid - 1
        return -1
```
