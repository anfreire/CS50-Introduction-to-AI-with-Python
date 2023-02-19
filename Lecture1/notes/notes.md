---
id: kptgvxu4nzswkwe3fewx2an
title: Notes
desc: ''
updated: 1676769213293
created: 1676760675923
---

#### Definitions here [folder](../material)

### How to approch a problem in machine learning

1. Starting with a frontier that just contains one state.
2. Repeat:
    [Page 40](../material/lecture0.pdf)
    - If the frontier is empty, there is no solution.
    - Remove a node from the frontier.
    - If the node contains a goal state, return the corresponding solution.
    - Expand the node, adding the resulting nodes to the frontier.

# How to avoid a problem

[Page 58](../material/lecture0.pdf)

### Revised approach

1. Starting with a frontier that just contains one state.
2. Start with an empty explored set.
3. Repeat:
    - If the frontier is empty, there is no solution.
    - Remove a node from the frontier.
    - If the node contains a goal state, return the corresponding solution.
    - Expand the node, adding the resulting nodes to the frontier.
    - If the node is not in the explored set, add it to the explored set.

#### Whats the order of the frontier?
##### Stack
###### last-in first-out data type
## This is called depth-first search.

##### Queue
###### first-in first-out data type
## This is called breadth-first search.

### What is the difference between DFS and BFS?

Depth-first search is a strategy for searching a tree or graph. It starts at the root node and explores as far as possible until it reaches a goal state or a dead end. It then backtracks and explores the next branch, exhausting all possible paths until it finds a goal state or a dead end. It then backtracks again and explores the next branch, and so on. It is a recursive algorithm. As no preference is given to the order in which the nodes are expanded, it is possible that the algorithm will find a goal state that is not optimal. If the solution is possible, depth-first search will find it, but it may not be the most efficient solution. Eventually, the algorithm will exhaust all possible paths and return the best solution it has found, its all about the order of the frontier.

Breadth-first search is a strategy for searching a tree or graph. It starts at the root node and explores all of the neighbor nodes at the present depth prior to moving on to the nodes at the next depth level. It uses the opposite strategy as depth-first search, which instead explores the node branch as far as possible before being forced to backtrack and expand other nodes. It is a non-recursive algorithm. As no preference is given to the order in which the nodes are expanded, it is possible that the algorithm will find a goal state that is not optimal. If the solution is possible, breadth-first search will find it, but it may not be the most efficient solution. Eventually, the algorithm will exhaust all possible paths and return the best solution it has found, its all about the order of the frontier.

### Uninformed search
#### Uninformed search is a search algorithm that does not use any problem-specific knowledge to guide the search.

### Informed search
#### Informed search is a search algorithm that uses problem-specific knowledge to guide the search.


- Greedy best-first search
  Search algorithm that expands the node that is closest to the goal, on the grounds that this is likely to lead to a solution quickly. It does not guarantee to return the optimal solution, but in many practical problem domains, it is much faster than other approaches. It is a heuristic search algorithm. Expands the node that is closest to the goal, on the grounds that this is likely to lead to a solution quickly. It does not guarantee to return the optimal solution, but in many practical problem domains, it is much faster than other approaches. It is a heuristic search algorithm.
    Difference between informed and uninformed search on the DFS algorithm:
    - Informed search doesn't choose arbitrarily, it uses problem-specific knowledge to guide the search. In this case, the heuristic function. The manhattan distance is a heuristic function. Its not necessarily the shortest path, but it is a good approximation, that's why its called greedy best-first search.

- A* search
  Calculates the cost of the path from the start node to the current node, and adds it to the heuristic cost of the current node to get the total cost. It then expands the node with the lowest total cost. It is a heuristic search algorithm. Expands the node that is closest to the goal, on the grounds that this is likely to lead to a solution quickly. It does not guarantee to return the optimal solution, but in many practical problem domains, it is much faster than other approaches. It is a heuristic search algorithm.
    Difference between informed and uninformed search on the BFS algorithm:
    - As it progresses, it keeps track of the cost of the path from the start node to the current node, and adds it to the heuristic cost of the current node to get the total cost. It then expands the node with the lowest total cost. It is a heuristic search algorithm.

- Adversarial search
  Search algorithm that is used to find the best move in a game. It is a heuristic search algorithm. Search algorithm that is used to find the best move in a game. It is a heuristic search algorithm.

### MINIMAX
- Minimax is a decision rule used in decision theory, game theory, statistics, and philosophy for minimizing the possible loss for a worst case (maximum loss) scenario. When dealing with gains, it is referred to as "maximin"—to maximize the minimum gain. Originally formulated for two-player zero-sum game theory, covering both the cases where players take alternate moves and those where they make simultaneous moves, it has also been extended to more complex games and to general decision-making in the presence of uncertainty. Minimax is widely used in artificial intelligence and computer science.
- Makes the decision that maximizes the minimum value of the opponent's possible responses, while maximizing the same value for itself. It is a heuristic search algorithm. Search algorithm that is used to find the best move in a game. It is a heuristic search algorithm.

----

# TIKTAKTOE

INITIAL STATE: The board is empty.

PLAYER: 
        -   IF X as made a move the function will return O
        -   IF O as made a move the function will return X
        Tells us who's turn it is.

ACTIONS:
        -   Takes the state of the game, and returns a list of all the possible actions that can be taken.

RESULT:
        -   Takes a state and an action as input, and returns the state that results from taking that action.

TERMINAL:
        -   Takes a state as input, and returns True if the game is over, and False otherwise.

UTILITY:
        -   Takes a terminal state as input, and returns 1 if X has won, -1 if O has won, and 0 if the game is a draw.

Optimizations:
        -   Alpha-beta pruning
            Calculate the minimax value of a node, and if the value is less than alpha, then we know that the maximizer will never choose that node, and if the value is greater than beta, then we know that the minimizer will never choose that node. This allows us to prune the search tree, and thus improve the efficiency of the algorithm.
        -   Depth-Limited Minimax
            Limits the depth of the search tree, and thus improves the efficiency of the algorithm.
        Evaluation function
            A function that takes a state as input, and returns a value that represents how good that state is for the maximizing player. This allows us to prune the search tree, and thus improve the efficiency of the algorithm. The evaluation function is used in the minimax algorithm, and in the alpha-beta pruning algorithm.