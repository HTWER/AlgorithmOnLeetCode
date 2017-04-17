# 86.Partition List #

Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.

You should preserve the original relative order of the nodes in each of the two partitions.

For example,

	Given 1->4->3->2->5->2 and x = 3,
	return 1->2->2->4->3->5.

## Translate ##

把小于x的结点移到>=x的结点前，保持相对位置

## Solutions ##

### Approach #1 ###

注意测试用例 [1,1] 0

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
	    ListNode* partition(ListNode* head, int x) {
	        if(head == NULL || head->next == NULL) return head;
	        
	        ListNode *left = new ListNode(-1);
	        ListNode *right = new ListNode(-1);
	        ListNode *left_cur = left, *right_cur = right;
	        ListNode *p = head;
	        while(p != NULL){
	            if(p->val < x){
	                left_cur->next = p;
	                left_cur = p;
	            } else {
	                right_cur->next = p;
	                right_cur = p;
	            }
	            p = p->next;
	        }
	        left_cur->next = right->next;
	        right_cur->next = NULL;
	        return left->next;
	    }
	};