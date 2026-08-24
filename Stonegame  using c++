class Solution {
public:
    static int stoneGameVIII(vector<int>& stones) {
        const int n=stones.size();
        partial_sum(stones.begin(), stones.end(), stones.begin());
        int dp=stones.back();
        for(int i=n-2; i>=1; i--){
            dp=max(dp, stones[i]-dp);
        }
        return dp;
    }
};

auto init = []() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);
    return 'c';
}();
