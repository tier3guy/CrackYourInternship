[Question Link](https://leetcode.com/problems/find-peak-element)

```
class Solution {
public:
    int findPeakElement(vector<int>& nums) {

        // Linear solution:
        /*
        int prev = INT_MIN, next = INT_MIN;
        for(int i=0; i<nums.size(); i++){
            next = (i+1 < nums.size())? nums[i+1] : INT_MIN;
            if(nums[i] > prev && nums[i] > next) return i;
        }

        return 0;
        */

        // Logrithmic solution

        int start = 0, end = nums.size()-1, mid = 0;
        int prev, next;
        while(start <= end){

            mid = start + (end - start)/2;
            prev = (mid == 0)? INT_MIN : nums[mid-1];
            next = (mid == nums.size()-1)? INT_MIN : nums[mid+1];

            if(nums[mid] < next){
                start = mid+1;
            }
            else if(nums[mid] < prev){
                end = mid-1;
            }
            else return mid;
        }

        return 0;
    }
};
```
