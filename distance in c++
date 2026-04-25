class Solution {
public:
    int maxDistance(int side, vector<vector<int>>& points, int k) {
        long long perimeter = 4LL * side;
        vector<long long> pos;

        // Convert boundary points into 1D perimeter positions
        for (auto& p : points) {
            int x = p[0];
            int y = p[1];

            if (y == 0) {
                pos.push_back(x); // bottom
            }
            else if (x == side) {
                pos.push_back(1LL * side + y); // right
            }
            else if (y == side) {
                pos.push_back(3LL * side - x); // top
            }
            else {
                pos.push_back(4LL * side - y); // left
            }
        }

        sort(pos.begin(), pos.end());
        int n = pos.size();

        // Duplicate for circular handling
        vector<long long> arr(2 * n);
        for (int i = 0; i < n; i++) {
            arr[i] = pos[i];
            arr[i + n] = pos[i] + perimeter;
        }

        long long left = 0, right = 2LL * side, ans = 0;

        while (left <= right) {
            long long mid = (left + right) / 2;

            if (canPick(arr, pos, k, mid, perimeter)) {
                ans = mid;
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return (int)ans;
    }

    bool canPick(vector<long long>& arr, vector<long long>& base,
                 int k, long long dist, long long perimeter) {
        int n = base.size();

        for (int start = 0; start < n; start++) {
            int count = 1;
            long long first = arr[start];
            long long last = first;
            int idx = start;

            while (count < k) {
                long long target = last + dist;

                auto it = lower_bound(
                    arr.begin() + idx + 1,
                    arr.begin() + start + n,
                    target
                );

                if (it == arr.begin() + start + n) {
                    break;
                }

                last = *it;
                idx = it - arr.begin();
                count++;
            }

            if (count == k) {
                long long gap = perimeter - (last - first);

                if (gap >= dist) {
                    return true;
                }
            }
        }

        return false;
    }
};
