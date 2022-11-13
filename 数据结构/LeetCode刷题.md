# LeetCode刷题



## 链表

### 中等题

#### 两数相加

https://leetcode-cn.com/problems/add-two-numbers/

```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode listNode=null;
        ListNode head=null;
        int jinWei=0;
        while (l1!=null||l2!=null){
            int num1=l1==null?0:l1.val;
            int num2=l2==null?0:l2.val;
            int sum=num1+ num2+jinWei;
            if (listNode==null){
                head=listNode=new ListNode(sum%10);
            }else {
                listNode.next=new ListNode(sum%10);
                listNode=listNode.next;
            }
            jinWei=sum/10;
            if (l1 != null) {
                l1 = l1.next;
            }
            if (l2 != null) {
                l2 = l2.next;
            }
        }
        if (jinWei>0){
            listNode.next=new ListNode(jinWei);
        }

        return head;
    }
}
```



### 简单题

### 困难题

## 栈和队列

### 栈

#### 括号匹配问题

## 查找

### 简单题

#### 二分查找

https://leetcode-cn.com/problems/binary-search/submissions/

```java	
  public int search(int[] nums, int target) {
        int end=nums.length-1;
        int head=0;
        while (head<=end){
            int middle=(head+end)/2;
            if (target==nums[middle]){
                return middle;
            }else if (target<nums[middle]){
                end=middle-1;
            }else {
                head=middle+1;
            }
        }
        return -1;
    }
```

