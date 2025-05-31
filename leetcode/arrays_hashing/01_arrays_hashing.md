# Arrays & Hashing

## Day 1

### Contains Duplicate
I did it in python3. As soon as I heard unique identifier in the list, I thought of **HashSet**. Since HashSet keeps track of unique items, I just needed to compare the added unique items to the original nums array. Simply, I just checked when I added an item to a HashSet if the item existed in the set. The in operation in a set takes O(1) operation time, since we iterated through all the items in lists, the time complexity is O(n). Since we used a HashSet to store all of it, the space complexity is O(n)

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        mySet = set()
        for i in range(len(nums)):
            if nums[i] not in mySet:
                mySet.add(nums[i])
            else:
                return True
        return False
```

**Time Complexity:** O(n)  
**Space Complexity:** O(n)

### Valid Anagram
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # map each alphabet with a cnt integer for s
        sMap = defaultdict(int)
        for i in range(len(s)):
            sMap[s[i]] += 1

        # do the same for t
        tMap = defaultdict(int)
        for i in range(len(t)):
            tMap[t[i]] += 1

        # check if the two HashMap is the same
        return sMap == tMap
```

**Time Complexity:** O(n)  
**Space Complexity:** 3O(n) = O(n)

### Two Sum
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        # Create a hashmap to store number -> index
        numMap = {}
        
        # One pass through the array
        for i, num in enumerate(nums):
            # find the complement and check if that exists in the HashMap
            complement = target - num
            if complement in numMap:
                return [numMap[complement], i]
            # add it to the dict if the complement of the thing doesn't exist
            numMap[num] = i
            
        return []  # No solution found
```

**Time Complexity:** O(n)  
**Space Complexity:** O(n)

## Day 2

### Group Anagrams
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        # sorted(word) as key and the value as lists of indexes of the 
        # original array that had the same sorted array
        myMap = defaultdict(list)
        for i, word in enumerate(strs):
            # but then a list is not hashable so use a tuple
            myMap[tuple(sorted(word))].append(i)

        # make the outer array and made the inner arrays blank
        arr = [[] for _ in range(len(myMap))]

        # I just appended all the original values into the list of lists
        cnt = 0
        for key in myMap:
            retrieve = myMap[key]
            for index in retrieve:
                arr[cnt].append(strs[index])
            cnt += 1
        
        return arr
```

optimized version:
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        map = defaultdict(list)
        for word in strs:
            finalWord = ''
            for key in sorted(word):
                finalWord+=key
            map[finalWord].append(word)
        return list(map.values()) # key function I didn't know about, you can return list of values
```

**Time Complexity:** O(n * k * log k)
- n is number of strings
- k is length of longest string
- Dominated by sorting each string (k log k) done n times

**Space Complexity:** O(n * k)
- n is number of strings
- k is length of longest string
- Need to store all strings in both map and result array

### Top K Frequent Elements

**BUCKET SORT**

Bucket sort is a sorting algorithm that works by distributing elements into a number of buckets, then sorting each bucket individually. It's particularly useful when the input is uniformly distributed over a range.

### How it Works:
1. Create n empty buckets
2. Put each element in its corresponding bucket
3. Sort each bucket individually
4. Concatenate all buckets

### Data Structure:
an array of arrays (just like the implementation of a HashMap)

For this question, I first used a sorting method where I populated the hashMap with keys as the num values and the value as the frequency of that certain num value happening in that nums array. And then I used a complex lambda function to grab the top k elements using the only the frequencies as the reference. However, this solution is O(n log n) which is not optimal.

Therefore, we use a bucket sort. Since we know that the frequencies for a certain value cannot exceed the length of the nums array, we create a bucket and each index represents the frequencies of a certain number. And in that index, we store a list of all the numbers that have that specific frequency. Then, we decrement from the top and grab the top k elements, ignoring the empty lists.

### Sorting
```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        myMap = defaultdict(int)
        for values in nums:
            myMap[values] += 1
        
        return [kv[0] for kv in sorted(myMap.items(), key=lambda kv: kv[1])][-k:]
