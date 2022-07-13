# Merge-interval
Merge interval leetcode
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& inter) {
     vector<vector<int>>res;
       if(inter.size()==0){
           return res;
       } 
        sort(inter.begin(),inter.end(),[](vector<int>&a,vector<int>&b){
            return a[0]<b[0];
        });
        vector<int>current=inter[0];
        for(int i =1;i<inter.size();i++){
            if(current[1]<inter[i][0]){
                res.push_back(current);
                current=inter[i];
            }
            else{
                current[1]=max(current[1],inter[i][1]);
            }
        }
        
        res.push_back(current);
        return res;
    }
};
