# 19.Remove Nth Node From End of List #

Given a linked list, remove the nth node from the end of list and return its head.

For example,

	Given linked list: 1->2->3->4->5, and n = 2.
	After removing the second node from the end, the linked list becomes 1->2->3->5.

Note:

Given n will always be valid.
Try to do this in one pass.

## Translate ##

删除倒数第n个结点，输入的n保证有效

## Solutions ##

### Approach #1 ###

快慢指针

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
	    ListNode* removeNthFromEnd(ListNode* head, int n) {
	        if(head == NULL) return head;
	        ListNode *res = new ListNode(-1);
	        res->next = head;
	        ListNode *fast = res, *slow = res;
	        for(int i = 0; i < n; i++){
	            fast = fast->next;
	        }
	        while(fast->next != NULL){
	            slow = slow->next;
	            fast = fast->next;
	        }
	        slow->next = slow->next->next;
	        return res->next;
	    }
	};