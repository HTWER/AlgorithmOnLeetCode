# 148.Sort List #

Sort a linked list in `O(n log n)` time using constant space complexity.

## Translate ##

对一个单向链表排序，时间复杂度O(nlogn)，空间O(1)

## Solutions ##

### Approach #1 ###

单向链表排序使用归并，中点用快慢指针找出

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
	    ListNode* sortList(ListNode* head) {
	        if(head == NULL || head->next == NULL) return head;
	        //用快慢指针找中点
	        ListNode *fast = head, *slow = head;
	        while(fast->next != NULL && fast->next->next != NULL){
	            fast = fast->next->next;
	            slow = slow->next;
	        }
			//断开前后两半
	        fast = slow;
	        slow = slow->next;
	        fast->next = NULL;
			//递归
	        ListNode *L1 = sortList(head);
	        ListNode *L2 = sortList(slow);
	        return mergeLists(L1, L2);
	    }
	    ListNode* mergeLists(ListNode *L1, ListNode *L2){
	        ListNode *res = new ListNode(-1);
	        for(ListNode *p = res; L1 != NULL || L2 != NULL; p = p->next){
	            int val1, val2;
	            val1 = L1 == NULL ? INT_MAX : L1->val;
	            val2 = L2 == NULL ? INT_MAX : L2->val;
	            if(val1 <= val2){
	                p->next = L1;
	                L1 = L1->next;
	            } else {
	                p->next = L2;
	                L2 = L2->next;
	            }
	        }
	        return res->next;
	    }
	};