## 1.目录

| [offer 6: 从头到尾打印链表](https://www.nowcoder.com/practice/d0267f7f55b3412ba93bd35cfa8e8035?tpId=13&tqId=11156&tPage=1&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking) | [offer 18 :删除链表中重复的节点](<https://www.nowcoder.com/practice/fc533c45b73a41b0b44ccba763f866ef?tpId=13&tqId=11209&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking>) | [offer 22: 链表中的倒数第 k 个节点](<https://www.nowcoder.com/practice/529d3ae5a407492994ad2a246518148a?tpId=13&tqId=11167&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking>) |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [offer 23: 链表中环的入口节点](<https://www.nowcoder.com/practice/253d2c59ec3e4bc68da16833f79a38e4?tpId=13&tqId=11208&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking>) | [offer 25: 反转链表](<https://www.nowcoder.com/practice/75e878df47f24fdc9dc3e400ec6058ca?tpId=13&tqId=11168&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking>) | [offer 25: 合并两个排序的链表](<https://www.nowcoder.com/practice/d8b6b4358f774294a89de2a6ac4d9337?tpId=13&tqId=11169&tPage=1&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking>) |
| [offer 35: 复杂链表的复制](<https://www.nowcoder.com/practice/f836b2c43afc4b35ad6adc41ec941dba?tpId=13&tqId=11178&tPage=2&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking>) | [offer 52: 两个链表的第一个公共节点](<https://www.nowcoder.com/practice/6ab1d9a29e88450685099d45c9e31e46?tpId=13&tqId=11189&tPage=2&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking>) |                                                              |


## 2、题目

### 1. 从头到尾打印链表
- 题目描述

    输入一个链表，按链表从尾到头的顺序返回一个ArrayList。

- 输入 

    {67,0,24,58}

- 输出 
    [58,24,0,67]

- 以下是3种解决方案

```
    class Solution:
        # 返回从尾部到头部的列表值序列，例如[1,2,3]
        def printListFromTailToHead(self, listNode):
            res = []

            # 1、放入列表 逆序输出
            while listNode:
                res.append(listNode.val)
                listNode = listNode.next
            return res[::-1]

            # 2、使用栈
            temp = []
            while listNode:
                temp.append(listNode.val) # 进栈
                listNode = listNode.next
            while temp:
                res.append(temp.pop()) # 出栈
             return res

            # 3、递归
            def solutions(Node):
                if Node: 
                    solutions(Node.next)
                    res.append(Node.val)
                    
            solutions(listNode)         
            return res
```

### 2. 删除链表中重复的节点

- 题目描述

    在一个排序的链表中，存在重复的结点，请删除该链表中重复的结点，重复的结点不保留，返回链表头指针。 例如，链表1->2->3->3->4->4->5 处理后为 1->2->5

- 输入 

    {1,2,3,3,4,4,5}

- 输出 
    {1,2,5}

- 以下是3种解决方案

```
    class Solution:
        def deleteDuplication(self, pHead):

            cur=pHead
            hashmap={}
            arr=[]

            # 建立统计的hashmap {val:count}
            while cur:
                val=cur.val
                hashmap[val]=hashmap.setdefault(val,0)+1
                cur=cur.next

            # 将count为1的val放入list
            for i in hashmap:
                if hashmap[i]==1:
                    arr.append(i)

            # 排序
            arr=sorted(arr)
            
            # 构建ListNode
            start=ListNode(0)
            p=start
            for i in arr:
                temp=ListNode(i)
                p.next=temp
                p=p.next
                
            return start.next  

```