class Solution {
public:
    bool stoneGameIX(vector<int>& stones) {
        vector<int> cnt(3,0);
        int n=stones.size();
        for(int i=0;i<n;i++) cnt[stones[i]%3]++;
        if(min(cnt[1],cnt[2])==0) return max(cnt[1],cnt[2])>2 && cnt[0]%2>0;
        return abs(cnt[1]-cnt[2])>2 || cnt[0]%2==0;
    }
};
