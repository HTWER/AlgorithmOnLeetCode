# 92.Reverse Linked List II #

Reverse a linked list from position m to n. Do it in-place and in one-pass.

For example:

	Given 1->2->3->4->5->NULL, m = 2 and n = 4,	
	return 1->4->3->2->5->NULL.

**Note:**

Given m, n satisfy the following condition:

1 ≤ m ≤ n ≤ length of list.

## Translate ##

反转链表的第`m~n`结点，m, n满足`1 ≤ m ≤ n ≤ length of list`

## Solutions ##

### Approach #1 ###

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
	    ListNode* reverseBetween(ListNode* head, int m, int n) {
	        ListNode *res = new ListNode(-1);
	        res->next = head;
	        ListNode *p = res;
	        for(int i = 1; i < m; i++){
	            p = p->next;
	        }
	        ListNode *head2 = p;
	        p = head2->next;
	        ListNode *cur = p->next;
	        for(int i = m; i < n; i++){
	            p->next = cur->next;
	            cur->next = head2->next;
	            head2->next = cur;
	            
	            cur = p->next;
	        }
	        return res->next;
	    }
	};