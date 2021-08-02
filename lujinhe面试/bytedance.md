# 后端开发一面-2021.7.29

## 问题

1. C++中有哪些不同种的构造函数
2. select、poll、epoll，epoll原理及使用
3. C++0x（c++11的意思？）有哪些新特性
4. 右值引用的作用
5. 智能指针share_ptr，如何解决智能指针循环引用
6. 一个线程池如何构思，如何改进为可以动态调整线程数目的线程池
7. go的并发控制有哪些机制
8. new/delete是否可以重载，重载的new的使用场景（未回答出来）

## 代码

1. 写两个goroutine一起打印1到100
2. 将上面代码扩展到N个goroutine，要求保证goroutine运行的均衡性
   * 面试官提示可以有简单方法保证均衡性，让我下来之后查查资料

>感受：go问的比较多一点，面试官更注重实战，基本没有问太多八股文，重点考察了并发编程



# 后端开发二面-2021.8.2

感受：二面面试官没有一面认真，面试完不确定能不能过

## 问题

1. 线程和进程是什么
2. 为什么有了进程还要有线程
3. rpc和http的区别
4. protobuf和rpc的关系
5. 为什么要三次握手



## 代码

反转链表中指定的一段（lc92-反转链表II）

~~~C++
// 将第left到第right个节点反转，从1开始索引
ListNode* reverseBetween(ListNode* head, int left, int right) {
	if(!head || !head->next) return head;
    int walked = 1;
    ListNode* prehead = new ListNode(0);
    prehead->next = head;
    while(walked < left){
        prehead = prehead->next;
        walked++;
    }
    ListNode* cur = prehead->next;// cur是反转段链表的尾节点
    while(walked < n){
        ListNode* nextcur = cur->next;// 当前要取出来做头插法的节点
        cur->next = nextcur->next;
        nextcur->next = cur;
        prehead->next = nextcur;
        walked++;
    }
    return head;
}
~~~



