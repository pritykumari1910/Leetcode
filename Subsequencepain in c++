class Solution {
public:
    int subsequencePairCount(vector<int>& nums) {
        int m = *max_element(nums.begin(), nums.end()), mod = 1e9 + 7;
        vector<vector<int>> dp(m + 1, vector<int>(m + 1, 0));
        dp[0][0] = 1;

        for (int x : nums) {
            auto next_dp = dp;
            for (int g1 = 0; g1 <= m; ++g1) {
                for (int g2 = 0; g2 <= m; ++g2) {
                    if (!dp[g1][g2]) continue;
                    int n1 = gcd(g1, x), n2 = gcd(g2, x);
                    next_dp[n1][g2] = (next_dp[n1][g2] + dp[g1][g2]) % mod;
                    next_dp[g1][n2] = (next_dp[g1][n2] + dp[g1][g2]) % mod;
                }
            }
            dp = move(next_dp);
        }

        long long ans = 0;
        for (int g = 1; g <= m; ++g)
            ans = (ans + dp[g][g]) % mod;
        return ans;
    }
};
