# april7_2025
The problem that i solved today in leetcode

1.Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.

Code:
class Solution {
    public boolean f(int ind,int[] nums,int sum,int tot,int[][] dp)
    {
        if(ind==nums.length)
            return sum==tot;
        if(dp[ind][sum]!=-1)
            return dp[ind][sum]==1?true:false;
        boolean t=f(ind+1,nums,sum-nums[ind],tot+nums[ind],dp);
        boolean nt=f(ind+1,nums,sum,tot,dp);
        dp[ind][sum]=(t||nt)?1:0;
        return t||nt;
    }
    public boolean canPartition(int[] nums) {
        int n=nums.length;
        int sum=0;
        for(int x:nums)
            sum+=x;
        int[][] dp=new int[n][sum+1];
        for(int[] x:dp)
            Arrays.fill(x,-1);
        return f(0,nums,sum,0,dp);
    }
}
