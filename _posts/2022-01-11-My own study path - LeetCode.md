---
layout:     post
title:      My own study path - LeetCode
subtitle:   My own study path - LeetCode
date:       2022-01-11
author:     DeSoiat
header-img: img/jpg/11.jpg
catalog: true
tags: 
    - JAVA
    - LeetCode
---


# 206. Reverse Linked List

Given the head of a singly linked list, reverse the list, and return the reversed list.

![picture1](https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg)

```
     //iterate
    public ListNode reverseList(ListNode head) {
        ListNode prev = null; 
        ListNode next;
        ListNode current = head;

        while (current != null){
            next = current.next; //store the next pointer
            current.next = prev; //point the next to pre or null value 
            prev = current; // store the current value to prev so the next value will point to the current value for prev
            current = next; // move down the list
        }
            return prev; 
    }
    
    //recursive
     public ListNode reverseList(ListNode head) {
        
         if(head == null || head.next ==null){return head;} //check list
     
        ListNode newHead = reverseList(head.next); 
        head.next.next = head;
        head.next = null;
        return newHead;
        
    }
```







