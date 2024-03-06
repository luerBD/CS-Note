# Leetcode 题解 - 链表

## 1.找出两个链表的交点

160. Intersection of Two Linked Lists (Easy)

[Leetcode](https://leetcode.com/problems/intersection-of-two-linked-lists/description/) / [力扣](https://leetcode-cn.com/problems/intersection-of-two-linked-lists/description/)

<img src="assets/image-20240227211121667.png" alt="image-20240227211121667" style="zoom:50%;" />

pA走过的路径为A链+B链

pB走过的路径为B链+A链

pA和pB走过的长度都相同，都是A链和B链的长度之和，相当于将两条链从尾端对齐，如果相交，则会提前在相交点相遇，如果没有相交点，则会在最后相遇。

```haskell
pA:1->2->3->4->5->6->null->9->5->6->null
pB:9->5->6->null->1->2->3->4->5->6->null
```

```c
struct ListNode *getIntersectionNode(struct ListNode *headA, struct ListNode *headB) {
    struct ListNode *pa = headA, *pb = headB;
    while(pa != pb)
    {
        pa = pa ? pa->next : headB;
        pb = pb ? pb->next : headA;
    }
    return pa;
}
```

## 2.翻转链表

206. Reverse Linked List (Easy)

[Leetcode](https://leetcode.com/problems/reverse-linked-list/description/) / [力扣](https://leetcode-cn.com/problems/reverse-linked-list/description/)

<img src="assets/微信图片_20240228153706.jpg" alt="微信图片_20240228153706" style="zoom: 25%;" />

new_head指针：新链表的头指针，初始时new_head=NULL;

p指针：从旧链表中每次往下选择一个结点进行摘取，放到新链表中；

tmp指针：为了让p可以继续往下选择新结点，每次提前保存p选择结点的后继结点。

关键操作总结如下：

```c
tmp = p->next;
p->next = new_head;
new_head = p;
p = tmp;
```

实现代码：

```c
struct ListNode* reverseList(struct ListNode* head) {
   struct ListNode *new_head = NULL, *p = head;
   while(p)
   {
       struct ListNode* tmp = p->next;
       p->next = new_head;
       new_head = p;
       p = tmp;
   }
   return new_head; 
}
```

## 3.归并两个有序的链表

21. Merge Two Sorted Lists (Easy)

[Leetcode](https://leetcode.com/problems/merge-two-sorted-lists/description/) / [力扣](https://leetcode-cn.com/problems/merge-two-sorted-lists/description/)

```c
struct ListNode* mergeTwoLists(struct ListNode* list1, struct ListNode* list2) {
    struct ListNode *list3 = (struct ListNode *)malloc(sizeof(struct ListNode));
    struct ListNode *p3 = list3;
    while(list1 != NULL && list2 != NULL)
    {
        if(list1->val <= list2->val)
        {
            p3->next = list1;
            list1 = list1->next;
        }
        else
        {
            p3->next = list2;
            list2 = list2->next;
        }
        p3 = p3->next;
    }
    p3->next = list1 == NULL ? list2 : list1;

    return list3->next;
}
```

## 4.从有序链表中删除重复节点

83. Remove Duplicates from Sorted List (Easy)

[Leetcode](https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/) / [力扣](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/description/)

```
Given 1->1->2, return 1->2.
Given 1->1->2->3->3, return 1->2->3.
```

```c
struct ListNode* deleteDuplicates(struct ListNode* head) {
    struct ListNode *p = head, *q = p->next;
    if(!p || !(p->next))
    {
        return NULL; // 如果该链表为空表或者后继结点为空，则返回NULL
    }
    while(p->next)
    {
        if(p->val == q->val)
        {
            p->next = q->next;
            q = q->next;
        }
        else
        {
            p = p->next;
        }
    }
    return head;
}
```

## 5.删除链表的倒数第 n 个节点

19.Remove Nth Node From End of List (Medium)

[Leetcode](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/) / [力扣](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/description/)

第一步：统计链表结点数，记作l

第二步：寻找删除结点的前驱结点，

当l>1时，倒数第n个结点就是正数第l-n个结点，故我们需要找到第l-n结点的前驱结点，将其删除即可；

当l=1时，倒数第1个结点就是正数第1个结点，故我们直接将该结点删除即可，再令head=NULL;

情形1：链表中的结点数 > 1，则

![image-20240305231350083](assets/image-20240305231350083.png)

```
q=p->next;
p->next = q->next;
free(q);
```

情形2：链表中的结点数=1，则

![image-20240305232346122](assets/image-20240305232346122.png)

```
free(p);
head=NULL;
```

完整代码实现：

```c
struct ListNode* removeNthFromEnd(struct ListNode* head, int n) {
    struct ListNode * p = head;
    struct ListNode * q;
    int i, l = 0;
    if(!p)
    {
        return NULL;
    }
    while(p)
    {
        l++;
        p = p->next;
    }
    p = head;
    for(i = 0; i < l - n - 1; i++)
    {
        p = p->next;
    }
    if(p->next != NULL)
    {
        q = p->next;
        p->next = q->next;
        free(q);
    }
    else
    {
        free(p);
        head = NULL;
    }
    return head;
}
```

