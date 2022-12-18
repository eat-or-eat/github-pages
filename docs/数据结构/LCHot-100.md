> 时间O(N)：
>
> 空间O(N)：

```python

```



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

#### [2. 两数相加](https://leetcode.cn/problems/add-two-numbers/?favorite=2cktkvj)

> 时间O(max(m,n)+1)：，遍历m或者n的链表完后，还可能会进位运行一次
>
> 空间O(1)：返回值不计入空间复杂度

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        head = result = ListNode(0)  # head用于添加结果，result用于返回结果
        carry = 0  # 进位标志符号
        while l1 or l2 or carry:  # 如果两个链表都遍历完了同时不存在进位才跳出
            # 获得链表的值
            num_l1 = l1.val if l1 else 0  
            num_l2 = l2.val if l2 else 0
            num_add = num_l1 + num_l2 + carry  # 计算位数相加和
            carry = 1 if num_add >= 10 else 0  # 更新进位值，大于9就为1
            head.next = ListNode(num_add % 10)  # 对10求余获得个位
            # 更新节点
            head = head.next
            l1 = l1.next if l1 else 0
            l2 = l2.next if l2 else 0
        return result.next  # 返回的是result.next因为原本的result是0
```

#### [3. 无重复字符的最长子串](https://leetcode.cn/problems/longest-substring-without-repeating-characters/?favorite=2cktkvj)

> 时间O(N)：每个元素遍历一次，一共N次
>
> 空间O(N)：substr最多存储N个元素。
>
> 遍历每个元素，如果碰到有重复的就在子串中去除，然后更新最大长度

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if not s: return 0

        n = len(s)
        left = 0  # 用于记录当前的左元素索引
        substr = set()
        max_len = 0
        cur_len = 0
        for i in range(n):
            cur_len += 1  # 每添加一个元素就加一
            while s[i] in substr:  # 剔除重复的部分
                substr.remove(s[left])
                left += 1
                cur_len -= 1
            if cur_len > max_len: max_len = cur_len  # 更新最大长度
            substr.add(s[i])  # 记录字串元素
        return max_len
```

#### [4. 寻找两个正序数组的中位数](https://leetcode.cn/problems/median-of-two-sorted-arrays/?favorite=2cktkvj)

> 时间O($nlog_n$)：[Timsort - Wikipedia](https://en.wikipedia.org/wiki/Timsort)
>
> 空间O(N)：合并后的列表有N个元素(num1+num2)

```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        num = nums1 + nums2  # 合并
        num = sorted(num)  # 排序
        n = len(num)
        if n % 2 == 0:  # 偶数 
            return (num[n//2] + num[n//2 - 1]) / 2
        else:
            return num[n//2]  # 基数
```