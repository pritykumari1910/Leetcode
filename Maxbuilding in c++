//translated using AI
class Solution {
public:
    int maxBuilding(int n, vector<vector<int>>& restrictions) {
        vector<vector<int>> arr;

        arr.push_back({1, 0});

        for (auto &r : restrictions) {
            arr.push_back(r);
        }

        sort(arr.begin(), arr.end());

        // Left to right pass
        for (int i = 1; i < arr.size(); i++) {
            int d = arr[i][0] - arr[i - 1][0];
            arr[i][1] = min(arr[i][1], arr[i - 1][1] + d);
        }

        // Right to left pass
        for (int i = arr.size() - 2; i >= 0; i--) {
            int d = arr[i + 1][0] - arr[i][0];
            arr[i][1] = min(arr[i][1], arr[i + 1][1] + d);
        }

        int ans = 0;

        for (int i = 1; i < arr.size(); i++) {
            int x1 = arr[i - 1][0];
            int h1 = arr[i - 1][1];

            int x2 = arr[i][0];
            int h2 = arr[i][1];

            int d = x2 - x1;

            ans = max(ans, (h1 + h2 + d) / 2);
        }

        int lastPos = arr.back()[0];
        int lastH = arr.back()[1];

        ans = max(ans, lastH + (n - lastPos));

        return ans;
    }
};
