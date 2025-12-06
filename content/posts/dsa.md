---
draft: true
title: 'DSA Prep+tips+exp'
tags: ["Resources","Insightful","DSA"]
---

# Data Structures:-

According to me data structures are type of data storing methods or containers which is used to store, organise, retrieve and manipulate data efficiently. I mean a computer can do the job even though the data's are not stored efficiently and the tasks will be finished no matter what.but, if you think from a business perspective which focuses on customer satisfaction and one of the ways to achieve them is by giving them instant results. think of yourself as a customer and you are searching a product in amazon what happens if it takes more time to give you the results you feel many emotions and thoughts which might depend on the person and the situation but the point is it creates a friction between you and the product which makes you choose the better thing compared to that right. even though the results will be showed to you eventually no matter what without considering the external factors such as no internet, server down etc... you get the point right.so this is where data sturctures come into play and it is important for a developer to know when to use which data structure to be efficient and reliable.

If you as a developer use an `array` data structure where you need to perform n number of `insertion` and `deletion`, the job will be done for sure but is it efficient? and if you consider this then what is the difference between a good developer and a bad developer. seriously no offense guys but it is our duty to know all these things and be a good developer. that's what differentiates us from others. Actually to tell you the truth i was one of the bad developers who didn't care about when to use which data structure since my PC did the job anyway. but then i was preparing for an interview which required DSA(Data structures & Algorithms) and the magic happened when i started learning it.

so, we will be learning DSA while sharing my experience and tips to make myself as well as you guys a better developer:>

Basically there are 7 data structures avaialble they are,
1. Array
2. LinkedList
3. Stack
4. Queue
5. Hashtable
6. Trees
7. Graphs

>**Note**: The time complexities discusses here are based on the worst case scnario only.

## Arrays:-
Arrays are the most commonly used data structures because it stores data in a continuous format which makes it easy to `search and retrieve` items but it has dificulties when performing `insertion` and `deletion` and the most important part is it should contain similar data types only. Array has a `time complexity of O(1)` for `searching and retieving by index` and `O(n)` for `insertion, deletion` and `searching by value`.

so `arrays` are most suitable when you need quick retireval by index which is efficient. lets take a real world example where you need to find a seat in a movie theatre which contains a series of continuous seats(Array) where you have details of your seat it can be a seat number or combination of row number and column number etc... since you have the index(details) you can find it easily.

## LinkedLists:-
A linkedlist is considered the opposite of the array because it is `dynamic` meaning it can `expand or shrink easily`, it is best suited for `insertion` and `deletion` but when it comes to retrieval it has difficulties since it is `not continuous` and we have traverse from node to node till we get our required result. Linked list have a `time complexity of O(1)` for `insetion and deletion` and `O(n)` for `search and retireval`.

so `linkedlists` are most suitable for insertion and deletion which is efficient. lets take a real world example where you need to create a necklace by adding the beads in a string.now if you need to add a bead(insert), you can add it anywhere in the necklace(linkedlist) and if you want to remove a bead(delete), you can remove a bead from anywhere in the necklace(linkedlist).

## Stack:-
A stack is kind of the combination of arrays and linkedlist, yeah i know crazy right but let me explain. stack stores data in a `continuous` format like array and it has fast `insertion and deletion` like linkedlist. but here's a drawback you can't access random elements like arrays and random insertion and deletion like linkedlist because stack uses `LIFO`(Last In First Out) which prevents both random access and random insertion and deletion. since stack only deals with the top it has `time complexity of O(1)` for all operations provided by it such as `push,pop,peek/top and isempty`

so `stacks` are most suited for insertion and deletion which is efficient. lets take a real world example where you are browsing a homepage and you have wandered to multiple links within the webpage but you need to go back to a particular page which you have came across while wandering but it doesn't have a direct link so you start using the browser's back button(stack) to go back(pop) to the required page.

## Queue:-
A queue is said to be an alternate version of the stack where order is very important. queue uses `FIFO`(First In First Out) so the `insertion` is made at the end and `deletion` is done at the start. just like stack queue has a `time complexity of O(1)` for all operations provided by it such as `enqueue(insertion), dequeue(deletion), peek/front and isempty`

so `queue` is most suited for scheduling tasks and processing things in a sequence. let's take a real world example where you are standing in a line to buy sweets. the lines moves in order when the first one to stand in lives is served first.

## Hashtable:-
Hashtables uses key-value pairs to store data which makes it easy to `search and retrieve` data, `insert and delete` data using keys. hashtable doesn't store data in order so the worst case `time complexity` for `insert, delete and search/retrieve` is `O(n)` and the worst case happens only when there are more hash collisions but apart from that the average `time complexity` is `O(1)` for `insert, delete and search/retrieve`

so `hashtables` are most suitable for super fast searching,inserting and deletion by keys. it is mostly used for counting item's frequency,caching and indexing. lets take a real world example where you need to find food item(key) in a restaurent menu(hashtable).

## Trees:-
Trees are hierarchical data structures which are made up of nodes and the top most node is called root node. each node can have two or more child nodes and there will be no cycles. trees represents data with parent-child relationship. since it is hierarchical, operations such as searching, insertion and sorting is done easily. tree data structure has a `time complexity of O(n)` for unbalanced trees and `time complexity of O(log n)` for balanced trees and these apllies to all operation offered by trees.

so `trees` are most suited for searching, sorting and inserting hierarchical data which is efficient. lets take a real life example where you need to search a file(child node) in a file system(tree)

## Graphs:-
Graphs are collection of nodes connected by edges and they have cycles. graphs are used to represent network and relationship between the items 













































































# Algorithms:-

Before diving deep into the Algorithms, we need to learn about the metrics which is used to assess the complexity of the data structures. there are two types of metrics to analyse the complexities they are:-
1. Time complexity
2. Space complexity

## Time complexity:-
It is used to measure the 