```

**Time Complexity:** O(n log n)  
**Space Complexity:** O(n)

### Bucket Sort
```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        # bucketsort
        arr = [] # first I make the buckets with an empty array containing each index 
        for _ in range(len(nums) + 1):
            arr.append([])
        
        # I make a hashMap to store all the values in nums as keys and its frequency as the value
        myMap = defaultdict(int)
        for values in nums:
            myMap[values] += 1
        
        # I populate the array (buckets) with the keys corresponding to the value index 
        for key in myMap:
            arr[myMap[key]].append(key)
            
        # I grab the top k elements by going through all of the array from end index (used a while loop)
        output = []
        cnt = k
        arrCnt = len(nums)
        while cnt > 0:
            if arr[arrCnt]:  # Check if list is not empty
                for num in arr[arrCnt]:  # Iterate through the list
                    output.append(num)
                    cnt -= 1
                    if cnt == 0:
                        break
            arrCnt -= 1  # Move to next frequency
            
        return output
```

**Time Complexity:** O(n)  
**Space Complexity:** O(n)

### Encode and Decode Strings
A delimiter is a indicator that separates words from each other. I first thought of the input of why can't we just indicate the words from just each length such as 3word4make something like that but I soon realize if the word goes double digit, it will be impossible to see if the word includes the next digit such as 2we3say1:3yes10!@#$%^&*(). Here we don't know if it's a 1 or a 10. Therefore we need a delimter to indicate that a new word is starting. In my case, I chose a "#". The number left to it indicates the length of the word, the symbols to the right of it indicates the word itself.

```python
class Solution:
    def encode(self, strs: List[str]) -> str:
        output = ""
        for words in strs:
            output += str(len(words)) + "#" + words  # Add delimiter
        return output

    def decode(self, s: str) -> List[str]:
        original = []
        i = 0
        while i < len(s):
            j = s.find('#', i) # Find '#' starting from position i
            length = int(s[i:j]) # get the length
            original.append(s[j + 1: j + 1 + length]) # append the word
            i = j + 1 + length # move the i
        return original
```

**Time Complexity:** O(n)  
**Space Complexity:** O(n)

## Day 3

### Products of Array Except Self
* First pass (prefix): For each position, we store the product of all numbers to the left
* Second pass (suffix): We multiply each position by the product of all numbers to the right

```python
def productExceptSelf(nums: List[int]) -> List[int]:
    n = len(nums)
    output = [1] * n
    
    # Calculate prefix products
    prefix = 1
    for i in range(n):
        output[i] = prefix
        prefix *= nums[i]
    
    # Calculate suffix products and combine with prefix
    suffix = 1
    for i in range(n-1, -1, -1):
        output[i] *= suffix
        suffix *= nums[i]
    
    return output
```

![Prefix Product Visualization](./assets/prefix.png)

**Time Complexity:** O(n)  
**Space Complexity:** O(n)

### Valid Sudoku
Map keys into valid row, column, and box key into a single hashMap

```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        myMap = defaultdict(set)

        for i in range(9):
            for j in range(9):
                if board[i][j] == ".": # Skip unfilled cells
                    continue

                # Create tuple keys for row, column, and box
                row_key = (i, -1)
                column_key = (-1, j)
                box_key = (i // 3, j //3) # this maps to corresponding box as 0, 0 or 1, 1

                # Check if number exists in row, column, or box
                if board[i][j] in myMap[row_key]:
                    return False
                if board[i][j] in myMap[column_key]:
                    return False
                if board[i][j] in myMap[box_key]:
                    return False

                # Add number to corresponding sets
                myMap[row_key].add(board[i][j])
                myMap[column_key].add(board[i][j])
                myMap[box_key].add(board[i][j])

        return True
```

**Time Complexity:** O(9 * 9)  
**Space Complexity:** O(9 * 9)

### Longest Consecutive Sequence
```python
def longestConsecutive(nums: List[int]) -> int:
    mp = defaultdict(int)  # Map to store length of consecutive sequence for each number
    res = 0  # Track the maximum length found

    for num in nums:
        # Only process if we haven't seen this number before
        if not mp[num]:
            # Get the length of consecutive sequences on both sides
            # mp[num-1] gives length of sequence ending at num-1
            # mp[num+1] gives length of sequence starting at num+1
            # Add 1 for the current number
            mp[num] = mp[num - 1] + mp[num + 1] + 1
            
            # Update the length at the start of the sequence
            # num - mp[num-1] is the start of the left sequence
            mp[num - mp[num - 1]] = mp[num]
            
            # Update the length at the end of the sequence
            # num + mp[num+1] is the end of the right sequence
            mp[num + mp[num + 1]] = mp[num]
            
            # Update the maximum length if needed
            res = max(res, mp[num])
    
    return res
```

**Time Complexity:** O(n)  
**Space Complexity:** O(n) 