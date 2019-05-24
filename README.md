# dodoro.github.io
dodoro的blog

### 3. Longest Substring Without Repeating Characters
Given a string, find the length of the longest substring without repeating characters.

Example 1:
```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```

Example 2:
```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```
Example 3:
```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

```
//c++

class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        unordered_map<char, int> offset;
        int left=0,right=0,maxlen=0;
        // string str='';//不用保存str,只需要长度即可
        int len=s.length();
        //从头遍历到尾部
        while(right<len){
            // cout<<s[right]<<endl;
            if(offset.count(s[right])){
                left=max(left, offset[s[right]] + 1);
            }
            offset[s[right]]=right;
            maxlen = max(maxlen, right - left + 1);
            ++right;
        }
        return maxlen;
    }
};
```
