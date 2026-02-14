double A[102];
class Solution {
public:
    double champagneTower(int poured, int query_row, int query_glass) {
        if (poured==0) return 0;
        memset(A, 0, (query_row+2)*sizeof(double));
        A[0]=poured;
        for(int i=0; i<query_row; i++){
            for(int j=i; j>=0; j--){
                double excess=max(0.0, (A[j]-1)/2.0);
                A[j]=excess;
                A[j+1]+=excess;
            }
        }
        return min(1.0, A[query_glass]);
    }
};
