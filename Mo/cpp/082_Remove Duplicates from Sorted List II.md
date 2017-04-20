# 82.Remove Duplicates from Sorted List II #

Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.

For example,

	Given 1->2->3->3->4->4->5, return 1->2->5.
	Given 1->1->1->2->3, return 2->3.

## Translate ##

删除所有出现多次的结点

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
	    ListNode* deleteDuplicates(ListNode* head) {
	        if(head == NULL || head->next == NULL) return head;
	        
	        ListNode res(-1);
	        res.next = head;
	        ListNode *p = &res, *cur = head;
	        while(cur != NULL){
	            while(cur->next != NULL && cur->val == cur->next->val){
	                cur = cur->next;
	            }
	            if(p->next == cur)
	                p = p->next;
	            else
	                p->next = cur->next;
	            cur = cur->next;
	        }
	        return res.next;
	    }
	};