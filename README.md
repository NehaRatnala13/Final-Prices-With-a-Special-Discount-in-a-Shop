# 1475. Final Prices With a Special Discount in a Shop

- **Platform:** LeetCode
- **Difficulty:** Easy
- **Topics:** Array, Stack, Monotonic Stack
- **Problem Link:** [Final Prices With a Special Discount in a Shop](https://leetcode.com/problems/final-prices-with-a-special-discount-in-a-shop/)

---

## Problem Statement

For each item `i` with a given price, a discount equal to the first subsequent price `prices[j]` (where `j > i` and `prices[j] <= prices[i]`) is applied. If no such item exists, no discount is given.

### Example 1
- **Input:** `prices = [8, 4, 6, 2, 3]`
- **Output:** `[4, 2, 4, 2, 3]`

### Constraints
- `1 <= prices.length <= 500`
- `1 <= prices[i] <= 1000`

---

## Approach & Intuition

* **Brute Force:** Check subsequent elements for each item until finding a smaller or equal price (\(O(n^2)\) time).
* **Monotonic Stack (Optimal):** Use a stack to track indices and resolve next-smaller-or-equal prices in a single pass (\(O(n)\) time, \(O(n)\) space).

---

## Implementation (Python)

```python
from typing import List

class Solution:
    def finalPrices(self, prices: List[int]) -> List[int]:
        answer = prices[:]
        stack = []

        for i, price in enumerate(prices):
            while stack and prices[stack[-1]] >= price:
                idx = stack.pop()
                answer[idx] -= price
            stack.append(i)

        return answer
```
