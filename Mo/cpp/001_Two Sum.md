# 1.Two Sum #

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

**Example:**

	Given nums = [2, 7, 11, 15], target = 9,
	
	Because nums[0] + nums[1] = 2 + 7 = 9,
	return [0, 1].

## Translate ##

给定一个整数，返回数组中和为该数的两个元素的下标

## Solutions ##

### Approach #1 ###


	/**
	 * 1. 排序 
	 * 2. 头尾指针向中间移 
	 */ 
	vector<int> twoSum(vector<int>& nums, int target) {
		vector<int> res;
		/* sort(nums); */
		int p = 0, q = nums.size() - 1;
		while(p < q) {
			if(nums[p] + nums[q] == target) {
				res.push_back(p);
				res.push_back(q);
				return res; 
			} else {
				nums[p] + nums[q] > target ? q-- : p++;
			}
		}
		return res;
	}

### Approach #2 ###
	/**
	 * 使用map
	 * 复杂度 O(n) 
	 */ 
	vector<int> twoSum(vector<int>& nums, int target) {
		vector<int> res;
		unordered_map<int, int> m;
		for(int i=0; i<nums.size(); i++){
			if(m.find(nums[i]) == m.end()){
				//the map's `key` is the number, the `value` is the position
				m[target - nums[i]] = i;
			} else {
				res.push_back(m[nums[i]]);
				res.push_back(i);
				break;
			}
		}
		return res;
	}
