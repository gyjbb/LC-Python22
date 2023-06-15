# LC-Python22

## 216.Combination Sum III, 17.Letter Combinations of a Phone Number

June 13, 2023  4h

Congratulations!\
This is the 22sh day for leetcode python study. Today we will learn more about backtracking!\
The challenges today are about ~~need to delete later~~.


## 216.Combination Sum III
[Reading link](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0216.%E7%BB%84%E5%90%88%E6%80%BB%E5%92%8CIII.md)\
[video](https://www.bilibili.com/video/BV1wg411873x/?spm_id_from=pageDriver&vd_source=63f26efad0d35bcbb0de794512ac21f3)\
[leetcode](https://leetcode.com/problems/combination-sum-iii/)\
Similar to the combination, here we have one more condition, the sum need to equal to the target given.
```python
class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        result = []    #save the result
        self.backtracking(n, k, 0, 1, [], result)
        return result

    def backtracking(self, targetSum, k, currentSum, startIndex, path,result):
        if currentSum > targetSum:      #cutting the branch
            return
        if len(path) == k:
            if currentSum == targetSum:
                result.append(path[:])
            return
        for i in range(startIndex, 9-(k-len(path))+2):      #cutting branch
            currentSum += i     #process the node
            path.append(i)      #process the node
            self.backtracking(targetSum, k, currentSum, i+1, path,result)
            currentSum -= i     #backtracking
            path.pop()      #backtracking
```


## 17.Letter Combinations of a Phone Number
[leetcode](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)\
Think first, then no idea :(\
The number of digits determines the depth of the tree, and 3 letters for each number determines the width of tree.\







