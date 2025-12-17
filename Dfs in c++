class Solution {
public:
    int n, K;
    vector<int> prices;
    long long dp[1005][505][3];

    long long dfs(int i, int t, int state) {
        if (i == n) {
            return (state == 0 ? 0 : LLONG_MIN / 2);
        }

        if (dp[i][t][state] != -1)
            return dp[i][t][state];

        long long ans = dfs(i + 1, t, state);

        if (state == 0) {
            ans = max(ans, dfs(i + 1, t, 1) - prices[i]);
            ans = max(ans, dfs(i + 1, t, 2) + prices[i]);
        }
        else if (state == 1 && t < K) {
            ans = max(ans, dfs(i + 1, t + 1, 0) + prices[i]);
        }
        else if (state == 2 && t < K) {
            ans = max(ans, dfs(i + 1, t + 1, 0) - prices[i]);
        }

        return dp[i][t][state] = ans;
    }

    long long maximumProfit(vector<int>& prices, int k) {
        this->prices = prices;
        n = prices.size();
        K = k;

        memset(dp, -1, sizeof(dp));
        return dfs(0, 0, 0);
    }
};
