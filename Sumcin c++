#include <bits/stdc++.h>
using namespace std;

struct Node {
    int cnt = 0;     // Sum of distinct counts in this segment
    int sq_cnt = 0;  // Sum of squares of distinct counts in this segment
    int lazy = 0;    // Pending addition for children
};

const int MOD = 1e9 + 7;
const int N = 1e5 + 1;
int last_seen[N];
Node tree[4 * N];

// Applies an addition of 'x' to all elements in the segment [st, end]
void apply(int node, int st, int end, int x) {
    int len = end - st + 1;
    
    // (a + x)^2 = a^2 + 2*a*x + x^2
    // Must update sq_cnt FIRST using the old cnt
    tree[node].sq_cnt = (0LL + tree[node].sq_cnt + 2LL * x * tree[node].cnt + 1LL * x * x % MOD * len) % MOD;
    
    // Update normal sum: sum(a + x) = sum(a) + len * x
    tree[node].cnt = (1LL * len * x + tree[node].cnt) % MOD;
    
    // Accumulate lazy tag for child nodes
    tree[node].lazy = (1LL * tree[node].lazy + x) % MOD;
}

// Pushes the pending lazy updates down to the left and right children
void lazyPropogation(int node, int st, int end) {
    if (tree[node].lazy == 0) return;
    int x = tree[node].lazy;
    int mid = st + (end - st) / 2;
    
    apply(2 * node, st, mid, x);
    apply(2 * node + 1, mid + 1, end, x);
    
    tree[node].lazy = 0; // Reset lazy tag after pushing down
}

// Combines results from left and right children into the parent node
void merge(int node, int left, int right) {
    tree[node].cnt = (0LL + tree[left].cnt + tree[right].cnt) % MOD;
    tree[node].sq_cnt = (0LL + tree[left].sq_cnt + tree[right].sq_cnt) % MOD;
}

// Range update: adds 1 to all elements in the query range [ql, qr]
void update(int node, int st, int end, int ql, int qr) {
    // 1. No overlap
    if (qr < st || end < ql) return;
    
    // 2. Complete overlap
    if (ql <= st && end <= qr) {
        apply(node, st, end, 1);
        return;
    }

    // 3. Partial overlap: push lazy values down and recurse
    lazyPropogation(node, st, end);
    int mid = st + (end - st) / 2;
    update(2 * node, st, mid, ql, qr);
    update(2 * node + 1, mid + 1, end, ql, qr);
    merge(node, 2 * node, 2 * node + 1);
}

class Solution {
public:
    int sumCounts(vector<int>& nums) {
        int n = nums.size(), ans = 0;
        
        // Reset segment tree and last_seen array for the current test case
        fill(tree, tree + 4 * n + 1, Node());
        memset(last_seen, -1, sizeof(last_seen));

        for (int i = 0; i < n; i++) {
            // Subarrays starting from 'st' to 'i' get a new distinct element
            int st = (last_seen[nums[i]] == -1 ? 0 : last_seen[nums[i]] + 1);
            last_seen[nums[i]] = i;
            
            // Add 1 to the distinct count of all subarrays starting in [st, i]
            update(1, 0, n - 1, st, i);
            
            // tree[1].sq_cnt holds the sum of squares for all subarrays ending at 'i'
            ans = (1LL * tree[1].sq_cnt + ans) % MOD;
        }

        return ans;
    }
};
