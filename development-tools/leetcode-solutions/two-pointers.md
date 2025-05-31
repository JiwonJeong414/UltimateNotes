# Two Pointers

## Day 1

### Valid Palindrom

i represents the beginning of the string and j represents the end of the string. isalnum checks if its a alphanumeric character. .lower() converts the character into a lowercase character. We check i, j if it equals to each other and if it's not, return false. If it completes the while loop, return true.

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        i, j = 0, len(s) - 1

        while i < j:
            if not s[i].isalnum():
                i += 1
                continue

            if not s[j].isalnum():
                j -= 1
                continue 

            if s[i].lower() != s[j].lower():
                return False
            
            i += 1
            j -= 1

        return True
```

### Two Sum II - Input Array Is Sorted

Same pointers. if the arr[i] + arr[j] exceeds target j -= 1, if it is below i += 1

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        i, j = 0, len(numbers) - 1

        output = [] # output array

        while i < j:
            if numbers[i] + numbers[j] > target:
                j -= 1
            
            if numbers[i] + numbers[j] < target:
                i += 1
            
            if numbers[i] + numbers[j] == target:
                output.append(i + 1)
                output.append(j + 1)
                return output

        return output
```

### Three Sum

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        res = []
        nums.sort()

        for i, a in enumerate(nums):

            # we don't want to reuse the same value so we skip
            if i > 0 and a == nums[i - 1]:
                continue

            # Two pointers
            l, r = i + 1, len(nums) - 1
            while l < r:
                threeSum = a + nums[l] + nums[r]
                if threeSum > 0:
                    r -= 1
                elif threeSum < 0:
                    l += 1
                else:
                    res.append([a, nums[l], nums[r]])
                    # updating pointers
                    
                    # [-2, -2, 0, 0, 2, 2]
                    # we only have to update one pointer bc the two conditions up there will update the other
                    # simulate
                    l += 1
                    while nums[l] == nums[l - 1] and l < r:
                        l += 1
        
        return res
```