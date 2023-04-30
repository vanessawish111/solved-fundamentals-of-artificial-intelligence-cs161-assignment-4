Download Link: https://assignmentchef.com/product/solved-fundamentals-of-artificial-intelligence-cs161-assignment-4
<br>
<ol>

 <li>In this problem, you will write a Lisp program that converts graph coloring problems into SAT problems and use a SAT solver to solve them. We have broken the task into multiple functions and provided you with some basic code for file I/O and for gluing all the functions together (see <strong>hw4-skeleton.lsp</strong>).</li>

</ol>

For each graph coloring problem, each node will be represented by a positive integer (node index). Each color is also represented by a positive integer (color index).




Similarly, for a SAT problem, each variable is represented by a positive integer (variable index). As a result, a positive integer is used for a positive literal and a negative integer is used for a negative literal. A clause is simply a list containing the literals of the clause. A CNF formula is then simply a list of clauses.




For example, if variable <em>a </em>has index 1, variable <em>b </em>has 2, and variable <em>c</em> has index 3, then the clause (a v ¬b v ¬c) is represented as the list (1 -2 -3). The CNF formula (a v b v c) ^ (¬a v b v ¬c) is represented as ((1 2 3) (-1 2 -3)). Of course, the order of clauses and literals in each clause does not matter.




Here are your tasks:




<ol>

 <li>Write a function called node2var that takes a node index (n), a color index (c), and the maximum color index (k). This function should return the index of the propositional variable that represents the constraint: “node n receives color c” (with k colors being considered). Use the following conversion convention:</li>

</ol>

<em>variable index = (n-1)*k + c </em>

<em> </em>

<ol>

 <li>Write a function called at-least-one-color that takes a node index (n), a color index (c), and the maximum color index (k). This function should return a clause that represents the constraint: “node n must be colored with <em>at least</em> one color whose index comes from the set {c,c+1,…,k}.”</li>

</ol>




<ul>

 <li>Write a function called at-most-one-color that takes the same arguments as atleast-one-color. This function should return a list of clauses that represent the constraint: “node n must be colored with <em>at most </em>one color whose index comes from the set {c,c+1,…,k}.”</li>

</ul>




<ol>

 <li>Write a function called generate-node-clauses that takes a node index (n) and the maximum color index. This function should return a list of clauses that constrain node n to be colored with <em>exactly </em>one color whose index is in the set {1,2,…,k}.</li>

</ol>




<ol>

 <li>Write a function called generate-edge-clauses that takes an edge (x y) and the maximum color index (k). An (undirected) edge is simply a list of two node indices. This function should return a list of clauses that prohibit nodes x and y from having the same color in the set {1,2,…,k}.</li>

</ol>




After finishing all the above parts, you should be able to convert a graph coloring problem into a SAT problem. To do so, call




(graph-coloring-to-sat &lt;graph filename&gt; &lt;SAT filename&gt; &lt;max color index&gt;)




The graph filename is the name of the input graph file. The SAT filename is the name of the output file you want the program to write to. Max color index is simply the number of colors being considered in the problem.




The graph file has the following format:




<ul>

 <li>The first line contains 2 numbers. The first one is the number of vertices in the graph, the second one is the number of edges.</li>

 <li>Each subsequent line describes an edge. An edge is represented by two numbers—the node indices of the two nodes linked by the edge.</li>

</ul>




Now that you have a converting program working, you will use it to convert some actual graph coloring problems into SAT problems and solve them with a SAT solver.




First, consider the following graph (whose nodes are labeled with their node indices):










A graph file for this graph is also provided (graph1.txt). Convert the graph coloring problem of this graph with 3 colors into a SAT instance using the program you wrote.




Then, download the RSat SAT solver from (<a href="http://reasoning.cs.ucla.edu/rsat/">http://reasoning.cs.ucla.edu/rsat/</a><a href="http://reasoning.cs.ucla.edu/rsat/">)</a>. Read the manual carefully. Use RSat to solve the SAT instance obtained above. <strong>Is the instance satisfiable?</strong>




Do the conversion again, this time, with 4 colors. Use RSat to solve this new SAT instance. <strong>Is the instance satisfiable?</strong>




<strong>What do the answers of these two SAT instances tell you about the graph coloring problem of the above graph? Can you give a solution (a coloring) to the graph coloring problem of the above graph based on the results of RSat? </strong>

<strong> </strong>

Now, use a similar approach to solve the graph coloring of the graph described in graph2.txt. <strong>What is the minimum number of colors required to properly color this graph?</strong>