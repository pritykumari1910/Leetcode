// Optimizations for faster execution (Beats 100%)
#pragma GCC optimize("O3,unroll-loops")
#pragma GCC target("avx2,bmi,bmi2,lzcnt,popcnt")

static const bool _ = []() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);
    return false;
}();

class Solution {
public:
    int minimumDeletions(string s) {
        int res = 0;
        int b_count = 0;
        
        // Iterate by reference to avoid unnecessary copying
        for (const char& c : s) {
            if (c == 'b') {
                b_count++;
            } else { 
                // Encountered 'a'
                // If there are preceding 'b's, we have a conflict ("ba")
                if (b_count > 0) {
                    res++;      // Delete one character to resolve conflict
                    b_count--;  // Decrease count of unmatched 'b's
                }
            }
        }
        
        return res;
    }
};
