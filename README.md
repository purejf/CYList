```
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


no head reverse
    p q r;
     p->next = null;
     while (q) {
        r = q->next;
         q->next = p;
         p = q;
         q = r;
     }
     
```
