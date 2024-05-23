class Solution {
public:
    int solve(int i, int k, int n, vector<int> &nums, vector<int> &dp)
    {
        if (i == n)
        {
            return 0;
        }
        
        int o1 = 0, o2 = 0;
        o1 = solve(i + 1, k, n, nums, dp);
        if (binary_search(dp.begin(), dp.end(), nums[i] - k) == 0)
        {
            dp.push_back(nums[i]);
            o2 = 1 + solve(i + 1, k, n, nums, dp);
            dp.pop_back();
        }
    
        return o1 + o2;
    }
    int beautifulSubsets(vector<int>& nums, int k) {
        sort(nums.begin(), nums.end());
        
        int n = nums.size();
        vector<int> dp;
        return solve(0, k, n, nums, dp);
    }
};
