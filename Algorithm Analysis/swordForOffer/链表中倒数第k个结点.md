## ��Ŀ����

> ����һ����������������е�����k����㡣

##��������

> ����

##�������

> ������k�����

##��Ŀ����

�ڵ�������

```
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}
```

> �ⷨһ  ����ʱ�䣺35ms  ռ���ڴ棺503k

```
public class Solution {
    public ListNode FindKthToTail(ListNode head,int k) {
		   if(head==null || k<=0){
               return null;
           }        
           ListNode last = head;
           for(int i=1;i<k;i++){
               last = last.next;
               if(last==null){
                   return null;
               }
           }
        
           while(last.next!=null){
               head = head.next;
               last = last.next;
           }
        
           return head;
    }
}
```

�����������жϱ߽磬�½�һ���ڵ�last����ʼָ��head�ڵ㣻��
����
�������������ˣ�����ʹ����head�ڵ�������ڵ㣨���������С�ڣ�ͷ���null��������
����
�����������ڵ�ͬʱ��������ֱ��lastָ�����һ���ڵ�Ϊֹ��

�����ܷ������ڵ�head�ڵ���ǵ����ڣ���ڵ㡣


> �ⷨ�� ������ʱ�䣺34ms��ռ���ڴ棺629k

```
public class Solution {
    public ListNode FindKthToTail(ListNode head,int k) {
����������if(head==null || k<=0){
               return null;
        }
        
        ListNode p = head;
        ListNode q = head;
        int i = 0;
        for (; p != null; i++) {
            if (i >= k){
                q = q.next;
            }     
            p = p.next;
        }
        return i < k ? null : q;
    }
}
```
������ⷨһ��ͬһ��˼·������ֻ����һ�α������¼����Ӷ�O(n)��