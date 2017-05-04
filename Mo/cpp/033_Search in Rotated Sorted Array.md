# 33.Search in Rotated Sorted Array #

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.

## Translate ##

在某点旋转一个已排序的数组，返回给定值在数组中的下标，找不到返回-1

## Solutions ##

### Approach #1 ###

二分查找

	class Solution {
	public:
	    int search(vector<int>& nums, int target) {
	        int first = 0, last = nums.size();
	        while(first != last){
	            int mid = first + (last - first) / 2;
	            if(nums[mid] == target) 
	                return mid;
	            if(nums[first] <= nums[mid]){  //first~mid有序
	                if(nums[first] <= target && nums[mid] > target)
	                    last = mid;
	                else
	                    first = mid + 1;
	            } else {           //mid~last有序
	                if(nums[mid] < target && target <= nums[last-1])
	                    first = mid + 1;
	                else
	                    last = mid;
	            }
	        }
	        return -1;
	    }
	};