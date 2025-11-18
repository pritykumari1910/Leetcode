class Solution {
public:
    bool isOneBitCharacter(vector<int>& bits) { 
        bits.pop_back(); // remove guaranteed last 0
        int n = bits.size();

        // short-circuit: empty or last remaining bit is 0
        if (n == 0 || bits.back() == 0) return true;

        int i = 0;
        while (i < n - 1)
            i += bits[i] + 1;

        return i == n;
    }
};
