class Solution {
public:
    
    // new back track imagine linke two are going from same pos 
    
    int solve(int i1,int j1,int i2,int j2,vector <vector <int>> &grid,int n,vector <vector <vector <int>>> &dp){
        
        // base case if out of bound return INT_MIN
        
        if(i1>n || i2>n || j1>n || j2>n || grid[i1][j1]==-1 || grid[i2][j2]==-1)return INT_MIN;
        
        // can calculate j2 from i1 j1 i2 because i1+j1=i2+j2
        
        if(dp[i1][j1][i2]!=-1)return dp[i1][j1][i2];
        
        // 2*2 cases 2 robots ,1 down 2 down ,  1 right 2 down, 1 down 2 right , 1 right 2 right
        
        if(i1==n && j1==n){
            return grid[i1][j1];
        }
        
        int cherries=0;
        
        if(i1==i2 && j1==j2){
            cherries+=grid[i1][j1];
        }
        else{
            cherries+=grid[i1][j1]+grid[i2][j2];  
        } 
        
        
        int a1=solve(i1+1,j1,i2+1,j2,grid,n,dp);  // 1 down 2 down
        int a2=solve(i1+1,j1,i2,j2+1,grid,n,dp);  // 1 down 2 right
        int a3=solve(i1,j1+1,i2+1,j2,grid,n,dp);  // 1 right 2 down
        int a4=solve(i1,j1+1,i2,j2+1,grid,n,dp);  // 1 right 2 right
        
        
        return dp[i1][j1][i2]=(cherries+max(max(a1,a2),max(a3,a4)));
        
        // return max(max(a1,a2),max(a3,a4));
        
        
        
        
        
        
    }
    
    int cherryPickup(vector<vector<int>>& grid) {
        int n=grid.size();
        vector <vector <vector <int>>> dp(n+1,vector <vector <int>> (n+1,vector <int> (n+1,-1)));
        
        return max(0,solve(0,0,0,0,grid,n-1,dp));
        
    }
};
