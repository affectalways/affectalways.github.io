# 11 盛最多水的容器






```
给定 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。
说明：你不能倾斜容器，且 n 的值至少为 2。
```

![https://aliyun-lc-upload.oss-cn-hangzhou.aliyuncs.com/aliyun-lc-upload/uploads/2018/07/25/question_11.jpg](https://aliyun-lc-upload.oss-cn-hangzhou.aliyuncs.com/aliyun-lc-upload/uploads/2018/07/25/question_11.jpg?ynotemdtimestamp=1593701291427)

```
图中垂直线代表输入数组
[1,8,6,2,5,4,8,3,7]。在此情况下，容器能够容纳水（表示为蓝色部分）的最大值为 49。
```

##### 示例:

```
输入: [1,8,6,2,5,4,8,3,7]
输出: 49
class Solution:
    def maxArea(self, height):
        length = len(height)
        max = 0
        left_index = 0
        right_index = length - 1
        while left_index < right_index:
            area = min(height[left_index], height[right_index]) * (right_index - left_index)
            if max < area:
                max = area
            if height[left_index] < height[right_index]:
                while left_index < right_index:
                    if height[left_index] < height[left_index + 1]:
                        left_index = left_index + 1
                        break
                    else:
                        left_index = left_index + 1
            else:
                right_index = right_index - 1
                while right_index < left_index:
                    if height[right_index] < height[right_index - 1]:
                        right_index = right_index - 1
                        break
                    else:
                        right_index -= 1
        return max
"""
时间复杂度为O(n)， 空间复杂度为O(1)
思路：left、right游标分别从列表左右两端向中间靠拢
1、计算以left、right为左右游标的容量（取游标指向的值中较小的作为容器高度）
2、比较left、right两个游标指向值的大小，较小的往下一个位置移动，
否则随便选择一个游标下移，在本程序中固定选择右边的游标下移
3、重复步骤1 的计算，直到程序结束
"""
class Solution:
    def maxArea(self, height: list) -> int:
        max = 0
        left = 0
        right = len(height) - 1
        while left < right:
            l = left  #暂存左边游标的位置
            r = right  #暂存右边游标的位置
            if height[left] < height[right]:
                h = height[left]
                left += 1
            else:
                h = height[right]
                right -= 1
            tmp = h * (r - l)  #计算当前容器的容量
            max = tmp if tmp > max else max
        return max
```
