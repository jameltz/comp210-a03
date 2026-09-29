# A3 Worksheet: Design Document for the Linked List

**Name: Jack Meltzer**
**Onyen: 730748670**

Six sections, 15 points. Fill this in **before** you write any code. It is a design document, so it says what your methods must do and what must stay true, not how you will write them. Everything you need is in `README.md`. Keep it short: the whole document should fit on about one page. Write your answers directly under each prompt.

---

## 1. The problem in your own words (2 points)

In two or three sentences, describe the problem this assignment asks you to solve. Say what the six new methods let a program do with a list of whole numbers, and whether they build new lists or change the ones they are given.

```
This assignment asks you to implement six methods for linked lists of whole numbers: simpleMerge adds one list to the start of another, removeAtIndex removes a node at a given index, isEqual checks whether two lists contain the same elements in the same order, removeRepeats removes duplicate values, reverse reverses the order of the list, and merge interleaves two lists. All six methods modify the existing list or lists they are given rather than creating and returning a new list.
```

---

## 2. Operations (3 points)

For each method you will write, describe in a few words what it is responsible for. Then say which of the list's **first node**, **last node**, and **size** the method can change, and in what situation. If it can change none of them, write "none". For the two merge methods, also say what state `list2` is left in.

| Method | What it is responsible for                                                                                                                                                 | Which of first node / last node / size it can change, and when                                                                                                        |
|---|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `simpleMerge` | Adds list2 to start of current list                                                                                                                                        | First node and size change when list2 is non-empty, last node changes when current list is empty. List 2 is left empty.                                               |
| `removeAtIndex` | Removes the node at a specified index                                                                                                                                      | First node changes when removing index 0, last node changes when removing the last node, size always changes.                                                         |
| `isEqual` | Checks whether two lists have the same elements in the same order                                                                                                          | None                                                                                                                                                                  |
| `removeRepeats` | Removes duplicate values from a sorted list                                                                                                                                | First node can change if first value is duplicated, likewise for last node. Size decreases for every duplicate node removed.                                          |
| `reverse` | Reverses the order of all nodes in the list                                                                                                                                | First and last node will change as long as list is not empty. Size will never change.                                                                                 |
| `merge` | Interleaves list2 into current list, starting with list2's first node.   | First node and size change as long as list2 is non-empty. Size will increase by size of list1. Last node changes if list2 is longer than list1. list2 is left empty.  |

---

## 3. Data structure and justification (2 points)

This assignment uses a singly linked list that keeps a reference to both its first node and its last node. In one sentence, justify a linked list over an array-backed list (like the dynamic array from L11) for the work in Tasks 1 and 6. In a second sentence, explain what keeping a reference to the **last** node gives the class, and name one method, either provided or one of yours, that would have to do more work without it.

```
A linked list is useful for Tasks 1 and 6 because nodes can be connected and rearranged without shifting all the elements like they would in an array-backed list. Keeping a reference to the last node allows the class to access the end of the list directly, so add would have to traverse the entire list to find the last node without it.
```

---

## 4. Class invariant (3 points)

State the invariant the `LinkedList` class must maintain: what is always true about `_head`, `_tail`, and `_size` whenever no method is in the middle of running. Your answer should cover an empty list and a non-empty list, and it should say how `_size` relates to the nodes actually in the list.

```
For an empty list, _head and _tail are both null and _size is 0. For a non-empty list, _head points to the first node, _tail points to the last node, and _tail.getNext() is null. Also _size is always equal to the number of nodes actually in the linked list.
```

---

## 5. Three edge cases (3 points)

List three edge cases where a first attempt at one of your methods is likely to go wrong. Use at least two different methods, and don't reuse the main examples from the README. For each one, give the exact input (the list, plus `list2` or the index where one applies) and the correct result, including anything that must change about the first node, the last node, or the size.

| Method | Input | Correct result |
|simpleMerge|current list = empty, list2 = 7 --> 8 --> 9|Correct result: current list = 7 --> 8--> 9, _head = 7, _tail = 9, _size = 3|
|removeRepeats|current list = 4 --> 4 --> 4|Correct result: current list = 4 with _head = 4, _tail = 4, _size = 1  |
|merge|current list = 2 --> 4 --> 6, list2 = 1|Correct result: current list = 1 --> 2 --> 4 --> 6, _head = 1, _tail = 6, _size = 4|
|  |  |  |

---

## 6. Test strategy (2 points)

In two or three sentences, describe how you will check each method before you submit to the autograder. Say what you will look at after each call besides the printed contents of the list, and where your edge cases from section 5 come in.

```
I will test each method with normal cases and edge cases, checking not only the printed list contents but also that _size is correct, _head points to the first node, and _tail points to the last node when appropriate. I will also check that list2 is empty after simpleMerge and merge, and I will use the three edge cases from Section 5 to make sure boundary cases work correctly.
```

---

## Submitting

Turn this in with your answers as a `.md` file on Gradescope. The code goes to Gradescope separately; see `README.md`.
