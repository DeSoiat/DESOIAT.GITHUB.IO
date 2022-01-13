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
        
         if(head == null || head.next ==null){return head;} 
     
        ListNode newHead = reverseList(head.next); 
        head.next.next = head;
        head.next = null;
        return newHead;
        
    }
```

---

# 1. Two Sum

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

```
Example 1:
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

```
 /*
    //最普通的暴力解法 
    public static int[] twoSum(int[] nums, int target){
        for(int i=0;i< nums.length-1;i++) {
            for (int j = 1; j <= nums.length - 1; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i,j};
                }
            }
        }
        return new int [0];
    }
    */


//优化1 内循环 int j = 1 会让J 从1循环到尾 而I的每次增加 J 都必须从1-尾 可以将 j = i + 1 那么J 就可以自己从比i大1 的位置开始循环 可以减少资源的浪费
   /* public static int[] twoSum(int[] nums, int target){
        Map<Integer,Integer> map = new HashMap<Integer,Integer>();
        for(int i=0;i< nums.length-1;i++) {
            for (int j = i + 1; j <= nums.length - 1; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i,j};
                }
            }
        }
        return new int [0];
    }

    */

    // 优化2 放弃使用 IJ 双循环 改为 使用 map 用循环将数值放入 map 后利用 target - i = y 的计算公式 用containsKey 来查找Y 只需要一次循环即可 o（n）

    public static int[] twoSum(int[] nums, int target){

        Map<Integer,Integer> map = new HashMap<Integer,Integer>();

        for(int i=0;i <= nums.length-1;i++) {
           

           if(map.containsKey(target - nums[i])) // put in 2 check for 15 no, then put in 7 check for 8 no, put in 11 check for 4 no , put in 15 check for 2 yes return
           { 
               return new int[]{map.get(target - nums[i]),i}; 
           }
           
            map.put(nums[i],i); 

        }
        return new int[0];
    }

```

---







