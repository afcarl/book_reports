# [Cracking the Coding Interview: 189 Programming Questions and Solutions](https://www.amazon.com/Cracking-Coding-Interview-Programming-Questions/dp/0984782850/ref=pd_lpo_sbs_14_t_0?_encoding=UTF8&psc=1&refRID=2D8JZV4YGTS2KG4NTWF3&dpID=41XgSiYW7dL&preST=_SY291_BO1,204,203,200_QL40_&dpSrc=detail)

By Gayle Laakmann McDowell

## I: The interview process

 - Overview of standard interview process
   - Goals: Measure analytical skills, coding skills, tech knowledge, experience and culture fit

 - Lack of response means nothing
 - It is common to re-apply to positions

## II: Behind the scenes

 - Usual process: Tech screening, on site with multiple interviews
 - Case studies of interview processes at common large tech companies

## III: Special situations

 - Experienced candidates: Less recent classword, more hands on experience
   - May or may not get algorithms questions
 - Unit testers: Lower coding expectations
 - PMs: Can be technical or non-technical
 - Dev Lead and managers: Emphasis on project scoping and management skills
 - Startups: Highly variable
   - Higher emphasis on building things and culture fit

## IV: Before the interview

 - Standard prep work
 - Flow chart from T-12 months to T+2 daysof interview

## V: Behavioral Questions

Interview prep: Have soundbite for each question for 3 projects.
 - Challenges
 - Mistakes/failures
 - Enjoyed
 - Leadership
 - Conflicts
 - What you'd do differently

General concepts
 - Know honest weaknesses, how you're improving on them
 - Questions for the interviewer: Be prepared
 - Know technical projects

Responding to BI questions

 - Be speific, limit scope, offer to dive deeper
 - Structure ansers
   - Nugget first, then describe, or
   - Situation, action, result
 - Mind character traits: Initiative / leadership, empathy, compassion, humility, teamwork / helpfulness

Tell me about yourself (general guidelines)

 - Current role (quick), college, grad school and onward. current role (in depth), hobbies, summary

## VI: Big O

Time complexity & space complexity

 - Big O: upper bound
 - Big Omega: lower bound
 - Big Theta: If O and Omega are the same, then that value is the Theta

Space complexity:

 - Not highly standardized
 - Usually approach, Turing machine w/ 3 tapes
   - Read only input tape
   - Read & write working tape
   - Write only output tape
 - Most would only include the working tape. Including input would require minimum S: O(n), and including output doesn't discriminate between hard problems and large output problems

Tricks

 - Amortized. E.g. array list X insertions take O(2x), while amortized time for each insertion is O(1)
 - Log N: Pops up when you halve work with each step
 - Recursive: Tends to be O(branches^{depth}), where branches are number of time recursive function is called in return line, and depth is recursion depth

## Chapter VII: Technical Questions

Core data structures, algorithms and concepts

 - Data Structures: Linked Lists, Trees, Tries, Graphs, Stacks & Queues, Heaps, Vectors / ArrayLists, HashTables
 - Algorithms: Breadth First Search, Depth First Search, Binary Search, Merge Sort, Quick Sort
 - Concepts: Bit manipulation, Memory (stack vs heap), Recursion, Dynamic Programming, Big O time & space

### Cheat sheet (WIP):

Data Structures

 - Tries: prefix-based trees, each node has valid_entry boolean
 - Stack: FILO
 - Queue: FIFO
 - Heap: Tree, where parents are greater than children (in max heap), or parents are less than children (in min heap). Commonly used as priority queue. 
 - Vectors / ArrayLists: They are the same. They are arrays that double in size when they are full. 

Algorithms

 - Depth first search: Add all children to stack (FILO)
 - Breadth first search: Add all children to queue (FIFO)
 - Binary search: Only valid for searching sorted arrays. Initialize upper and lower. Pick pivot element between upper and lower. If query element is greater than pivot element, set lower to pivot. If query element is below pivot element, set upper to pivot. If query element is pivot element, return. Rinse & repeat. 
 - Merge sort: Split array into n subarrays, each containing one element. Keep merging subarrays into ordered subarrays, until only one array remains. 
 - Quick sort (Pivot sort): 
   - Pick a pivot
   - Re-order array so elements less than pivot come before, greater than come after. Pivot is now in final position
   - Recursively apply operations to sub-arrays, until sub-arrays are of size 0 or 1

### Technical question flow

 - Listen: Identify problem, interesting / unusual information
 - Example: Choose a moderate size example that isn't a special case. Work through applying algorithm on example as a 
 human
 - Outline algorithm
   - Brute force: State the obvious / easy answer
   - Optimize: Look for optimizations on brute force, find unused information, evaluate space and time complexity
   - Walk through: Write TODOs for each step in algorithm, get an idea for modularity
 - Implement: Write beautiful code
 - Test
   - Self code review
   - Small test cases
   - Special / edge cases

### TODO

 - Finish cheat sheet
 - Implement Merge sort, Quick sort
 - Memory: Stack vs heap
 
## The Offer and Beyond

 - Be polite
 - Negotiate any offers you receive
 
## IX: Interview Questions

### Technical Question Approach (WIP)

List out each explicitly 

 - Problem: Given, Return
 - Example: One positive, one negative (usually)
 - Approaches: 
   - List: List out possible options, starting w/ brute force.
   - Evaluate: Find space and time complexity for each
   - Choose
   - Walk through
 - Outline & Implement
   - Write out method signature
   - Write out TODOs, with space to implement
   - Implement
   - Test
 - Step back
   - Perform code review
   - Evaluate solution
   - Evaluate edge cases
 - Outtro
   - Potential next steps, optimizations
   - Mention documentation & testing

### IX Chapter 1: Arrays and Strings

Tips & Tricks:

 - StringBuilder: Concatenating strings requires creating a new string for every concatenation. String builder avoids this by using a single ArrayList, and converting to a String when necessary.

Solution ideas: 

 - Start from end of array
 - Use character counts

### IX Chapter 2: Linked Lists

Tips & Tricks

 - Runner technique: Have 2 pointers. P1 moves one node per iteration, P2 moves k nodes per iteration

Solution ideas:

 - Use two pointers, to represent a 'window'

### IX Chapter 3: Stacks and Queues

Solution ideas:

 - Modify node to hold information about stack (e.g. minimum when node was inserted)

### IX Chapter 4: Trees and Graphs

#### Trees

Tree types

 - Binary tree: 0 to 2 children per node
 - Binary search tree: All left descendents <= node data < all right descendents
 - Tries (Prefix Trees): n-ary tree, with one character stored at each node. * nodes indicate full words

Descriptions
 - Complete binary trees: All levels must be filled, except for last. Last is filled left to right
 - Full binary tree: All nodes have 0 or 2 children
 - Perfect: Full and complete
 - Traversal: In order, pre-order, post-order

#### Graphs

Representations

 - Adjacency list: (Edge, edge, weight) (sparse form)
 - Adjacency matrix: Matrix, with edge weight w represented at M[a][b]= w

Descriptions:

 - Search: Depth first search, breadth first search
 - Bi-directional search: For finding path between two nodes. Run BFS from each node. When two searches collide, shortest path found
