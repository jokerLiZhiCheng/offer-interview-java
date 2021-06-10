# leetcode

## 链表问题

### 旋转链表问题
    将链表每个节点向后移动k个位置：
    public ListNode rotateRight(ListNode head, int k)
    解题方法：将其闭合为环——对k取余数——移动头结点

### 链表的中间结点
    找到指定链表的中间链表
    public ListNode middleNode(ListNode head)
    解题方法：快慢指针法
            快指针一次走两个节点，慢指针走一个节点，当快指针到达末尾时，慢指针指向的就是中间结点