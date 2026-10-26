constexpr int N=1e5;
const int sz=1567;// ceil(N/64)
int Rt[N], Rk[N]; 
using u64=unsigned long long;
u64 Sum[N];

u64 Bitset[sz];
inline void Set(int x){
    Bitset[x>>6]|=(1ULL<<(x&63));
}
inline void Unset(int x){
    Bitset[x>>6]&=~(1ULL<<(x&63));
}

class UnionFind {
public:
    int n;
    int *root, *rank;

    UnionFind(int n) : n(n) {
        root=Rt;
        rank=Rk;
        iota(root, root+n, 0);
        memset(rank, 0, n*sizeof(int));
    }

    int Find(int x) {
        return root[x]==x ? x : root[x]=Find(root[x]);
    }

    bool Union(int x, int y) {
        x=Find(x), y=Find(y);
        if (x==y) return 0;

        if (rank[x]>rank[y]) swap(x, y);
        root[x]=y; 
        rank[y]+=(rank[x]==rank[y]);

        // Accumulate island sum directly into the new root
        Sum[y]+=Sum[x];
        Sum[x]=0;
        Unset(x);// unset xth bit in Bitset
        return 1;
    }
};

class Solution {
public:
    static inline int idx(int i, int j, int c) { return i*c+j; }

    static int countIslands(vector<vector<int>>& grid, int k) {
        const int r=grid.size(), c=grid[0].size(), n=r*c;
        const int q=(n+63)>>6;
        memset(Bitset, 0, q*sizeof(u64));
        for (int i=0; i<r; i++) {
            for (int j=0; j<c; j++) {
                const int x=grid[i][j], id=idx(i, j, c);
                Sum[id]=x;
                if (x>0) Set(id);
            }
        }
        UnionFind G(n);

        //Iterate through all cells and union adjacent land cells 
        for (int i=0; i<r; i++) {
            for (int j=0; j<c; j++) {
                if (grid[i][j]==0) continue;
                const int cur=idx(i, j, c);

                if (j+1<c && grid[i][j+1]>0) 
                    G.Union(cur, cur+1);

                if (i+1<r && grid[i+1][j]>0)
                    G.Union(cur, cur+c);
            }
        }

        // Count valid roots with island sum divisible by k
        int cnt=0;
        for(int i=0; i<q; i++){// mask iteration
            for (u64 mask=Bitset[i]; mask; mask&=(mask-1)) {
                const int cur=(i<<6)+__builtin_ctzll(mask);
                cnt+=(Sum[cur]%k==0);
            }
        }
        return cnt;
    }
};
auto init = []()
{ 
    ios::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);
    return 'c';
}();
