#LEETCODE 912 : SORT AN ARRAY SOLUTION : 

class Solution {
public:
void merge(vector<int>&v, int left, int mid, int right){
    vector<int>vec;
    int i = left , j = mid + 1;
    while(i <= mid && j <= right){
        if(v[i] <= v[j]){
            vec.push_back(v[i]);
            i++;
        }
        else{
            vec.push_back(v[j]);
            j++;
        }
    }
    while(i <= mid){
        vec.push_back(v[i]);
            i++;
    }
    while(j <= right){
        vec.push_back(v[j]);
            j++;
    }

    for(int i = 0 ; i < vec.size() ; i++){
        v[left + i] = vec[i]; //Using v[i] = vec[i] always overwrites from index 0 
        ,destroy left half of the array when sorting right  
    }
}
    void mergeSort(vector<int>&v , int left , int right){
        if(left >= right) return;
        int mid = left + (right - left) / 2;
        mergeSort(v,left,mid);
        mergeSort(v,mid+1,right);
        merge(v, left, mid, right);
    }
    vector<int> sortArray(vector<int>& nums) {
        int right = nums.size() - 1;
        mergeSort(nums,0,right);
        return nums;
    }
};
