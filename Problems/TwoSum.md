## 题目地址
https://leetcode-cn.com/problems/two-sum

## 题目描述
```
给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。
```

### 示例:
```
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

## Solution

## Key

## Code
- **Language**: Python
- **Data**: 2020-05-23
```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """

        dic = {}  #dictionary
            #represents hash table (simple dictionary in this case). Its purpose is to store numbers mapped to their respective indices in the nums array which allows for direct lookup.
        for index,value in enumerate(nums):
            remaining = target - value
            if remaining not in dic: #check whether there is a key == remaining
                dic[value] = index
            else:
                return [dic[remaining],index]
```
- **难点**： 
    - dictionary

- **Note**: if >=2 same numbers in nums, there will be a runtime error: Solution either does not exist or is not unique
- 暴力搜索
  
``` python
        # Test: 29/29, but too slow
        for i in range(0,len(nums)):
            for j in range(0,len(nums)):
                if i != j and nums[i] + nums[j] == target:
                    return [i,j]
        return [-1]
```
