## ��Ŀ����

> �������Ŷ�����A��B���ж�B�ǲ���A���ӽṹ��

##��������

> ���Ŷ�����A��B

##�������

> booleanֵ

##��Ŀ����

���ڵ�������

```
public class TreeNode {
    int val = 0;
    TreeNode left = null;
    TreeNode right = null;
    public TreeNode(int val) {
        this.val = val;
    }
}
``` 

> �ⷨ  ������ʱ�䣺30ms ��ռ���ڴ棺629k

```
public class Solution {
������//�ж�root1Ϊ���ڵ���� �Ƿ���� root2Ϊ������
    public boolean HasSubtree(TreeNode root1,TreeNode root2) {
    
    ����//���������һ���ڵ�Ϊ�վͷ���false
        if (root1 == null || root2 == null) return false;
       
    // ���root2Ϊ���ڵ���� �ǡ�root1Ϊ������������������true;�������α��������ӽڵ������ж�
������return��isSubtree(root1,root2)||
������������������HasSubtree(root1.left,root2)||
��������������������HasSubtree(root1.right,root2);
        
    }��
    //�ж�root2Ϊ���ڵ���� �Ƿ�Ϊ root1Ϊ������������
    public boolean  isSubtree(TreeNode root1, TreeNode root2) {
        if (root2 == null) return true;
        if (root1 == null) return false;
        
        if (root2.val == root1.val) {
        //������ڵ���ͬ�ֱ�����������������Ƿ���ͬ
�������������� return isSubtree(root1.left, root2.left)&& ��              ������������������������isSubtree(root1.right, root2.right);
        }else {
            return false;
        }
    }
}
```

������Ҫ�ݹ�root1�����ҵ���root2��һ���Ľڵ㣻

�ҵ���ͬ�ĸ��ڵ��Ҫ�ж��Ƿ������������ҽڵ㶼��ȣ�������ȷ���true�����򷵻�false;