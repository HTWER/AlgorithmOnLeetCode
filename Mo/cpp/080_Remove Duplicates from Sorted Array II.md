# 80.Remove Duplicates from Sorted Array II #

Follow up for "Remove Duplicates":
What if duplicates are allowed at most twice?

For example,

	Given sorted array nums = [1,1,1,2,2,3],

Your function should return length = 5, with the first five elements of nums being 1, 1, 2, 2 and 3. It doesn't matter what you leave beyond the new length.

## Translate ##

删除重复的元素，最多允许重复两次

## Solutions ##

### Approach #1 ###

	class Solution {
	public:
	    int removeDuplicates(vector<int>& nums) {
	        if(nums.size() < 3) return nums.size();
	        int i = 2;
	        for(int j = 2; j < nums.size(); j++){
	            if(nums[j] != nums[i - 2])
	                nums[i++] = nums[j];
	        }
	        return i;
	    }
	};