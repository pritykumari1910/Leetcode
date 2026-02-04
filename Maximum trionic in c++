class Solution {
public:
    static long long maxSumTrionic(vector<int>& nums) {
        const int n=nums.size();
        //guaranteed that at least one trionic subarray exists.
        //if (n==4) return accumulate(nums.begin(), nums.end(), 0LL);

        long long ans=-1e15;
        for (int i=0, l=0, p=0, q=0, r=0; i<n-1; i+=i==l) {
            // Find start of first uphill
            while (i<n-1 && nums[i]>=nums[i+1]) i++;
            l=i;

            long long Sum=0;
            //Leg 1: Uphill
            while (i<n-1 && nums[i]<nums[i+1]) {
                Sum+=(nums[i]>0)?nums[i]:0;
                i++;
            }
            p=i;
            if (p==l||(p+1<n && nums[p]==nums[p+1])) 
                continue; 
            
            // nums[p-1] must be added to Sum
            Sum+=(nums[p-1]<0)?nums[p-1]:0;

            // Leg 2: Downhill
            while (i<n-1 && nums[i]>nums[i+1]) {
                Sum+=nums[i];// each one must be added to Sum
                i++;
            }
            q=i; 
            if (p==q||(q+1<n && nums[q]==nums[q+1])) 
                continue;

            // Leg 3: 2nd Uphill
            Sum+=nums[q]; // Valley is mandatory
            long long incr=0, maxIncr=INT_MIN;
            
            while (i<n-1 && nums[i]<nums[i+1]) {
                incr+=nums[i+1];
                maxIncr=max(maxIncr, incr);
                i++;
            }
            r=i;
            
            if (r>q) {
                ans=max(ans, Sum+maxIncr);
                // Backtrack to q, q=l
                i=q; 
            }
        }
        return ans;
    }
};
