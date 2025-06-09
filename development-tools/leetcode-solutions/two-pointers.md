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

### Container With Most Water

Quite simple once you get hang of two pointers. We always compute area using the shorter height between the two pointers, because that’s the max height the water can go without spilling.

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        l, r = 0, len(height) - 1
        max_container = 0
        
        while (l != r):
            if height[l] > height[r]:
                container_size = (r - l) * height[r]
                if container_size > max_container:
                    max_container = container_size
                r -= 1
            else:
                container_size = (r - l) * height[l]
                if container_size > max_container:
                    max_container = container_size
                l += 1
                    
        return max_container
```

Time Complexity: O(n)

Space Complexity: O(1)

### Trapping Rain Water

I found this really hard. The initial approach to do this is to keep the prefix and suffix arrays.

Since we know that water at i is bounded by

min(max height to the left of i, max height to the right of i) - height[i]

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        n = len(height)
        if n == 0:
            return 0
        
        leftMax = [0] * n
        rightMax = [0] * n
        
        leftMax[0] = height[0]
        for i in range(1, n):
            leftMax[i] = max(leftMax[i - 1], height[i])
        
        rightMax[n - 1] = height[n - 1]
        for i in range(n - 2, -1, -1):
            rightMax[i] = max(rightMax[i + 1], height[i])
        
        res = 0
        for i in range(n):
            res += min(leftMax[i], rightMax[i]) - height[i]
        return res
```

we can create a leftMax array and rightMax array to store all the values;

However, there is an optimization
-->  We don't need to store arrays of leftMax/rightMax for every index. Since we’re sweeping inward from both sides and always using the smaller wall as the bounding height, we can calculate water trapped on the fly.




```python
class Solution:
    def trap(self, height: List[int]) -> int:
        l, r = 0, len(height) - 1

        leftMax = height[0]
        rightMax = height[-1]

        total = 0
        
        while l < r:
            if leftMax < rightMax:
                # Move left pointer
                l += 1
                leftMax = max(leftMax, height[l])
                total += leftMax - height[l]
            else:
                # move right pointer
                r -= 1
                rightMax = max(rightMax, height[r])
                total += rightMax - height[r]
        
        return total
```

Time Complexity: O(n)

Space Complexity: O(1)