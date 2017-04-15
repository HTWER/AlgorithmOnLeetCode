# 24.Swap Nodes in Pairs #

Given a linked list, swap every two adjacent nodes and return its head.

For example,
Given `1->2->3->4`, you should return the list as `2->1->4->3`.

Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.

## Translate ##

两两翻转链表结点

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
	    ListNode* swapPairs(ListNode* head) {
	        if(head == NULL || head->next == NULL) return head;
        
	        ListNode resHead(-1);
	        resHead.next = head;
	        
	        ListNode *p = &resHead;
	        ListNode *t = head, *next = t->next;
	        while(next){
	            p->next = next;
	            t->next = next->next;
	            next->next = t;
	            
	            p = t;
	            t = p->next;
	            next = ( t ? t->next : NULL );
	        }
	        return resHead.next;
	    }
	};

### Approach #2 ###

如果没有不允许改变链表的要求，可以两两swap(p->val, p->next->val)

	class Solution {
	public:
	    ListNode* swapPairs(ListNode* head) {
	        ListNode *p = head;
			while(p && p->next){
				swap(p->val, p->next->val);
				p = p->next->next;
			}
			return head;
	    }
	};
	
