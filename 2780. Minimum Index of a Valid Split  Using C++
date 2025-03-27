class Solution {
public:
    int minimumIndex(vector<int>& nums) {
        auto find_dominant_element = [](const vector<int>& arr) {
            int candidate = -1, count = 0;
            
            // Boyer-Moore Majority Vote algorithm
            for (int num : arr) {
                if (count == 0) {
                    candidate = num;
                    count = 1;
                } else if (num == candidate) {
                    count++;
                } else {
                    count--;
                }
            }

            count = count_if(arr.begin(), arr.end(), [&](int num) { return num == candidate; });
            return (count > arr.size() / 2) ? candidate : -1;
        };

        int dominant = find_dominant_element(nums);
        if (dominant == -1) return -1;

        int left_count = 0, total_dominant_count = count(nums.begin(), nums.end(), dominant);
        
        for (int i = 0; i < nums.size() - 1; i++) {
            if (nums[i] == dominant) {
                left_count++;
            }

            int left_subarray_count = left_count;
            int right_subarray_count = total_dominant_count - left_count;

            if (left_subarray_count > (i + 1) / 2 && 
                right_subarray_count > (nums.size() - i - 1) / 2) {
                return i;
            }
        }

        return -1;
    }
};
