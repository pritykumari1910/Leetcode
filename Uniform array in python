class Solution:
    def uniformArray(self, nums1: list[int]) -> bool:
        
        min_odd = float("inf")
        min_even = float("inf")
        
        for value in nums1:

            if value % 2:
                min_odd = min(value,min_odd)
            else:
                min_even = min(value,min_even)

        return (min_even > min_odd) or min_even == float("inf") or min_odd == float("inf")
