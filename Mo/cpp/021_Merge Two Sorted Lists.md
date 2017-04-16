# 21.Merge Two Sorted Lists #

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

## Translate ##

合并两个有序的链表，返回的新链表使用原链表的结点

## Solutions ##

归并排序中的merge操作

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
	    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
	        ListNode *res = new ListNode(-1);
	        for(ListNode *p = res; l1 != NULL || l2 != NULL; p = p->next){
	            int val1 = l1 == NULL ? INT_MAX : l1->val;
	            int val2 = l2 == NULL ? INT_MAX : l2->val;
	            if(val1 <= val2){
	                p->next = l1;
	                l1 = l1->next;
	            } else {
	                p->next = l2;
	                l2 = l2->next;
	            }
	        }
	        return res->next;
	    }
	};