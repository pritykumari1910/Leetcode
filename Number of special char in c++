class Solution {
public:
    static int numberOfSpecialChars(string& word) {
        bitset<27> A[2];
        for(char c: word){
            bool isLower=c&32;
            A[isLower][31&c]=1;
        }
        return (A[0]&A[1]).count();
    }
};
