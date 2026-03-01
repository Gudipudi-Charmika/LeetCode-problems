# LeetCode-problems
LEETCODE 1
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        n=len(nums)
        res=[]
        for i in range(n):
            for j in range(i+1,n):
                if (nums[i]+nums[j]==target):
                    res.append(i)
                    res.append(j)
        return res
LEETCODE 2
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        carry=0
        dummy_node=ListNode(0)
        curr=dummy_node
        while l1 and l2:
            val=l1.val+l2.val+carry
            carry=val//10
            val=val%10
            curr.next=ListNode(val)
            curr=curr.next
            l1=l1.next
            l2=l2.next
        while l1:
            if carry==1:
                val=l1.val+carry
                carry=val//10
                val=val%10
                curr.next=ListNode(val)
            else:
                curr.next=l1
            curr=curr.next
            l1=l1.next
        while l2:
            if carry==1:
                val=l2.val+carry
                carry=val//10
                val=val%10
                curr.next=ListNode(val)
            else:
                curr.next=l2
            curr=curr.next
            l2=l2.next
        if carry==1:
            curr.next=ListNode(carry)
        return dummy_node.next
LEETCODE 3
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        left=0
        ml=0
        chset=set()
        for r in range(len(s)):
            if s[r] not in chset:
                chset.add(s[r])
                ml=max(ml,r-left+1)
            else:
                while s[r] in chset:
                    chset.remove(s[left])
                    left+=1
                chset.add(s[r])
        return ml
LEETCODE 4
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        nums1.extend(nums2)
        nums1.sort()
        length=len(nums1)
        i=len(nums1)//2
        if len(nums1)%2!=0:
            return nums1[i]
        else:
            return (nums1[i]+nums1[i-1])/2.0
LEETCODE 7
class Solution:
    def reverse(self, x: int) -> int:
        rev=0
        n=x
        def dtob(n):
            res=""
            while n!=0:
                rem=n%2
                if rem==1:
                    res+="1"
                else:
                    res+="0"
                n=n//2
            return res[::-1]
        if x<0:
            x=-x
        while x!=0:
            r=x%10
            rev=rev*10+r
            x=x//10
        m=dtob(rev)
        if len(m)>=32:
            return 0
        elif n<0:
            return (-1*rev)
        return rev
LEETCODE 9
class Solution:
    def isPalindrome(self, x: int) -> bool:
        n=x
        rev=0
        if x<0:
            return False
        else:
            while x!=0:
                r=x%10
                rev=rev*10+r
                x=x//10
        if n==rev:
            return True
        else:
            return False
LEETCODE 26
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        if not nums:
            return 0
        i=0
        for j in range(1,len(nums)):
            if nums[j]!=nums[i]:
                i+=1
                nums[i]=nums[j]
        return i+1
LEETCODE 27
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        n=len(nums)
        c=0
        for i in range(n):
            if val!=nums[i]:
                nums[c]=nums[i]
                c+=1
        return c
LEETCODE 33
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        n=len(nums)
        for i in range(n):
            if nums[i]==target:
                return i
        return -1
        
LEETCODE 41
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        num_s=set(nums)
        i=1
        while True:
            if i not in num_s:
                return i
            i+=1
LEETCODE 43
class Solution:
    def multiply(self, num1: str, num2: str) -> str:
        num=0
        num3=0
        n=len(num1)
        if num1==0 or num2==0:
            return "0"
        else:
            for i in num1:
                num=num*10+(ord(i)-48)
            c=num
            p=len(num2)
            for i in num2:
                num3=num3*10+(ord(i)-48)
            q=num3
            m=c*q
            return str(m)
LEETCODE 50
