## 题目地址
https://leetcode.com/problems/reverse-integer/

## 题目描述
```
Given a 32-bit signed integer, reverse digits of an integer.
```

### 示例:
```
Input: 123
Output: 321

Input: -123
Output: -321

Input: 120
Output: 21
```

### Note:
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: **[−2^31,  2^31 − 1]**. 
For the purpose of this problem, assume that your function returns **0** when the reversed integer overflows.


## Solution

## Key
- 1 --> 1, not 100
- -123 --> -321
- 9000000 --> 9
- 1534236469 --> 0 
  - Initial may be 32bit, but result not. Example from tests: 1534236469 --> 9646324351 (it's more than 2**31 and should be replace by 0).
        


## Code
- **Language**: Python
- **Data**: 2020-05-24
```python
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        
        if x >= -2**31 and x <= 2**31 -1:
            d = ''
            x2 = str(abs(x))
            
            for i in reversed(x2):
                d += i
            d =int(d)
            
            if d >= -2**31 and d <= 2**31 -1:
                if x < 0:
                    d = -1 * d
                return d 
            else:
                return 0        
        else:
            return 0
```

## Reference:
- **Language**: Python
``` python
def reverse(self, x):
    sign = [1,-1][x < 0]
    rst = sign * int(str(abs(x))[::-1])
    return rst if -(2**31)-1 < rst < 2**31 else 0
```
- **Note**:
  - ```sign = [1,-1][x < 0]``` is very smart!
    - [1,-1] is a list which has two elements, [x<0] is as a slice,when false is 0 ,when true is 1,so the express can get the emements
    - [1,-1] is an array. When x <0, it means we will pick #1 element of [1,-1], which is '-1'. Otherwise, when x >0, [x<0] will be false, which is 0. Then, we will pick #0 element of [1,-1], which is '+1'. It is a very tricky and smart way to solve for sign of an integer.
  - ```abs(x)``` gets absolute x, |x|
  - ```str(x)[::-1]``` transform the data type of variable x to ```str``` (make x a string), and **reverse** string x
    - a[::-1]相当于 a[-1:-len(a)-1:-1]，也就是从最后一个元素到第一个元素复制一遍，即倒序。
  - ```-(2**31)-1 < rst < 2**31``` 
