<img width="959" height="539" alt="image" src="https://github.com/user-attachments/assets/b3ad9712-8b95-449c-a0a8-20c1bc9a42c2" /># LRU-CACHE-
C++ solution to LeetCode 146: LRU Cache using a Hash Map and Doubly Linked List, achieving O(1) average time complexity for get() and put() operations.
# LRU Cache — LeetCode 146

## Overview

This project contains a C++ implementation of the **Least Recently Used (LRU) Cache**, a data structure that stores key-value pairs and removes the least recently used entry when its capacity is exceeded.

The solution is designed to achieve **O(1) average time complexity** for both `get()` and `put()` operations using a Hash Map and a Doubly Linked List.

## Problem Statement

Implement an `LRUCache` class with the following operations:

- `LRUCache(int capacity)` — Initializes the cache with a fixed capacity.
- `int get(int key)` — Returns the value associated with the key, or `-1` if the key does not exist.
- `void put(int key, int value)` — Inserts or updates a key-value pair. If the capacity is exceeded, the least recently used entry is removed.

Whenever a key is accessed or updated, it becomes the most recently used entry.

**Problem:** [LeetCode 146 — LRU Cache](https://leetcode.com/problems/lru-cache/)

**Difficulty:** Medium  
**Language:** C++  
**Topics:** Data Structures, Hash Map, Doubly Linked List, Cache Design

## Approach

The implementation combines two data structures:

### 1. Hash Map

The Hash Map stores each key, its value, and an iterator pointing to its position in the linked list. This allows entries to be found efficiently.

### 2. Doubly Linked List

The linked list maintains the order of usage:

- **Front:** Most recently used entry.
- **Back:** Least recently used entry.

When an entry is accessed or updated, it moves to the front. When the cache reaches its capacity, the entry at the back is removed.

## Operations

### `get(key)`

1. Check whether the key exists in the Hash Map.
2. If it does not exist, return `-1`.
3. Otherwise, move the key to the front of the linked list.
4. Return its associated value.

### `put(key, value)`

1. If the key already exists, remove its old position from the linked list.
2. If the key is new and the cache is full, remove the least recently used entry.
3. Insert the key at the front of the linked list.
4. Update the Hash Map with the value and the new list position.

## Example

**Input:**

```text
LRUCache cache = new LRUCache(2);
cache.put(1, 1);
cache.put(2, 2);
cache.get(1);
cache.put(3, 3);
cache.get(2);
cache.put(4, 4);
cache.get(1);
cache.get(3);
cache.get(4);
```

**Output:**

```text
null
null
null
1
null
-1
null
-1
3
4
```

**Explanation:**

1. Insert `(1, 1)` and `(2, 2)`.
2. Access key `1`, making it the most recently used.
3. Insert `(3, 3)`, evicting key `2`.
4. Access key `2`; it is no longer present, so return `-1`.
5. Insert `(4, 4)`, evicting key `1`.
6. Keys `3` and `4` return values `3` and `4`, respectively.

## Complexity Analysis

| Operation | Average Time Complexity |
|---|---|
| `get(key)` | O(1) |
| `put(key, value)` | O(1) |

**Space Complexity:** O(capacity)

The cache stores at most `capacity` entries in the Hash Map and Doubly Linked List.

## Concepts Learned

- Hash Maps and efficient key lookup
- Doubly Linked Lists and iterator management
- Cache eviction policies
- Maintaining usage order
- Designing data structures with constant-time average operations

## Technologies Used

- C++
- Standard Template Library (STL)
- LeetCode Online Judge

## How to Run

1. Open the [LeetCode LRU Cache problem](https://leetcode.com/problems/lru-cache/).
2. Select C++ as the programming language.
3. Paste the solution into the editor.
4. Click **Submit** to run the test cases.

The implementation uses the C++ STL containers `list` and `unordered_map`.

## Key Takeaway

This problem demonstrates how combining a Hash Map with a Doubly Linked List enables efficient cache operations while maintaining the order of recently used entries.

---

*Part of my journey in Data Structures and Algorithms using C++.*
