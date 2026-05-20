class Solution {
public:
    vector<int> findThePrefixCommonArray(vector<int>& A, vector<int>& B) {
        uint8_t sum = 0, k = 50;

        for (uint8_t i = 0; i < A.size(); i++) {
            uint8_t u = A[i] - (A[i] > k) * k - 1,
                    v = B[i] - 1;

            sum += A[u] > k;
            A[u] += (A[u] <= k) * k;

            sum += A[v] > k;
            A[v] += (A[v] <= k) * k;

            B[i] = sum;
        }

        return B;
    }
};
