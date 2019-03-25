### leetcode:

#### 19、思路：

​	1、链表遍历；

​	2、首尾指针；

```c

```



#### 24、两两交换链表中的节点：

```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
你的算法只能使用常数的额外空间。
你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。
 */
struct ListNode* swapPairs(struct ListNode* head) {
    if (head == NULL || head->next == NULL) return head;
    struct ListNode *p = head, *q = head->next, *k = head->next->next;
    head = head->next;
    while (1) {
        q->next = p, p->next = k;
        if (k && k->next) p->next = k->next;
        p = k;
        if (p == NULL || p->next == NULL) break;
        q = p->next, k = q->next;
    }
    return head;
}
```

24-2：加一个虚拟头结点

#### 83、

```c
struct ListNode {
    int val;
    struct ListNode *next;
}
struct ListNode* deleteDuplicates(struct ListNode* head) {
    struct ListNode *p = head, *q;
    while (p && p->next) {
        if (p->val == p->next->val) {
            q = p->next;
            p->next = q->next;
            free(q);
        } else {
            p = p->next;
        }
    }
    return head;
}
```

链表排序用冒泡排序

141

```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
bool hasCycle(struct ListNode *head) {
   if(head == NULL) return false;
    struct ListNode *p = head, *q = head->next;
    while (q && q->next) {
        p = p->next;
        q = q->next;
        q = q->next;
        if (p == q) return true;
    }
    return false;
}
```

160

```c

```

202、

思路：int中最大值为以2开头的10位数，最大值为1999999999， 最长为1 + 81*9=730 ，链表长度不超过731

链表判环问题：一个指针向后走一步，另一个指针向后走两步，若相遇，则证明链表有环。

```c
int get_next(int x) {
    int ret = 0;
    while (x) {
        ret += (x % 10) * (x % 10);
        x /= 10;
    }
    return ret;
}

bool isHappy(int n) {
    int p = n,  q = get_next(get_next(n));
    while (q != 1) {
        p = get_next(p);
        q = get_next(get_next(q));
        if (p == q) return 0;
    }
    return 1;
}    
```

203

```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* removeElements(struct ListNode* head, int val) {
    struct ListNode ret, *p = &ret, *q;
    ret.next = head;
    while (p->next) {
        if (p->next->val == val) {
            q = p->next;
            p->next = q->next;
            free(q);
        } else {
            p = p->next;
        }
    }
    return ret.next;
}
```

206

```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* reverseList(struct ListNode* head) {
    struct ListNode ret, *p = head, *q;
    ret.next = NULL;
    while (p) {
        q = p->next;
        p->next = ret.next;
        ret.next = p;
        p = q;
    }
    return ret.next;
}
```

234、将链表拆分为两个链表，将两半同时输出

237

```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
void deleteNode(struct ListNode* node) {
   struct ListNode *q = node->next;
    node->val = node->next->val;
    node->next = node->next->next;
    free(q);
    return ;
}
```

