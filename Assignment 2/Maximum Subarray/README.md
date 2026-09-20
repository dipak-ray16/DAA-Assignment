#LEETCODE 53 : MAXIMUM SUBARRAY SOLUTION : 

class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        // kadane algorithmn
        int cursum = 0;
        int maxsum = 0;
        for( int x : nums){
            cursum += x;
            maxsum = max(maxsum , cursum);
            if(cursum < 0) cursum =0;
        }
        return maxsum;
    }
};
