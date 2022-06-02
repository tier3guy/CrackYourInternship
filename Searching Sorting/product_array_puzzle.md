[Question Link](https://practice.geeksforgeeks.org/problems/product-array-puzzle4525/1#)

```
class Solution{
  public:

    vector<long long int> productExceptSelf(vector<long long int>& nums, int n) {

        long long int pdt = 1;
        long long int zeroCount = 0; bool containsZero = false;
        for(int i=0; i<nums.size(); i++){
            if(nums[i]) pdt *= nums[i];
            else zeroCount += 1;
        }

        if(zeroCount) containsZero = true;

        for(int i=0; i<nums.size(); i++){
            if(containsZero){
                if(nums[i]){
                    nums[i] = 0;
                }
                else{
                    if(zeroCount > 1) nums[i] = 0;
                    else nums[i] = pdt;
                }
            }
            else{
                nums[i] = pdt/nums[i];
            }
        }

        return nums;
    }
};
```
