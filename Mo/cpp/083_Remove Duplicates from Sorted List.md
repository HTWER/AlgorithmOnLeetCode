# 83.Remove Duplicates from Sorted List #

Given a sorted linked list, delete all duplicates such that each element appear only once.

For example,

	Given 1->1->2, return 1->2.
	Given 1->1->2->3->3, return 1->2->3.

## Translate ##

删除重复结点，只保留一个

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
	        ListNode *p = head, *q = p->next;
	        while(q != NULL){
	            if(p->val == q->val)
	                p->next = q->next;
	            else
	                p = q;
	            q = p->next;
	        }
	        return head;
	    }
	};