# Theory vs. Practice

- List 3 reasons why asymptotic analysis may be misleading with respect to
  actual performance in practice.

  Asymptotic analysis bases an algorithms performace largly on input sizes, and how an algorithm opperates based on these input sizes. Actual runtime can be affected by factors that are not accounted for when an algorithm runs. A few of these factors include:
  1) Asymptotic analysis looks strictly at the opperations that are being excecuted on an input, and how long they take in general. Software and hardware can be a factor that gets overlooked in this, as some machines may result in diffent complexities than others.
  2) Asymptotic analysis looks at a sort of "whole picture" when deciding how long an algorithm takes to run, and in simplified $O$ complexities, constant terms are ignored ie: $O(5n + 20)$ is simplified to $O(5n)$, and the constant is dropped. This time can add up and take longer than expected when working with large input sizes, resulting in a longer runtime than a $\Theta$ representation could suggest. Asymptotic analysis also ignores lower order terms that arise in in algorithm. If an algorithm has a complexity of $O(n^2 + n^4), it is simplified to $O(n^4)$, however the $n^2$ can be rather large with large inputs, yeilding longer runtime results.
  3) Asymptotic analysis can be misleading when assuming best/worst case everytime, like the example below, if we assume best case, a binary search tree take at most $log_2(1000) = 10 comparisons, and worst case takes at most n = 1,000 comparisons. These are quite different and the data should be considered if you get an unexpected runtime result. 

- Suppose finding a particular element in a binary search tree with 1,000
  elements takes 5 seconds. Given what you know about the asymptotic complexity
  of search in a binary search tree, how long would you guess finding the same
  element in a search tree with 10,000 elements takes? Explain your reasoning.

The Asymptotic analysis of a binary search tree is $O(log(n))$, the height of a binary search tree is $log_2(n)$ for a tree with $n$ elements.For 1,000 elements we have $log_2(1000) = 9.96578$, or approximately 10 seconds. For 10,000 elements, we have $log_2(10,000) = 13.28771$, or about 14 seconds. We know that for 1,000 elements, it actually takes 5 seconds, so we need to know what effect 10,000 elements will have on this algorithm's runtime. We can find this by: $(log_2(10,000))/(log_2(1,000)$, or $14/10 = 1.4$. So plugging in our 1.4 increase rate for 10,000 elements we have $5 * 1.4 = 7$ seconds for 10,000 elements.

- You measure the time with 10,000 elements and it takes 100 seconds! List 3
  reasons why this could be the case, given that reasoning with the asymptotic
  complexity suggests a different time.
  1) Resource Contention: If the machine running the BST search is also executing other programs or processes, the available computational resources (CPU, memory, etc.) may be limited. Reduced access to fast cache or main memory could lead to slower data retrieval, increasing the runtime. Running the BST code on a system performing heavy multitasking could lead to slower search times due to reduced resource availability. While this would affect small input sizes as well, the affect scales with the input size, you you are seeing a larger diffence with a larget input size than you would with a small input size. For example, if the overhead of another process running is 10ms (costs the bst 1ms per memory fetch) with 1,000 elements, the overhead will be 10 seconds, however, with 10,000 elements, this is a 100 second delay. While resource deprivation affects all input sizes, the effects of this become much more apparent with large input sizes. 
  2) Effect of Data Types: The type of data stored in the BST can impact performance. For instance: Searching through a tree of tuples involves accessing and comparing multiple elements within each tuple, which adds overhead. Searching a tree of integers is faster because integers are simple and quick to compare. Much like the above reason, the data types also affect small input sizes, but the effects become much more apparent with larger input sizes.
  3) Software Implementation and Tree Balance: The efficiency of the BST implementation and the software environment also play a role. Factors include: Whether the BST is balanced or unbalanced (unbalanced trees lead to greater heights and longer search times, not enough to solely cause the above scenario, but they do contribute). Overheads from memory management and garbage collection, especially in environments like Python, as well as the way comparisons are implemented and handled in the code, as a binary search tree with 10,000 elements could take 14 seconds running best case $O(log_2(n))$, the implementation could casue this to run in linear time, resulting in a complexity of $O(n)$ which would affect this.
     
Add your answers to this markdown file.

Help: https://stackoverflow.com/questions/59206128/balanced-vs-unbalanced-binary-tree-clarification-needed, https://github.com/COSC3020/theory-vs-practice-swilso59-2, https://www.bigocheatsheet.com
“I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.”
