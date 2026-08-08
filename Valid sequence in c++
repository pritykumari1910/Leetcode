class Solution {
public:
    vector<int> validSequence(string word1, string word2) {
        int n = word1.size(), m = word2.size();
        vector<int> suf(n + 1, 0);
        for (int i = n - 1, j = m - 1; i >= 0; --i) {
            suf[i] = suf[i + 1];
            if (j >= 0 && word1[i] == word2[j]) {
                ++suf[i];
                --j;
            }
        }
        vector<int> res;
        res.reserve(m);
        int budget = 1;
        for (int i = 0; i < n && (int)res.size() < m; ++i) {
            if (word1[i] == word2[res.size()])
                res.push_back(i);
            else if (budget && (int)res.size() + budget + suf[i + 1] >= m) {
                --budget;
                res.push_back(i);
            }
        }
        return (int)res.size() == m ? res : vector<int>();
    }
};
