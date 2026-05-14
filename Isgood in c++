class Solution {
public:
    bool isGood(vector<int>& nums) {
        const int n=nums.size()-1;
        if (n==0) return 0;
        int freq[201]={0};
        for(int x : nums){
            if (++freq[x]==2){
                if (x!=n) return 0;
            }
        }
        for(int x=1; x<=n-1; x++){
            if (freq[x]!=1) return 0;
        }
        return freq[n]==2;
    }
};
