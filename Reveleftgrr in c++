int8_t dp[151];
class Solution {
public:
    array<int, 26> freq{};
    int n, half;
    int oddIdx=-1;
    bool revLeftIsGrR(const string& t){
        for(int i=0; i<half; i++){
            if (t[half-1-i]>t[half+(n&1)+i]) return 1;
            if (t[half-1-i]<t[half+(n&1)+i]) return 0;
        }
        return 0;
    }
    // Assume i < half
    bool canPlace(int i, const string& target, unsigned hasC) {
        if (dp[i]!=-1) return dp[i];
        const char c=target[i];
        if (freq[c-'a']==0) return 0;

        // Use 1 c
        unsigned hasC1=hasC;
        if (--freq[c-'a']==0) hasC1 &= ~(1<<(c-'a'));
        
        bool ans=0;
        if (i==half-1) {
            if (n&1) {
                if ('a'+oddIdx!=target[half]) 
                    ans=('a'+oddIdx > target[half]);
                else ans=revLeftIsGrR(target);
            } 
            else ans=revLeftIsGrR(target);
        } 
        else {
            int nxt=target[i+1]-'a';
            if (hasC1>>(nxt+1))
                ans=1;
            else if (!((hasC1>>nxt) & 1)) 
                ans=0;
            else 
                ans=canPlace(i+1, target, hasC1);
        }
        // Backtrack readd 1 c
        freq[c-'a']++;
        return dp[i]=ans;
    }
    inline string build_palindrome(const string& ans){
        string pal=ans;
         if (n&1) pal+='a'+oddIdx;
        string rev=ans;
        reverse(rev.begin(), rev.end());
        pal+=rev;
        return pal;
    }
    string lexPalindromicPermutation(string& s, string& target) {
        n=s.size(), half=n>>1;
        memset(dp, -1, half);
        unsigned par=0, hasC=0;
        for(char c : s){
            const int idx=c-'a';
            freq[idx]++;
            hasC|=1<<idx;
            par^=(1<<idx);
        }
        if (popcount(par)>1) return "";

        if (n&1) oddIdx=countr_zero(par);
        for(unsigned mask=hasC; mask; mask&=(mask-1)){
            int i=countr_zero(mask);
            freq[i]>>=1;
            // original oddIdx may freq=1
            if (freq[i]==0) hasC &=~(1u<<i);
        }

        string ans="";
        for (int i=0; i<half; i++) {
            int t_i=target[i]-'a';
            // Try to match target[i] if valid
            if (freq[t_i] > 0 && canPlace(i,target, hasC)) {
                ans+=target[i];
                if (--freq[t_i]==0) hasC &= ~(1u<<t_i); 
            } 
            else {
                // Use bitmask to find the min char>target[i]
                unsigned higher=hasC>>(t_i+1);
                if (higher==0) return "";
                int choice=countr_zero(higher)+t_i+1;
                if (--freq[choice]==0) hasC &= ~(1u<<choice);
                ans+='a'+ choice;

                //remaining positions  with smallest available characters
                for (int j=i+1; j<half; j++) {
                    int idx=countr_zero(hasC);
                    ans+='a'+idx;
                    if (--freq[idx]==0) hasC &=~(1u<<idx); 
                }
                return build_palindrome(ans);
            }
        }

        // Prefix up to half matches target[0...half-1]
        string pal=build_palindrome(ans);
        return pal>target ? pal : "";
    }
};
