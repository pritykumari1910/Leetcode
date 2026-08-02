class Solution {
public:
    int count(int n, int m) {
        const int MOD = 1000000007;

        std::vector<std::vector<int>> divisors(m + 1);

        for (int d = 1; d <= m; d++) {
            for (int multiple = d; multiple <= m; multiple += d) {
                divisors[multiple].push_back(d);
            }
        }

        std::vector<std::vector<long long>> dp(n + 1,
                                               std::vector<long long>(m + 1, 0));

        for (int v = 1; v <= m; v++)
            dp[1][v] = 1;

        for (int len = 2; len <= n; len++) {
            for (int v = 1; v <= m; v++) {

                for (int d : divisors[v]) {
                    dp[len][v] = (dp[len][v] + dp[len - 1][d]) % MOD;
                }

                for (int mult = v; mult <= m; mult += v) {
                    dp[len][v] = (dp[len][v] + dp[len - 1][mult]) % MOD;
                }

                dp[len][v] = (dp[len][v] - dp[len - 1][v] + MOD) % MOD;
            }
        }

        long long ans = 0;
        for (int v = 1; v <= m; v++) {
            ans = (ans + dp[n][v]) % MOD;
        }

        return (int)ans;
    }
};
