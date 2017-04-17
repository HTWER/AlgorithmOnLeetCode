# 445.Add Two Numbers II #

You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Follow up:
What if you cannot modify the input lists? In other words, reversing the lists is not allowed.

**Example:**

	Input: (7 -> 2 -> 4 -> 3) + (5 -> 6 -> 4)
	Output: 7 -> 8 -> 0 -> 7

## Translate ##

将两个链表存储的数相加，返回的结果也用链表存储

## Solutions ##

### Approach #1 ###

单向链表要从尾部开始操作，使用栈辅助

	/**
	 * Definition for singly-linked list.
	 * struct ListNode {
	 *     int val;
	 *     ListNode *next;
	 *     ListNode(int x) : val(x), next(NULL) {}
	 * };
	 */
	class Solution {
	public:
	    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
	        stack<int> s1, s2, s;
	        while(l1 != NULL){
	            s1.push(l1->val);
	            l1 = l1->next;
	        }
	        while(l2 != NULL){
	            s2.push(l2->val);
	            l2 = l2->next;
	        }
	        int jinwei = 0;
	        while(!s1.empty() || !s2.empty()){
	            int sum = jinwei;
	            if(!s1.empty()){
	                sum += s1.top();
	                s1.pop();
	            }
	            if(!s2.empty()){
	                sum += s2.top();
	                s2.pop();
	            }
	            jinwei = 0;
	            if(sum >= 10){
	                jinwei = 1;
	                sum -= 10;
	            }
	            s.push(sum);
	        }
	        if(jinwei == 1)
	            s.push(1);
	        ListNode* res = new ListNode(-1);
	        ListNode* cur = res;
	        while(!s.empty()){
	            int top = s.top();
	            s.pop();
	            ListNode* node = new ListNode(top);
	            cur->next = node;
	            cur = cur->next;
	        }
	        return res->next;
	    }
	};