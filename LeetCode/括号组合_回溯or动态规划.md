数字 `n` 代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 **有效的** 括号组合。

**示例 1：**

```
输入：n = 3
输出：["((()))","(()())","(())()","()(())","()()()"]
```

**示例 2：**

```
输入：n = 1
输出：["()"]
```

**solution**

```c++
/* 回溯法 */
/*
如果左括号数量不大于 nn，我们可以放一个左括号。如果右括号数量小于左括号的数量，我们可以放一个右括号。
*/
class Solution {
public:
    void dfs(vector<string>& ans, string cur, int left, int right, int n){
        if(cur.size()==2*n){
            ans.push_back(cur);
            return;
        }
        if(left<n){
            cur += '(';
            dfs(ans, cur, left+1, right, n);
            cur.pop_back();
        }
        if(right<left){
            cur += ')';
            dfs(ans, cur, left, right+1, n);
            cur.pop_back();
        }
    }
    
    vector<string> generateParenthesis(int n) {
        vector<string>ans;
        string cur = "";
        dfs(ans, cur, 0, 0, n);

        return ans;
    }
};


/* 动态规划 */
/*
既然知道了 i<n 的情况，那我们就可以对所有情况进行遍历：

"(" + 【i=p时所有括号的排列组合】 + ")" + 【i=q时所有括号的排列组合】

其中 p + q = n-1，且 p q 均为非负整数。
*/
class Solution {
public:
	vector<string> generateParenthesis(int n) {
		if (n == 0) return {};
		if (n == 1) return { "()" };
		vector<vector<string>> dp(n+1);
		dp[0] = { "" };
		dp[1] = { "()" };
		for (int i = 2; i <= n; i++) {
			for (int j = 0; j <i; j++) {
				for (string p : dp[j])
					for (string q : dp[i - j - 1]) {
						string str = "(" + p + ")" + q;
						dp[i].push_back(str);
					}
			}
		}
		return dp[n];
	}
};
```

