class Solution {
public:
    int minimumSumSubarray(vector<int>& nums, int l, int r) {
        int n = nums.size();
        vector<int> prefix(n + 1, 0);
        for (int i = 0; i < n; i++) {
            prefix[i + 1] = prefix[i] + nums[i];
        }
        int best = INT_MAX;
        for (int j = l; j <= n; j++) {
            for (int len = l; len <= min(r, j); len++) {
                int sum = prefix[j] - prefix[j - len];
                if (sum > 0 && sum < best) {
                    best = sum;
                }
            }
        }
        return best == INT_MAX ? -1 : best;
    }
};
