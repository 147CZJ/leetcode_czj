给你一个链表，每 k 个节点一组进行翻转，请你返回翻转后的链表。

k 是一个正整数，它的值小于或等于链表的长度。

如果节点总数不是 k 的整数倍，那么请将最后剩余的节点保持原有顺序。

 

示例：

给你这个链表：1->2->3->4->5

当 k = 2 时，应当返回: 2->1->4->3->5

当 k = 3 时，应当返回: 3->2->1->4->5
简单模拟 
```
public ListNode reverseKGroup(ListNode head, int k) {
       if(length(head)<k)return head;
       int size = k-1;
       ListNode pre = head;
       while(size>0){
           pre = pre .next;
           size--;
       }
       size = k-1;
       ListNode nexth = reverseKGroup(pre.next, k);
       pre.next = null;
       ListNode heads = fz(head);
       ListNode pret = heads;
       while(size>0){
           pret = pret.next;
           size--;
       }
       pret.next = nexth;
       return heads;
    }
    public ListNode fz(ListNode head){
         ListNode pre = null;
        ListNode curr = head;
        while(curr!=null){
            ListNode nextcurr = curr.next;
            curr.next = pre;
            pre = curr;
            curr = nextcurr;
        }
        return pre;
    }//反转列表
    public int length(ListNode head){
        ListNode tp  = head;
        int res = 0;
        while(tp!=null){
            res++;
            tp=tp.next;
        }
        return res;
    }//计算长
```