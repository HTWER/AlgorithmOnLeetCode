# 7.Reverse Integer #

Reverse digits of an integer.

**Example1:** x = 123, return 321

**Example2:** x = -123, return -321

The input is assumed to be a 32-bit signed integer. Your function should return 0 when the reversed integer overflows.

## Translate ##

反转整数，超出INT_MAX返回0

## Solutions ##

### Approach #1 ###

	class Solution {
	public:
	    int reverse(int x) {
	        long res = 0;
	        while(x != 0){
	            res  = res*10 + x % 10;
	            x /= 10;
	        }
	        return (res<INT_MIN || res>INT_MAX) ? 0 : res;
	    }
	};