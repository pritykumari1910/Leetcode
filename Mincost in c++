class Solution {
public:
    int minCost(int n, vector<vector<int>>& edges) {
        // Constructing adjacency matrix
        vector<vector<pair<int,int>>> adj(n);

        for(const auto& edge : edges){
            int u = edge[0];
            int v = edge[1];
            int cost = edge[2];

            // Forward edge
            adj[u].push_back({v, cost});
            // Backward edge
            adj[v].push_back({u, 2 * cost});
        }

        // Priority queue in ascending order of cost
        priority_queue<pair<int,int>, vector<pair<int,int>>, greater<pair<int,int>>> pq;

        // Dist array tracks min cost to each node from 0.
        vector<int> dist(n,INT_MAX);

        dist[0] = 0;
        pq.push({0,0});

        while(!pq.empty()){
            int d = pq.top().first; // distance
            int u = pq.top().second; // cost
            pq.pop();
            
            // if d > dist[u] it means d[u] is the shorter path to u found already so skip.
            if(d > dist[u]) continue;

            // else if u is n - 1, we found our answer, d is the cost.
            if(u == n - 1) return d;

            // for each node (B) that node u (A) goes has a edge to, update cost to that (B) node
            for(auto& edge : adj[u]){
                int v = edge.first;
                int weight = edge.second;
                // if cost(A) + weight < cost(B), update cost B.
                if(dist[u] + weight < dist[v]){
                    dist[v] = dist[u] + weight;
                    pq.push({dist[v],v});
                }
            }
        }
        // At last return -1.
        return -1;
    }
};
