---
Table of Contents
- [Terminology (1/2)](#through-out-this-course-we-will-be-using-the-following-terminology)
- [Definition of a search problem](#a-search-problem-is-defined-by-the-following)
- [Terminology (2/2)](#lets-add-some-more-terminology)
- [Solving a search problem](#approach-to-solving-a-search-problem)
- [A better approach to solving a search problem](#revised-approach---a-better-approach)
- [Depth-first search (DFS)](#depth-first-search-dfs)
- [Breadth-first search (BFS)](#breadth-first-search-bfs)
- [Uniformed search](#uniformed-search)
- [Informed search](#informed-search)
- [Greedy best-first search (GBFS)](#greedy-best-first-search-gbfs)
- [A\* search](#a-search)
- [Adversarial search](#adversarial-search)
- [Search problem in which two players alternate turns](#search-problem-in-which-two-players-alternate-turns)
- [Minimax search](#minimax-search)
- [Minimax algorithm in Tic-tac-toe](#minimax-algorithm-in-tic-tac-toe)
- [Minimax](#minimax)
- [Optimizations](#optimizations)
- [Alpha-beta pruning](#alpha-beta-pruning)
- [Depth-limited Minimax](#depth-limited-minimax)
---

### Through out this course we will be using the following terminology:

&nbsp;

- Agent

    Entity that perceives its environment and acts upon that environment.

&nbsp;

- State

    A configuration of the agent and its environment

&nbsp;

- Action

    Choices that can be made in a state

&nbsp;

- Transition model
    
    A description of what state results from performing any applicable action in any state

&nbsp;

- Goal test
    
    Way to determine whether a given state is a goal state

&nbsp;

- Path cost

    Numerical cost associated with a given path

&nbsp;

[Go to top](#table-of-contents)

---

&nbsp;

## A **search problem** is defined by the following:

&nbsp;

- **Initial state** - The state at the beginning of the search - (s0)
- **Actions** - The actions that can be performed in a state - ACTIONS(s)
- **Transition model** - The model that describes the result of performing an action in a state - RESULT(s, a)
- **Goal test** - The test that determines whether a state is a goal state - (sF)
- **Path cost** - The cost of a path - (g(n))

#### ⚠️ Symbol representation for explanation purposes - might not be the same as the one in the lecture ⚠️


&nbsp;

[Go to top](#table-of-contents)

---

&nbsp;

## Let's add some more terminology:

&nbsp;

- Solution

    A sequence of actions that leads from the initial state to a goal state

&nbsp;

- Optimal solution

    A solution that has the lowest path cost among all solutions

&nbsp;

- Node

    A data structure that keeps track of:
        - a **state**
        - a **parent** (node that generated this node)
        - an **action** (action applied to parent to generate this node)
        - a **path cost** (from initial state to this node)

&nbsp;

[Go to top](#table-of-contents)

---

&nbsp;

## Approach to solving a search problem:

&nbsp;

1. **Initialize the frontier** - a data structure that contains the initial node
2. Repeat:
    1. If the frontier is empty, then there is **no solution**
    2. Remove a node from the frontier
    3. If the node contains a goal state, then return the solution
    4. **Expand** the chosen node, adding the resulting nodes to the frontier 

There is a problem with this approach:
    
    The frontier can contain the same node multiple times, which is not optimal.

&nbsp;

[Go to top](#table-of-contents)

---

&nbsp;

## Revised approach - a better approach:

&nbsp;

1. **Initialize the frontier** - a data structure that contains the initial node
2. Start with an empty **explored set**
3. Repeat:
    1. If the frontier is empty, then there is **no solution**
    2. Remove a node from the frontier
    3. If the node contains a goal state, then return the solution
    4. **Expand** the chosen node, adding the resulting nodes to the frontier
    5. Add the node to the explored set

&nbsp;

[Go to top](#table-of-contents)


---

&nbsp;

## Depth-first search (DFS)

&nbsp;

### Search algorithm that always expands the deepest node in the frontier

- This algorithm when encounters two paths, it doesn't have a preference for one over the other, it just goes until it reaches the end of the path or it reaches a dead end.
- If it reaches a dead end, it backtracks to the last node that has more than one path and continues from there.
- Because it has a explored set, it doesn't get stuck in an infinite loop.
- The order of the frontier is last in first out (LIFO).

&nbsp;

[Go to top](#table-of-contents)

---

&nbsp;

## Breadth-first search (BFS)

&nbsp;

### Search algorithm that always expands the shallowest node in the frontier

- The difference between DFS and BFS is that when it encounters two paths, it progresses by levels on both paths, not into the end of one path and then the other like DFS.
- The order of the frontier is first in first out (FIFO).

&nbsp;

[Go to top](#table-of-contents)

---

&nbsp;

## Uniformed search

&nbsp;

### Search strategy that uses no problem-specific knowledge

- It doesn't use any problem-specific knowledge, it just uses the search problem definition.

&nbsp;

[Go to top](#table-of-contents)

---

&nbsp;

## Informed search

&nbsp;

### Search strategy that uses problem-specific knowledge to find solutions more efficiently

- It uses problem-specific knowledge to find solutions more efficiently.
  Example: Heuristic function that estimates the cost of the cheapest path from the current state to a goal state.

&nbsp;

[Go to top](#table-of-contents)

---

&nbsp;

## Greedy best-first search (GBFS)

&nbsp;

### Search algorithm that expands the node that is closest to the goal, as estimated by a heuristic function h(n)

- It uses a heuristic function to estimate the cost of the cheapest path from the current state to a goal state.
- It doesn't use the path cost, it just uses the heuristic function.
- For the heuristic function, usually use the Manhattan distance.

&nbsp;

[Go to top](#table-of-contents)

---

&nbsp;

## A* search

&nbsp;

### Search algorithm that expands the node that has the lowest value of f(n) = g(n) + h(n)

g(n) - the cost of the path from the initial state to node n

h(n) - the cost of the cheapest path from node n to a goal state

f(n) - the total cost of the path from the initial state to the goal state that goes through node n

- It uses a heuristic function to estimate the cost of the cheapest path from the current state to a goal state.
- It uses the path cost and the heuristic function.
- For the heuristic function, usually use the Manhattan distance.

&nbsp;

[Go to top](#table-of-contents)

---

&nbsp;

## Adversarial search

&nbsp;

### Search problem in which two players alternate turns

&nbsp;

Example: Tic-tac-toe

&nbsp;

## Minimax search

&nbsp;

### Search algorithm that is used to solve two-player, zero-sum, perfect-information games

&nbsp;

- It is used to solve two-player, zero-sum, perfect-information games.
- It is a **backtracking** algorithm.
- It is a **recursive** algorithm.

Max(X) aims to maximize the score.

Min(0) aims to minimize the score.

&nbsp;

### Game

&nbsp;

- S0 - initial state
- Player(s) - returns the player to move in state s
- Actions(s) - returns the set of actions that can be performed in state s
- Result(s, a) - returns the state that results from performing action a in state s
- Terminal(s) - returns true if s is a terminal state
- Utility(s) - final numerical value of the game

&nbsp;

### Minimax algorithm in Tic-tac-toe

&nbsp;

- Given a state **s**:
  - Max picks action **a** in **Actions(s)** that produces the highest value of **MIN-VALUE(Result(s, a))**
  - Min picks action **a** in **Actions(s)** that produces the lowest value of **MAX-VALUE(Result(s, a))**

&nbsp;

### Minimax

&nbsp;

function MAX-VALUE(state):
    if Terminal(state):
        return Utility(state)
    v = -infinity
    for action in Actions(state):
        v = max(v, MIN-VALUE(Result(state, action)))
    return v

function MIN-VALUE(state):
    if Terminal(state):
        return Utility(state)
    v = infinity
    for action in Actions(state):
        v = min(v, MAX-VALUE(Result(state, action)))
    return v

&nbsp;

### Optimizations

&nbsp;

#### Alpha-beta pruning

Alpha-beta pruning is a way to reduce the number of nodes that are evaluated by the minimax algorithm in its search tree. It stops evaluating a move when at least one possibility has been found that proves the move to be worse than a previously examined move. Alpha-beta pruning is an adversarial search algorithm used commonly for machine playing of two-player games (Tic-tac-toe, Backgammon, Checkers, Chess, Go, etc.). It is an extension of minimax algorithm that seeks to decrease the number of nodes that are evaluated by the minimax algorithm in its search tree.

&nbsp;

#### Depth-limited Minimax

Depth-limited Minimax is a limiter on the depth of the search tree. It is used to prevent the minimax algorithm from searching the entire game tree. It is used to prevent the minimax algorithm from searching the entire game tree to save computation time.

&nbsp;

[Go to top](#table-of-contents)

---



## Knowledge-Based Agents 
  
###  Agents that reason by operating on internal representations of knowledge.

&nbsp;
   
Lets take this sentences as information:

- If it didn't rain, Harry vidited Hagrid today.
- Harry visited Hagrid or Dumbledore today, but not both.
- Harry visited Dumbledore today.
  
Based on this information, we can conclude:

- Harry did not visit Hagrid today.
- It did not rain today.
 
&nbsp;

---

&nbsp;

### What represented those sentences?

An assertion about the world in a knowledge representation language.

&nbsp;

---

&nbsp;

To represent the information we have, there are several ways to do it. Today we will use Propositional Logic. For that, we will need to define some terms:

- Propositional Symbols
  - P -> for exmaple might represent the proposition "It did not rain today."
  - Q -> for exmaple might represent the proposition "Harry visited Dumbledore today."
  
- Logical Connectives
  - not: ¬
  - and: ∧
  - or: ∨
  - implication: →
  - biconditional: ↔

&nbsp;

---

&nbsp;

### Not (¬)


| P | ¬P |
|---|----|
| T | F  |
| F | T  |

&nbsp;

---

&nbsp;

### And ( ∧ )

| P | Q | P ∧ Q |
|---|---|-------|
| T | T | T     |
| T | F | F     |
| F | T | F     |
| F | F | F     |

&nbsp;

---

&nbsp;

### Or ( ∨ )

| P | Q | P ∨ Q |
|---|---|-------|
| T | T | T     |
| T | F | T     |
| F | T | T     |
| F | F | F     |

&nbsp;

---

&nbsp;

### Implication ( → )

| P | Q | P → Q |
|---|---|-------|
| T | T | T     |
| T | F | F     |
| F | T | T     |
| F | F | T     |

&nbsp;

---

&nbsp;

### Biconditional ( ↔ )


| P | Q | P ↔ Q |
|---|---|-------|
| T | T | T     |
| T | F | F     |
| F | T | F     |
| F | F | T     |
|   |   |       |


&nbsp;

---

&nbsp;


### Model

A model assigns truth values to the propositional symbols in a knowledge base.

Example:

    We have the following Propositional Symbols:

    P = It did not rain today.

    Q = Harry visited Dumbledore today.

    Our Model:

    {P = true, Q = false}


&nbsp;

---

&nbsp;

### Knowledge Base

A knowledge base is a set of sentences in a knowledge representation language.

Example:

    We have the following Propositional Symbols:

    P = It did not rain today.

    Q = Harry visited Dumbledore today.

    Our Knowledge Base:

    {¬P, Q → ¬P, Q}


&nbsp;

---

&nbsp;

### Entailment

Every model in wich sentence a is true, sentence b is also true.

    a |= b

Example:

    a = Today is 25th of December.

    b = Today is Christmas.

    a |= b

&nbsp;

---

&nbsp;

### Inference

The process of deriving new sentences from old ones.

Example:

    We have the following Propositional Symbols:

    P = It is a Tuesday.

    Q = It is raining.

    R = Harry will go for a run.

    Our Knowledge Base:

    KB: (P ∧ ¬Q) → R


&nbsp;

    How we read the Knowledge Base:

    If it is a Tuesday and it is not raining, then Harry will go for a run.

&nbsp;

    Let's add more information to our Knowledge Base:

    KB: (P ∧ ¬Q) → R 
    
    P           ¬Q


    - P is True
    - ¬Q is True
        - (P ∧ ¬Q) is True
            - R is True

&nbsp;

---

&nbsp;

## Model Checking

- To determine if KB |= α
  - Enumerate all possible models for KB
  - In every model in which KB is true, a is also true, then KB entails a.
  - Otherwise, KB does not entail a.

Example:

    We have the following Propositional Symbols:

    P = It is a Tuesday.

    Q = It is raining.

    R = Harry will go for a run.

    Our Knowledge Base:

    KB: (P ∧ ¬Q) → R
    
    P           ¬Q


    Query: R


|P|Q|R|KB|
|-|-|-|--|
|F|F|F|F |
|F|F|T|F |
|F|T|F|F |
|F|T|T|F |
|T|F|F|F |
|T|F|T|T |
|T|T|F|F |
|T|T|T|F |
|T|T|T|F |


&nbsp;

---

&nbsp;

### Inference Rules

&nbsp;

#### These might seem very simple, but we need to specify everything to the computer.

&nbsp;


- Modus Ponens
  - If a → b, and a is true, then b is true.
    
    Example:
    
        Information: 
            If its raining, then Harry it's inside.

        We can conclude:
            Harry is inside.

&nbsp;


- And Elimination
  
  - If a ∧ b is true, then a is true.
    
    Example:
    
        Information: 
            Harry is friends with Ron and Hermione.

        We can conclude:
            Harry is friends with Ron.

&nbsp;


- Double Negation Elimination

  - If ¬¬a is true, then a is true.
    
        Example:
        
            Information: 
                It is not true that Harry did not pass the test.

            We can conclude:
                Harry passed the test.

&nbsp;


- Implication Elimination
  
    -   If a → b is true, then ¬a ∨ b is true.

        Example:
    
            Information: 
                If it is raining, then Harry is inside.

            We can conclude:
                It is not raining, or Harry is inside.

&nbsp;


- Biconditional Elimination

    -   If a ↔ b is true, then (a → b) ∧ (b → a) is true.
  
        E.g:
            Information:
                If it is raining if and only if Harry is inside.

            We can conclude:
                If it is raining, then Harry is inside, and if Harry is inside, then it is raining.

&nbsp;


- De Morgan's Law

    - If ¬(a ∧ b) is true, then ¬a ∨ ¬b is true.
  
        Example:
    
            Information: 
                It is not true that both Harry and Ron passed the test.

            We can conclude:
                Harry did not pass the test, or Ron did not pass the test.

    - If ¬(a ∨ b) is true, then ¬a ∧ ¬b is true.
  
         Example:
    
            Information: 
                It is not true that Harry or Ron passed the test.

            We can conclude:
                Harry did not pass the test, and Ron did not pass the test.

&nbsp;


- Distributive Law

    - If a ∧ (b ∨ c) is true, then (a ∧ b) ∨ (a ∧ c) is true.
  
        Example:
    
            Information: 
                Harry is friends with Ron and Hermione.

            We can conclude:
                Harry is friends with Ron, or Harry is friends with Hermione.

    - If (a ∨ b) ∧ c is true, then (a ∧ c) ∨ (b ∧ c) is true.
  
        Example:
    
            Information: 
                Harry is friends with Ron or Hermione.

            We can conclude:
                Harry is friends with Ron, and Harry is friends with Hermione.

&nbsp;

---

&nbsp;

## Theorem Proving

&nbsp;

- initial state: starting knowledge base
- actions: inference rules
- transition model: new knowledge base after applying inference
- goal test: check statement we want to prove
- path cost function: number of steps in proof

&nbsp;

---

&nbsp;

## Resolution

- Resolution rule

    - If P ∨ Q is true and ¬P, then Q is true.
  
        Example:
    
            Information: 
                (Ron is in the great hall) ∨ (Hermione is in the library)
                Ron is not in the great hall.

            We can conclude:
                Harry is friends with Ron and Hermione, or Harry is friends with Ron or Hermione.

    We can use this rule to prove multiple things at once.

        Example:
    
            Information: 
                (Ron is in the great hall) ∨ (Hermione is in the library) ∨ (Harry is in the common room)
                Ron is not in the great hall.

            We can conclude:
                Hermione is in the library, or Harry is in the common room.

    It can be even more powerful.

        Example:
    
            Information: 
                (Ron is in the great hall) ∨ (Hermione is in the library)
                (Ron is not in the great hall) ∨ (Harry is sleeping)

            We can conclude:
                Hermione is in the library, or Harry is sleeping.

    The goal of this resolution, is to get new **clauses** that are true, and that are not already in the knowledge base.

&nbsp;

---

&nbsp;

## Clause

&nbsp;

### A disjuntion of literals.

    Example:
        P ∨ Q ∨ R

&nbsp;

---

&nbsp;

## Conjunctive Normal Form

&nbsp;

### Logical sentence that is a conjunction of clauses.

    Example:
        (P ∨ Q ∨ R) ∧ (¬P ∨ ¬Q ∨ ¬R)

&nbsp;

---

&nbsp;

## Conversion to CNF

&nbsp;

- Eliminate biconditionals
  - turn a ↔ b into (a → b) ∧ (b → a)
- Eliminate implications
  - turn a → b into ¬a ∨ b
- Move negations inwards
  - turn ¬(a ∨ b) into ¬a ∧ ¬b
  - turn ¬(a ∧ b) into ¬a ∨ ¬b
- Use distributive law
  - turn a ∧ (b ∨ c) into (a ∧ b) ∨ (a ∧ c)
  - turn (a ∨ b) ∧ c into (a ∧ c) ∨ (b ∧ c)

Example:

    (P ∨ Q) → R

    ¬(P ∨ Q) ∨ R    (Eliminate implications)

    (¬P ∧ ¬Q) ∨ R   (De Morgan's Law)

    (¬P ∨ R) ∧ (¬Q ∨ R)   (Distributive Law)

Example:

    (P ∨ Q ∨ R) ∧ (¬P ∨ R ∨ S)

    (Q ∨ R ∨ S)     (Resolution)

Example:

    P ∧ ¬P

    False           (Resolution)

&nbsp;

---

&nbsp;

## Inference by Resolution

&nbsp;


- To determine if KB |= a
  - Check if KB ∧ ¬a is a contradiction
    - If it is, then KB |= a
    - Otherwise, there is no entailment

  - Convert KB ∧ ¬a to CNF
  - Keep applying resolution until we get a contradiction
    - If we produce an empty clause, then KB |= a 
    - Otherwise, there is no entailment, and KB does not entail a

Example:

    Does (A ∨ B) ∧ (¬B ∨ C) ∧ (¬C) entail A?

        (A ∨ B) ∧ (¬B ∨ C) ∧ (¬C) ∧ (¬A)  (Resolution)

        (A ∨ B) ∧ (¬B ∨ C) ∧ (¬C) ∧ (¬A) ∧ (¬B) ∧ ()    (Resolution)

        Empty clause, so a contradiction was found, so KB |= a

&nbsp;

---

&nbsp;

## First Order Logic

&nbsp;

### First order logic is a logic that allows us to talk about objects and their properties.

- Universal Quantification

    - ∀x, P(x) is true if P(a) is true for all a.

        Example:
    
            Information: 
                ∀x, (x is a wizard) → (x is a student)

            We can conclude:
                Harry is a wizard, and Harry is a student.
        
    ∀x -> for all x

    P(x) -> predicate

    x -> variable

&nbsp;

- Existential Quantification
    
        - ∃x, P(x) is true if P(a) is true for some a.
            (At least one a exists that satisfies P(a))
    
            Example:
        
                Information: 
                    ∃x, (x is a wizard) ∧ (x is a student)
    
                We can conclude:
                    Harry is a wizard, and Harry is a student.
    
        ∃x -> for some x
    
        P(x) -> predicate
    
        x -> variable

