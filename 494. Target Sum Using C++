class Solution {
public:
    int n;
    int range;
    vector<vector<int>> dp;
    int F(int i, int sum, vector<int>& A, int t) {
        if (i >= n) {
            return sum == t;
        }
        if (dp[i][sum + range] != -1) {
            return dp[i][sum + range];
        }
        int takePositive = F(i + 1, sum + A[i], A, t);
        int takeNegative = F(i + 1, sum - A[i], A, t);
        return dp[i][sum + range] = takePositive + takeNegative;
    }
    int findTargetSumWays(vector<int>& A, int target) {
        n = A.size();
        int totalSum = accumulate(A.begin(), A.end(), 0);
        range = totalSum;
        dp.resize(n , vector<int> (2*totalSum + 1 , -1));
        return F(0, 0, A, target);
    }
};
