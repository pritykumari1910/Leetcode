class Solution {
public:
    static int minFlips(const string &s) {
        const uint n = s.length();
        uint p = 0, k = 0;
        for (const char c : s) {
            k += p ^ c & 1;
            p ^= 1;
        }
        uint r = min(k, n - k);
        if (n & 1) {
            p = 0;
            for (const char c : s) {
                k += (p ^ c & 1 ^ 1) - (p ^ c & 1);
                p ^= 1;
                r = min(r, min(k, n - k));
            }
        }
        return r;
    }
};
