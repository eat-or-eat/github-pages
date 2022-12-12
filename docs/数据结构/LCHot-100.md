#### [1. 两数之和](https://leetcode.cn/problems/two-sum/)

> 时间O(N)：遍历N个num
>
> 空间O(N)：一个哈希表随着N的数量增大
>
> 如果不用哈希表直接暴力搜索的话时间复杂度是$O(N^2)$，空间O(1)

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        dic = {}
        for i, num in enumerate(nums):
            aim = target - num
            if aim in dic:
                return [i,dic[aim]]
            else:
                dic[num] = i
```

