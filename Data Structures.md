## Array Sliding Window

https://leetcode.com/problems/longest-substring-without-repeating-characters/

```
def lengthOfLongestSubstring(self, s: str) -> int:
    left = 0
    max_length = 0
    char_set = set()

    for right in range(len(s)):
        while s[right] in char_set:
            char_set.remove(s[left])
            left = left + 1
        char_set.add(s[right])
        max_length = max(max_length, right - left + 1)
    
    return max_length
```

## Binary Search

https://leetcode.com/problems/binary-search/

```
def search(self, nums: List[int], target: int) -> int:
    left = 0
    right = len(nums) - 1
    while left <= right:
        middle = (right + left) // 2
        if target == nums[middle]:
            return middle
        elif target > nums[middle]:
            left = middle + 1
        else:
            right = middle - 1
    return -1
```

## Binary Tree Level Order Traversal

https://leetcode.com/problems/binary-tree-level-order-traversal/

```
def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
    if not root:
        return []
    ans = []
    queue = [root]
    while queue:
        level_size = len(queue)
        level = []
        for i in range(level_size):
            node = queue.pop(0)
            level.append(node.val)
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        ans.append(level)
    return ans
```

## DFS
```
def dfs(matrix):
  # Check for an empty matrix/graph.
  if not matrix:
    return []

  rows, cols = len(matrix), len(matrix[0])
  visited = set()
  directions = ((0, 1), (0, -1), (1, 0), (-1, 0))

  def traverse(i, j):
    if (i, j) in visited:
      return

    visited.add((i, j))
    # Traverse neighbors.
    for direction in directions:
      next_i, next_j = i + direction[0], j + direction[1]
      if 0 <= next_i < rows and 0 <= next_j < cols:
        # Add in question-specific checks, where relevant.
        traverse(next_i, next_j)

  for i in range(rows):
    for j in range(cols):
      traverse(i, j)
```

## BFS

https://leetcode.com/problems/number-of-islands/

```
def numIslands(self, grid: List[List[str]]) -> int:
    island = 0
    rows, cols = len(grid), len(grid[0])
    visited = set()

    def bfs(r, c):
        queue = deque()
        queue.append((r, c))
        visited.add((r, c))
        
        while queue:
            curr_i, curr_j = queue.popleft()
            directions = [[1,0],[-1,0],[0,1],[0,-1]]

            for dr, dc in directions:
                next_i, next_j = curr_i + dr, curr_j + dc
                if 0 <= next_i < rows and 0 <= next_j < cols and grid[next_i][next_j] == "1" and (next_i, next_j) not in visited:
                    queue.append((next_i, next_j))
                    visited.add((next_i, next_j))
    
    for r in range(rows):
        for c in range(cols):
            if grid[r][c] == "1" and (r, c) not in visited:
                island = island + 1
                bfs(r, c)
    return island
```

## Linked List

https://leetcode.com/problems/reorder-list/

```
def reorderList(self, head: Optional[ListNode]) -> None:
    """
    Do not return anything, modify head in-place instead.
    """
    # Find mid point
    slow = head
    fast = head.next
    while fast and fast.next:
        fast = fast.next.next
        slow = slow.next
    
    # Reverse second half
    prev = None
    curr = slow
    while curr:
        after = curr.next
        curr.next = prev
        prev = curr
        curr = after
    slow.next = None

    # Merge forward and backward
    A, B = head, prev
    while A and B:
        A_next = A.next
        B_next = B.next
        
        A.next = B
        B.next = A_next

        A = A_next
        B = B_next
```
## Backtrack

https://leetcode.com/problems/combination-sum/

```
def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
    res = []

    def backtrack(idx, comb, total):
        if total == target:
            res.append(comb[:])
            return
        if total > target or idx >= len(candidates):
            return
        comb.append(candidates[idx])
        backtrack(idx, comb, total + candidates[idx])
        comb.pop()
        backtrack(idx + 1, comb, total)

        return res
    
    return backtrack(0, [], 0)
```

## Heap

https://leetcode.com/problems/k-closest-points-to-origin/

```
def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
    min_heap = []
    for xi, yi in points:
        dist = xi ** 2 + yi ** 2
        min_heap.append((dist, xi, yi))
    
    heapq.heapify(min_heap)
    ans = []
    for i in range(k):
        a, b, c = heapq.heappop(min_heap)
        ans.append((b, c))
    return ans
```


## Dynamic Programming

https://leetcode.com/problems/coin-change/

```
def coinChange(self, coins: List[int], amount: int) -> int:
        dp = [amount + 1] * (amount + 1)
        dp[0] = 0
        for i in range(1, amount + 1):
            for c in coins:
                if i - c >= 0:
                    dp[i] = min(1 + dp[i - c], dp[i])
        return dp[-1] if dp[-1] != amount + 1 else -1
```

