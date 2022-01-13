# 题目

| 给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。<br/><br/>你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。<br/><br/>你可以按任意顺序返回答案。<br/><br/> <br/><br/>示例 1：输入：nums = [2,7,11,15], target = 9<br/>输出：[0,1]<br/>解释：因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。<br/>示例 2：输入：nums = [3,2,4], target = 6<br/>输出：[1,2]<br/>示例 3：输入：nums = [3,3], target = 6<br/>输出：[0,1]<br/> 提示：<br/>2 <= nums.length <= 104<br/>-109 <= nums[i] <= 109<br/>-109 <= target <= 109<br/>只会存在一个有效答案<br/>进阶：你可以想出一个时间复杂度小于 O(n2) 的算法吗？<br/><br/>来源：力扣（LeetCode）<br/>链接：https://leetcode-cn.com/problems/two-sum |
| ------------------------------------------------------------ |



# 题解

```python
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int,int> mp1;
        map<int,int> mp2;
        map<map<int, int>, int> mp;
        int ans1, ans2;
        for(int i=0;i<nums.size();i++){
            mp1[nums[i]] = i;
            mp[mp1]=i;
            if(mp.find(mp1)!=mp.end()){
                mp2[target-nums[i]]=-1;
                if(mp.find(mp2)!=mp.end()){
                    if(mp[mp1]!=mp[mp2]){
                        ans1 = mp[mp1];
                        ans2 = mp[mp2];
                        break;
                    }
                }
            }
        }
        vector<int> ans;
        ans.push_back(ans1);
        ans.push_back(ans2);
        return ans;
    }
};
```

