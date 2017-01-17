
```
typedef struct Node {
    int data;
    struct Node *next;
}NodeL;

void test();

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        test();
    }
    return 0;
}

// 正序创建一个简单的链表
NodeL *create(int n, bool reverse) {
    if (n == 0) return NULL;
    NodeL *head = (NodeL *)malloc(sizeof(NodeL));
    head->next = NULL;
    NodeL *tail = head;
    for (int i = 0; i < n; i++) {
        int data = i + 1;
        NodeL *node = (NodeL *)malloc(sizeof(NodeL));
        if (!reverse) {
            node->data = data;
            tail->next = node;
            tail = node;
            tail->next = NULL;
        } else {
            node->data = data;
            node->next = head->next;
            head->next = node;
        }
    }
    return head;
}
// 正序遍历所有节点
void display(NodeL *head) {
    NodeL *p = head->next;
    while (p != NULL) {
        printf("%d\n", p->data);
        p = p->next;
    }
}

// 正序删除索引为index的节点
NodeL *delete(int index, NodeL *head) {
    if (index < 0) return head;
    // p q r
    NodeL *p = head;
    while (index-- > 0) {
        p = p->next;
    }
    NodeL *q = p->next;
    p->next = q->next;
    q->next = NULL;
    return head;
}


// 逆置链表
NodeL *reverse(NodeL *head) {
    // head p q r
    NodeL *p = head->next;
    NodeL *q = p->next;
    NodeL *r = q->next;
    p->next = NULL;
    while (q != NULL) {
        r = q->next;
        head->next = q;
        q->next = p;
        p = q;
        q = r;
    }
    return head;
}

// 删除倒数第k个节点
NodeL *del(NodeL *head, int index) {
    NodeL *p = head->next;
    int length = 0;
    while (p != NULL) {
        p = p->next;
        length++;
    }
    return delete(length - index - 1, head);
}

NodeL *del2(NodeL *head, int index) {
    NodeL *p = head;
    NodeL *q = head;
    while (index-- > -1) {
        p = p->next;
    }
    while (p->next != NULL) {
        p = p->next;
        q = q->next;
    }
    // 此时q为需要删除的节点的前一个节点
    NodeL *r = q->next;
    q->next = r->next;
    r->next = NULL;
    return head;
}

NodeL *unionList(NodeL *first, NodeL *second) {
    if (first == NULL) {
        return second;
    } else if (second == NULL) {
        return first;
    }
   
    NodeL *p, *q;
    NodeL *newList = NULL;
    if (first->data < second->data) {
        newList = first;
        p = first->next;
        q = second->next;
    } else {
        newList = second;
        p = first->next;
        q = second->next;
    }
    NodeL *tail = newList;
    while (p != nil && q != nil) {
        if (p->data < q->data) {
            tail->next = p;
            tail = p;
            p = p->next;
        } else {
            tail->next = q;
            tail =q;
            q = q->next;
        }
    }
    
    if (p != nil) {
        tail->next = p;
    } else if (q != nil) {
        tail->next = q;
    }
    return newList;
}

void test() {
    
    // -10 -8 2 8
//    // <1 创建
//    {
//        // 1. 正序创建
//        NodeL *head = create(100, false);
//        // 2. 遍历
//        display(head);
//        // 3. 逆序创建
//        NodeL *reverseH = create(100, true);
//        // 4. 遍历
//        display(reverseH);
//        
//    }
//    // <2 逆置
//    {
//        // 1. 正序创建
//        NodeL *head = create(100, false);
//        // 2. 遍历
//        display(head);
//        // 3. 逆置
//        NodeL *reverseH = reverse(head);
//        // 4. 遍历
//        display(reverseH);
//    }
//    // <3 删除
//    {
//        // 1. 正序创建
//        NodeL *head = create(100, false);
//        // 2. 遍历
//        display(head);
////        // 3. 正序删除索引为index的节点
////        NodeL *deleteH = delete(1, head);
////        // 4. 遍历
////        display(deleteH);
//        // 5. 逆序删除索引为index的节点
//        // 5.1 遍历链表获取长度length 正序删除index:第length-index+1个节点
//        // 5.2 指针p和q，p比q多走index-1步，当p到达尾部的时候，q即倒数第index个节点
//        NodeL *del2H = del2(head, 1);
//        display(del2H);
//    }
    
    // 4. 合并
    {
        // 1、2、3、4、5
        NodeL *first = create(5, false);
        // 1、2、3、4、5、6
        NodeL *second = create(10, false);
        
        display(unionList(first, second));
    }
}
```
