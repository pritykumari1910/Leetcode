class Solution {
public:
    int totalFruit(vector<int>& fruits) {
        unordered_map<int,int>mpp;
        int l=0, r=0, basket1=-1, basket2=-1, maxfruit = 0;
        while(r<fruits.size()){
            if(basket1 == -1 || basket1 == fruits[r]){
                basket1 = fruits[r];
                mpp[fruits[r]]++;
            }
            else if(basket2 == -1 || basket2 == fruits[r]){
                basket2 = fruits[r];
                mpp[fruits[r]]++;
            }
            else{
                while(!mpp.empty() && mpp.size()>1){
                    mpp[fruits[l]]--;
                    if(mpp[fruits[l]] == 0){
                        if (fruits[l] == basket1) basket1 = -1;
                        if (fruits[l] == basket2) basket2 = -1;
                        mpp.erase(fruits[l]);
                    }
                    l++;    
                }
          
                if(basket1 == -1) basket1 = fruits[r];
                else basket2 = fruits[r];
                mpp[fruits[r]]++;
                
            }
            maxfruit = max(maxfruit, r-l+1);
            r++;
        }
        return maxfruit;
    }
};
