# [Cracking the Coding Interview: 189 Programming Questions and Solutions](https://www.amazon.com/Cracking-Coding-Interview-Programming-Questions/dp/0984782850/ref=pd_lpo_sbs_14_t_0?_encoding=UTF8&psc=1&refRID=2D8JZV4YGTS2KG4NTWF3&dpID=41XgSiYW7dL&preST=_SY291_BO1,204,203,200_QL40_&dpSrc=detail)

By Gayle Laakmann McDowell

## Chapter 1: The interview process

 - Overview of standard interview process
   - Goals: Measure analytical skills, coding skills, tech knowledge, experience and culture fit

 - Lack of response means nothing
 - It is common to re-apply to positions

## Chapter 2: Behind the scenes

 - Usual process: Tech screening, on site with multiple interviews
 - Case studies of interview processes at common large tech companies

## Chapter 3: Special situations

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
 - Quick sort: 