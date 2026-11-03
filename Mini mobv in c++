class Solution {
public:
    long long minMoves(vector<int>& nums) {
        int mx = *max_element(nums.begin(), nums.end());
        long long res = 0;
        for (int x : nums) {
            res += (mx - x);
        }
        return res;
    }
};
