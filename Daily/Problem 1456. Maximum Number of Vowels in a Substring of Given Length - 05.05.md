# 1456. Maximum Number of Vowels in a Substring of Given Length

## Python Code:
```shell
class Solution:
    def maxVowels(self, s: str, k: int) -> int:
        def vow(n):
            return n=='a' or n=='e' or n=='i' or n=='o' or n=='u'
        ans=0
        for i in range(k):
            if vow(s[i]):
                ans+=1
        m_ans=ans
        for i in range(k,len(s),1):
            if vow(s[i-k]):ans-=1
            if vow(s[i]):ans+=1
            m_ans=max(ans,m_ans)
        return m_ans
```

