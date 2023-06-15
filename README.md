# LC-Python22

## 216.Combination Sum III, 17.Letter Combinations of a Phone Number

June 13, 2023  4h

Congratulations!\
This is the 22sh day for leetcode python study. Today we will learn more about backtracking!\
The challenges today are about using backtracking as a kind of loop solution. For each loop, the number of possible choices of elements /size of one set defines the width of the tree, and the number of loops we need to have/k defines the depth of the tree, we use recursion to simplify the multiple loops. Don't forget the backtracking process followed!


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
The solutiion below is so cool and definitely worth reviewing again!
```python
class Solution:
    def __init__(self):
        self.letterMap = [
            "",     #0
            "",     #1
            "abc",     #2
            "def",     #3
            "ghi",     #4
            "jkl",     #5
            "mno",     #6
            "pqrs",     #7
            "tuv",     #8
            "wxyz"     #9
        ]
        self.result = []    #define a global variable to store all results
        self.s = ""     #define a global variable to store each string

    def backtracking(self, digits, index):
        if index == len(digits):
            self.result.append(self.s)
            return
        digit = int(digits[index])     #change number in digits from string input to real number
        letters = self.letterMap[digit]     #get the corresbonding letters for this digit
        for i in range(len(letters)):
            self.s += letters[i]        #add the letter to result string
            self.backtracking(digits, index+1)      #recursion, deal with the next number given in the digits
            self.s = self.s[:-1]    #backtracking, delete the last item added to the result string

    def letterCombinations(self, digits: str) -> List[str]:
        if len(digits) == 0:
            return self.result
        self.backtracking(digits, 0)
        return self.result
```







