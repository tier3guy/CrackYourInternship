[Question Link](https://techiedelight.com/practice/?problem=FloorAndCeil)

```
/*

Given a sorted integer array, find the floor and ceiling of a given number in it. For a given number x, floor(x) is the largest integer in the array less than or equal to x, and ceil(x) is the smallest integer in the array greater than or equal to x.

The solution should return the (floor, ceil) pair. If the floor or ceil doesn't exist, consider it to be -1.

Input: nums[] = [1, 4, 6, 8, 9], x = 2
Output: (1, 4)
Explanation: The floor is 1 and ceil is 4

Input: nums[] = [1, 4, 6, 8, 9], x = 6
Output: (6, 6)
Explanation: The floor is 6 and ceil is 6

Input: nums[] = [-2, 0, 1, 3], x = 4
Output: (3, -1)
Explanation: The floor is 3 and ceil doesn't exist

*/

class Solution
{
public:
	pair<int,int> findFloorAndCeil(vector<int> const &nums, int x)
	{
		int floor = -1, ceil = -1;

		// Method 1 - Linear Search

		/*
		for(int i=0; i<nums.size(); i++){
			if(nums[i] == x){
				floor = ceil = x;
				break;
			}
			else if(nums[i] < x){
				floor = nums[i];
			}
			else if(nums[i] > x){
				ceil = nums[i];
				break;
			}
		}
		*/

		// Binary Search

		// finding floor
		int start = 0, end = nums.size()-1, mid;
		while(start <= end){
			mid = start + (end - start)/2;
			if(nums[mid] == x){
				floor = x;
				break;
			}
			else if(nums[mid] > x){
				end = mid-1;
			}
			else{
				floor = nums[mid];
				start = mid+1;
			}
		}

		// finding ceil
		start = 0; end = nums.size()-1;
		while(start <= end){
			mid = start + (end - start)/2;
			if(nums[mid] == x){
				ceil = x;
				break;
			}
			else if(nums[mid] > x){
				ceil = nums[mid];
				end = mid-1;
			}
			else{
				start = mid+1;
			}
		}

		return {floor, ceil};
	}
};

```
