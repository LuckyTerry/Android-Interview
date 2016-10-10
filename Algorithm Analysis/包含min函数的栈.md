## ��Ŀ����

> ����ջ�����ݽṹ�����ڸ�������ʵ��һ���ܹ��õ�ջ��СԪ�ص�min������

##��������

> ջ�ṹ

##�������

> min����

##��Ŀ����

> �ⷨһ ��������ʱ�䣺33ms��ռ���ڴ棺528k

```
import java.util.Stack;

public class Solution {

    Stack<Integer> stack = new Stack<Integer>();
    Stack<Integer> min = new Stack<Integer>();
    public void push(int node) {
        stack.push(node);
        if(min.isEmpty()){
            min.push(node);
        }else{
            min.push(min.peek() > node ? node : min.peek());
        }
    }
    
    public void pop() {
        stack.pop();
        min.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int min() {
        return min.peek();
    }
}
```

����˼·��ʵ������ջ��stack�����洢���ݣ�min����������Сֵ��Ϊ��ʹminջ��Ԫ��һֱ�ǵ�ǰstackջ�е���Сֵ��Ҫ��stack��ջʱ�����жϣ������ջֵ�ȵ�ǰminջ��ֵ��С����Ѹ�ֵ��Ϊmin�µ�ջ����������**�ظ���һ��minջ��Ԫ��**��Ϊ��stack��minͬʱ��ջ����Ȼ��ջֵ���ܲ�һ����������Ӱ��minջ���ǵ�ǰstack�е���СԪ�أ���
������min������min.peek()�����ˣ�����ջ��������ջ��

> �ⷨ�� ������ʱ�䣺33ms ��ռ���ڴ棺654k��

```
import java.util.Stack;
import java.util.Iterator;
public class Solution {

     Stack<Integer> stack = new Stack<Integer>();
    public void push(int node) {
        stack.push(node);
    }
    
    public void pop() {
        stack.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int min() {
        Iterator<Integer> iterator = stack.iterator();
        int min = stack.peek();
        int temp = 0;
        while(iterator.hasNext()){
            temp = iterator.next();
            if(temp<min){
                min = temp;
             }
        }
        return min;
    }
}
```

������Ϊstackʵ����Collection�ӿڣ������õ�������������Ԫ�أ������Сֵ���ء� 

> �ⷨ��������ʱ�䣺28ms��ռ���ڴ棺629k

```
public class Solution {

    Stack<Integer> s = new Stack<Integer>();
    ArrayList<Integer> a = new ArrayList<Integer>();
    public void push(int node) {
        a.add(s.push(node));
    }
    
    public void pop() {
        a.remove(s.pop());
    }
    
    public int top() {
        return s.peek();
    }
    
    public int min() {
        Object[] b = a.toArray();
        Arrays.sort(b);
        return (int)b[0];
    }
}
```

������ÿ����ջԪ�ض�����һ��list�У�����Сֵʱ��listת�������飬��Arrays���������򣨴�С���󣩣�Ȼ�󷵻������һ��Ԫ�ؾ�����Сֵ��