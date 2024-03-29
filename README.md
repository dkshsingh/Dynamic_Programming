[youtube]  https://lnkd.in/dNc2dzkd
# Dynamic_Programming
## How to identify DP problem?
#### 1. Where there is recursion (2 calls) , DP is used (for overlapping problem)
#### a) Choice 
#### b) Optimal
#### 2. How to write DP code?
#### Recursion --> Memoizataion --> Top_Down approach solution

## Questions on Dp
#### 1. knapsack (6)
#### 2. unbounded kanpsack (5)
#### 3. fibonacci (7)
#### 4. LCS (longest common subsequence) (15)
#### 5. LIS (longest increasing subsequence) (10)
#### 6. Kadane's Algorithm (16)
#### 7. Matrix chain multiplication (7)
#### 8. DP on trees (4)
#### 9. DP on grid (14)
#### 10. others (5)

## 1. Knapsack
## Types of knapsack
#### 1. Subset Sum
#### 2. Equal sum partition
#### 3. Count of subset sum
#### 4. Minimum subset difference
#### 5. Largest sum

## 0-1 knapsack problem :
- Fractional knapsack (Greedy)
- 0-1 knapsack 
- unbounded knapsack
## 0-1 knapsack :
#### some weight (wt[]), some values (val[]) and then a maximum weight (W).

### How to write knapsack code?
1. Return Max profit
2. Return int

### function
      int knapsack(int wt[],int val[],int w, int n)
      {
         #base condition   ---> think of the smallest valid integer
         #choice diagram
         }
      
     ***** Base condition :
                   if(n==0||w==0)
                   return 0              #if item = 0 then max profit = 0
      
     ****** choice diagram :
                 recursive func 
                 for(I/P) call----> for (smaller I/P)     example ----> fib(n) call--> fib(n-1)
                 
                 if item1 and w1
                 then w1<=w            #w1 is given value and w is knapsack
           code:
               if(wt[n-1]<=w)
               return(val[wt]+knapsack(wt[],value[],w1-wt[n-1])
      
  #### Recursive :
                  int knapsack(int w[], int val[], int w, int n)
                  {
                      if(n==0||w==0)
                      return 0
                  if(wt[n-1]<=w
                      return max(val(n-1_+knapsack[wt,val, w-wt(n-1), n-1)
                      knapsack(int, val, w, n-1);
                  else if(wt[n-1]>w)
                      return knapsack(wt, val, w, n-1);
  #### Memoization:
                 knapsack(wt[], val[], w, n)
                 int t[n+1][w+1]
                 memset(t, -1, sizeof(t)]
  #### knapsack DP code(memoization):
                  int static(t[102][1002]
                  memset(t,-1,sizeof[t])
                  *****base condition
                  int knapsack(int wt[], int val[], int w, int n)
                  {
                      if(n==0||w==0)
                          return 0
                      if(t[n][w] += -1)
                          return t[n][w]
                  *****choice diagram
                  if(wt[n-1]<=w)
                      return t[n][w]= max(val[n-1]+knapsack[wt,val,w-wt[n-1], n-1), knapsack(wt,val,w,n-1)
                      else if(wt[n-1]>w)
                      return t[n][w]=(knapsack[wt,val,w,n-1)         ------this changes recursive to dp
  
      
      
      
