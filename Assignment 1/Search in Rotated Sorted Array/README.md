#LEETCODE 33 : SEARCH IN ROTATED SORTED ARRAY SOLUTION:-

class Solution {
public:
    int searchArray(vector<int>& vec , int left , int right , int target){
        if(left > right) return -1;
        int mid = left + (right - left) / 2;
        if(vec[mid] == target) return mid;
        if(vec[left] <= vec[mid]){
        if(vec[left] <= target && target < vec[mid]){
            return searchArray(vec , left , mid - 1 , target);
        }
        else{
            return searchArray(vec , mid + 1 , right , target);
        }
            }
        else{
           if(vec[mid] < target && target <= vec[right])
                return searchArray(vec , mid + 1 , right , target);
        
        else{
            return searchArray(vec , left , mid - 1 , target);
        }
        }
        return -1;
    }
    int search(vector<int>& nums, int target) {
        return searchArray(nums,0 , nums.size() - 1, target);
    }
};
