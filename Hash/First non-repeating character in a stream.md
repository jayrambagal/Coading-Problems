## First non-repeating character in a stream

Given an input stream of A of n characters consisting only of lower case alphabets. 

The task is to find the first non repeating character, each time a character is inserted to the stream. 

If there is no such character then append '#' to the answer.



## Example 
```bash
Input: A = "aabc"
Output: "a#bb"
Explanation: For every character first non
repeating character is as follow-
"a" - first non-repeating character is 'a'
"aa" - no non-repeating character so '#'
"aab" - first non-repeating character is 'b'
"aabc" - first non-repeating character is 'b'

```
```
Input: A = "zz"
Output: "z#"
Explanation: For every character first non
repeating character is as follow-
"z" - first non-repeating character is 'z'
"zz" - no non-repeating character so '#'

```

## Solution 

```python
from collections import deque
from collections import Counter

class Solution:
	def FirstNonRepeating(self, A):
	    
	    cnt = Counter()
	    q = deque()
	    ans = []
	    
	    for e in A:
	        cnt[e] += 1
	        q.append(e)
	        while q and cnt[q[0]] > 1:
	            q.popleft()
	        
	        ans.append(q[0] if q else '#')

	    return "".join(ans)  

```
## Solution 
```python
class Solution:
    # @param A : string
    # @return a strings
    def solve(self, A):
        n = len(A)
        
        freq = {}
        new_freq = {}
        ans = ""
        
        for i in range(n):
            
            if A[i] in freq:
                del freq[A[i]]
                new_freq[A[i]] = 1
            elif A[i] not in freq and A[i] not in new_freq:
                freq[A[i]] = 1
                
            if len(freq)!=0:
                for key,val in freq.items():
                    ans+=key
                    break
            else:
                ans+="#"
        return ans
```




## Geeksforgeeks
[First non-repeating character in a stream](https://practice.geeksforgeeks.org/problems/first-non-repeating-character-in-a-stream1216/1?page=1&difficulty[]=1&company[]=Amazon&company[]=Microsoft&category[]=Hash&sortBy=submissions)
