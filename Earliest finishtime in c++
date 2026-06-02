class Solution {
public:
    static int earliestFinishTime(vector<int>& landStartTime, vector<int>& landDuration, vector<int>& waterStartTime, vector<int>& waterDuration) {
        const int n=landStartTime.size(), m=waterStartTime.size();
        int minLandEnd=1e6, minWaterEnd=1e6;
        for(int i=0; i<n; i++) 
            minLandEnd=min(minLandEnd, landStartTime[i]+landDuration[i]);
        for(int i=0; i<m; i++) 
            minWaterEnd=min(minWaterEnd, waterStartTime[i]+waterDuration[i]);
        int ans=1e9;
        for(int i=0; i<m; i++){
            if (waterStartTime[i]<minLandEnd) 
                ans=min(ans, minLandEnd+waterDuration[i]);
            else ans=min(ans,  waterStartTime[i]+waterDuration[i]);
        }
        for(int i=0; i<n; i++){
            if (landStartTime[i]<minWaterEnd)
                ans=min(ans, minWaterEnd+landDuration[i]);
            else ans=min(ans,  landStartTime[i]+landDuration[i]);
        }
        return ans;
    }
};
