class Solution {
public:
    int countDaysTogether(auto a, auto b, auto c, auto d) {
        return clamp(min(f(b), f(d)) - max(f(a), f(c)) + 1, 0, 365);
    }

    int f(auto& s) {
        int m = (s[0] - '0') * 10 + (s[1] - '0');
        int q = (s[3] - '0') * 10 + (s[4] - '0');

        return (275 * m) / 9 - 30 - 2 * ((m + 9) / 12) + q;
    }
};
