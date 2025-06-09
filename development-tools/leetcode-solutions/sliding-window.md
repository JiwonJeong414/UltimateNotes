# Sliding Window

## Day 1

### Sliding Window: Best Time to Buy and Sell

Two Pointers solution. Start at 0, 1 indexes if right is smaller than left, move left to right. Since left and right are the same after moving left to right one, then move right again. Else, move right once.

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        i, j = 0, 1
        
        if len(prices) < 1:
            return 0
        
        if len(prices) == 2:
            return max(0, prices[1] - prices[0])

        maxSum = 0

        while j < len(prices):
            
            if prices[j] - prices[i] > maxSum:
                maxSum = prices[j] - prices[i]

            # if right is less than left, update pointer left
            if prices[j] < prices[i]:
                i = j
                # if equal move right one more
                if i == j:
                    j += 1
            else:
                j += 1
            

        return maxSum 
```

Time Complexity: O(n)

Space Complexity: O(1)

### Longest Substring Without Repeating Characters

Have left and right pointers. We increment right if we add existing characters to the hashset and it doesn't exist in the hashset. We track the maxLength by checking if j-i is greater everytime we increment j. If we do find a duplicate, we use a while loop until we got rid of that duplicate in the hashset by incrementing i and when we do we add the current one that we are in (that we were blocked by bc of previous duplicate in the front but now we got rid of bc of going through i) and then keep incrementing j.

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if not s:  # handle empty string
            return 0
        if len(s) == 1:  # handle single character
            return 1

        i, j = 0, 1

        maxLength = 1
        hashSet = set()
        hashSet.add(s[i])

        while j < len(s):
            if s[j] not in hashSet:
                hashSet.add(s[j])
                j += 1
                maxLength = max(maxLength, j - i)
            else:
                while s[j] in hashSet:  # while we haven't removed the duplicate
                    hashSet.remove(s[i])  # remove the leftmost character
                    i += 1
                hashSet.add(s[j])
                j += 1

        return maxLength
```

Time Complexity: O(n)

Space Complexity: O(m)

Where n is the length of the string and m is the total number of unique characters in the string.

### Longest Repeating Character Replacement

Have left (i) and right (j) pointers. We increment j if the window length minus the most frequent character count is less than or equal to k. We track the maxLength by checking if j-i+1 is greater every time we expand the window. If we find that window length minus most frequent count is greater than k, we shrink the window by incrementing i and removing characters from the hashMap until the condition is met again. Then we continue expanding the window by incrementing j.
 

```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        if len(s) == 1:  # handle single character
            return 1

        i, j = 0, 0

        maxLength = 1
        hashMap = {}
        hashMap[s[i]] = hashMap.get(s[i], 0) + 1

        while j < len(s):
            window_frequent = j - i + 1 - max(hashMap.values()) 

            # If (window length - most frequent count) <= k, we are fine
            if window_frequent <= k:
                maxLength = max(maxLength, j - i + 1)          
                j += 1
                if j < len(s):
                    hashMap[s[j]] = hashMap.get(s[j], 0) + 1

            # If not, loop it until the condition holds
            else:
                hashMap[s[i]] = hashMap.get(s[i]) - 1
                i += 1

        return maxLength
```

Time Complexity: O(n)

Space Complexity: O(m)

Where n is the length of the string and m is the total number of unique characters in the string.