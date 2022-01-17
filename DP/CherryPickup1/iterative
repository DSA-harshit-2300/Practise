class Solution {
public:
    
    //iterative dp
    
    int cherryPickup(vector<vector<int>>& grid) {
        
        
        // we need previous dp for step-1 and c1 c2 
        int n=grid.size();
        vector <vector <int>> prev(n+1,vector <int> (n+1,INT_MIN));
        
        if(n==0)return 0;
        
        if(grid[0][0]==-1)return 0;
        
        prev[0][0]=grid[0][0];
        
        int max_step=n+n-2;
        
        for(int steps=1;steps<=max_step;steps++){
            
            // for each step there are combination of row and col number
            // r1+c1=step c1=step-r1 r1 can max go upto steps
            // if step > n and r cannot be greater than n-1 i.e rmax is min of steps,n-1 and rmin if steps exeeds n-1 then eg steps=n and r==0 then c=n not possible therefore rmin = max(0,whats steps is ahead of n-1 i.e steps-n-1)
            
            vector <vector <int>> dp(n+1,vector <int> (n+1,INT_MIN));
            
            for(int r1=max(0,steps-(n-1));r1<=min(steps,n-1);r1++){
                for(int r2=max(0,steps-(n-1));r2<=min(steps,n-1);r2++){
                    
                    int c1=steps-r1;
                    int c2=steps-r2;
                    
                    if(grid[r1][c1]==-1 || grid[r2][c2]==-1){
                        continue;
                    }
                    
                    int cherries=0;
                    if(r1==r2){
                        cherries=grid[r1][c1];
                    }
                    else{
                        cherries+=grid[r1][c1]+grid[r2][c2];
                    }
                    
                    // 4 cases 
                    // case 1 UU
                    // case 2 UL
                    // case 3 LU
                    int a1,a2,a3,a4;
                    a1=a2=a3=a4=INT_MIN;
                    if(r1>0 && r2>0)
                    a1=prev[r1-1][r2-1];
                    if(r1>0 && c2>0)
                    a2=prev[r1-1][r2];
                    if(c1>0 && r2>0)
                    a3=prev[r1][r2-1];
                    if(c1>0 && c2>0)
                    a4=prev[r1][r2];
                    
                    dp[r1][r2]=max(max(a1,a2),max(a3,a4))+cherries;                    
                    
                }
            }           
            prev=dp;

        }
        return max(0,prev[n-1][n-1]);
    }
};
