constexpr int N=3e4;
int st[N], top=-1;
int dp[N];
class Solution {
public:
    static int longestValidParentheses(string& s) {
        const int n=s.size();
        if (n<2) return 0;
        top=-1;
        memset(dp, 0, n*sizeof(int));
       
        int ans=0;
        for(int i=0; i<n; i++){
            if (s[i]=='(') {
                st[++top]=i;
            }
            else{ //s[i]=')'
                if (top>=0){
                    int x=st[top--];
                    dp[i]=i-x+1;
                    if (x>=1) dp[i]+=dp[x-1];
                }
            }
            ans=max(ans, dp[i]);
        }
        return ans;
    }
};
