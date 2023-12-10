# Graphs, Graph Algorithms and Huffman Coding Tree. <br>
Projects:<br>
<br>
- CSE 100 project: Huffman Coding Tree. <br>
- CSE 100 project: Graphs and Graph Algorithms. <br>

I pledge not to share my code to maintain fairness, as per UCSD Academic Integrity Policies. While I cannot make my code publicly available, I am willing to provide it upon request from recruiters. <br>

## CSE 100 project: Graphs and Graph Algorithms. <br>


Overview
The mathematical concept of a "graph" is fundamental to Computer Science. In general, any network of connected individuals can be represented using a graph. Almost all of the data structures covered in this course are either themselves graphs or can be abstractly represented using a graph.
For example, in the realm of HIV and COVID-19 epidemiology, the current gold-standard method for analyzing viral sequence data to study the spread of the virus is to perform transmission clustering using a tool called HIV-TRACE (Pond et al., 2018). If you are given n viral sequences (one collected per patient), HIV-TRACE essentially does the following:
* Construct an empty graph with n nodes (one per sequence)
* Compute the distance between each pair of sequences (u,v) under the TN93 model of DNA evolution (Tamura & Nei, 1993)
* If the pairwise distance between u and v is less than or equal to a given threshold (HIV-TRACE uses 0.015 by default; in our sample data, we scale everything up by
* so it should be 15000000), connect u and v with an undirected edge
* Each of the connected components of the resulting graph define a "transmission cluster"
* In addition to finding transmission clusters, the graph produced by HIV-TRACE can yield other information relevant for the prevention of the spread of a virus (Grabowski et al., 2018)
In this Project, we have provided an API of a Graph class that you need to implement. This class will be used to represent undirected graphs. In the starter code, we have provided 4 code files (Graph.h, Graph.cpp, GraphTest.cpp, and Makefile) as well as 2 example graph files (small.csv and hiv.csv).
Graph.h
This file contains the basic declarations of the (undirected) Graph class that you need to implement. We have declared a series of function signatures that you will need to implement. You are free to modify Graph.h however you wish (e.g. adding instance variables to the Graph class, adding any helper functions you'd like, etc.). Our only requirement is that the function signatures we have declared remain unchanged (though you are welcome to overload them if you wish).
Please be sure to thoroughly read the header comments in Graph.h to be sure you understand the functionality, input(s), and output(s) of each function in the Graph class.
Graph.cpp
This file contains the skeleton of implementing the functions we have declared in the (undirected) Graph class. Your task is to fill in the function bodies. You are welcome to add any variables, functions, classes, etc. you wish.
GraphTest.cpp
TestGraph.cpp contains several basic unit tests. This file is only meant to give you an idea of how to write your own unit test files. You are highly encouraged to write as many unit tests as necessary to cover all possible cases. Although we'll not grade your test cases, it will help you find any bugs that may cause your submission to fail with our hidden test cases. This file will be ignored during submission.
Edge List
The <edgelist_csv> argument is the filename of an edge list representing an undirected graph with non-negative edge weights in the CSV format: each line represents an undirected edge between nodes u and v with weight w in the following format: u,v,w
For example, imagine we want to represent the following graph:

We could represent it using the following edge list CSV (note that the order of the rows is arbitrary):
A,B,1
A,C,5
B,C,1
B,D,1
E,F,4
F,G,5
In the example folder of the starter code, we have provided 2 example edge list CSV files: small.csv, which is the exact graph shown above, and hiv.csv, which is a small example graph produced from an HIV-TRACE analysis of a real HIV dataset from San Diego (Little et al., 2014).
Here are some things you can expect about the edge list CSVs you will be given:
* You are guaranteed there will not be any self-edges (e.g. u,u,?)
* You are guaranteed that you will not be given a multigraph, meaning you are guaranteed that there will not exist multiple edges between nodes u and v in the provided edge list
* Further, because the edges are undirected, if you see an edge from u to v (e.g. u,v,?), you are guaranteed that you will not see an edge from v to u (e.g. v,u,?) later in the file
    * Remember: an edge from u to v is bidirectional and is thus also an edge from v to u
* You are not guaranteed that the edges in the CSV will be sorted in any particular order
Makefile
This file will help you compile your code using the make command. If you choose to create any additional code files and add them to Makefile, you are welcome to do so. However, you must make sure that we are able to compile your code using the make command with your Makefile, which should create an object file named graph.o.


<br>

## CSE 100 project: Huffman Coding Tree. <br>

Design Notes
Before you write even a single line of code, it's important to properly design the various components of your compress and decompress programs. Here, we will discuss some aspects of the design that you should be sure to think about.
Parsing Command Line Arguments in C++
Remember that, in C++, you can parse command line arguments by writing a main function as follows:
int main(int argc, char* argv[]) {
    // your program's main execution code
}
The argc variable provides the number of command line arguments that were provided, and the argv variable is an array containing the command line arguments. See the following article to learn more about how to use them:
http://www.cplusplus.com/articles/DEN36Up4/
File I/O
For this assignment, you will have to read data from files and write data to files. To help you with this, in Helper.hpp and Helper.cpp, we have provided two helper classes that can make it easier to perform file I/O: FancyInputStream and FancyOutputStream. It is up to you to thoroughly read the header comments of the functions in these two classes to see how to use them. It is a good idea to have the "Project Workflow" open while you look at the function headers for FancyInputStream and FancyOutputStream to get a better idea of how you can apply various functions of those classes to the compress and decompress workflows.
Note that, in C++, ifstream and ofstream objects are automatically closed by their destructors. Thus, when a FancyInputStream or FancyOutputStream object is destroyed (e.g. if you create it on the runtime stack and it goes out of scope), the internal ifstream/ofstream object will also automatically get destroyed (and thus will automatically close).
Huffman Tree
One crucial data structure you will need is a binary trie (i.e., "code tree" or "encoding tree") that represents a Huffman code. The HCTree.hpp header file provides a possible interface for this structure (included in your repo as skeleton code); you can modify this in any way you want.
Additionally, you will write a companion HCTree.cpp implementation file that implements the interface specified in HCTree.hpp, and you will then use it in your compress and decompress programs. Note that, when you implement the HCTree class, you will want to use the HCNode class we have provided in Helper.hpp.
As you implement Huffman's algorithm, you will find it convenient to use multiple data structures. For example, a priority queue will assist in building the Huffman Tree. Feel free to utilize other beneficial data structures. However, you should use good object-oriented design in your solution. For example, since a Huffman code tree will be used by both your compress and decompress programs, it makes sense to encapsulate its functionality inside a single class accessible by both programs. With a good design, the main functions in the compress and decompress programs will be quite simple: they will create objects of other classes and call their methods to do the necessary work.
Be sure to refer to the "Honey, I Shrunk the File" section of the Data Structures Stepik text for more information about Huffman's algorithm.
Priority Queues in C++
A C++ priority_queue is a generic container that can hold any type, including HCNode* (wink wink). By default, a priority_queue<T> will use the < operator defined for objects of type T. Specifically, if a < b, then b is taken to have a higher priority than a (i.e., by default, it functions as a max-heap).
However, in the Huffman Tree building algorithm, we want to select symbols with lower frequencies first (i.e., we want to use a min-heap). To accomplish this, as can be seen in HCNode.cpp, we have overloaded the < operator to have reversed logic: for two HCNode objects a and b, the operation a < b will return true if the count of symbol a is greater than the count of symbol b. By doing this, our priority_queue will give higher priority to symbols with lower frequencies.
We have overloaded the < operator in the HCNode class, but our priority_queue will not contain HCNode objects: it will contain HCNode pointer objects (i.e., HCNode*). Thus, we need to tell the priority_queue how to compare HCNode* objects by defining a custom "comparison class" that will dereference the pointers and compare the objects they point to. This has been done for you via the HCNodePtrComp class in Helper.hpp. You can use it to create a priority_queue as follows:
priority_queue<HCNode*, vector<HCNode*>, HCNodePtrComp> pq;
* The first argument of the template (HCNode*) tells the priority_queue that it will be storing HCNode* objects
* The second argument of the template (vector<HCNode*>) tells the priority_queue to use a vector<HCNode*> container behind-the-scenes to store its elements
* The third argument of the template (HCNodePtrComp) tells the priority_queue to use our custom HCNodePtrComp class when comparing HCNode* objects to determine priorities
Be sure to refer to the C++ priority_queue documentation for more information about how to use a priority_queue.
Compressed File Header
In the "Suggested Control Flow" section, you will see references to a header that should be stored by the compress program and later retrieved by the decompress program. Both the compress and decompress programs need to construct the Huffman Tree before they can successfully encode and decode information, respectively. The compress program has access to the original file, so it can build the tree by first deciphering the symbol counts. However, the decompress program only has access to the compressed file, not the original file, so it has to use some other information to build the tree. The information needed for the decompress program to build the Huffman Tree needs to be stored in the header of the compressed file. In other words, the header information should be sufficient to reconstruct the tree.
Efficient Header Design
One extremely inefficient strategy for designing the header (which is what is used in the reference solution) is to simply store 256 shorts (in 2-byte chunks as unsigned short objects) at the beginning of the compressed file (i.e., encode the symbol counts as the header), but note that this is not very efficient and is guaranteed to use up 256*2 = 512 bytes! In order to receive full points, you must BEAT our reference solution by coming up with a more efficient way to represent this header!
However, we strongly encourage you to implement the naïve (256 unsigned short objects) approach first, and do not attempt to reduce the size of the header until you’ve gotten your compress and decompress to work correctly for the provided inputs.
Your compress program must work for input files where a particular byte value may occur up to ~60 thousand times in the file.
Alternative approaches may use arrays to represent the structure of the tree itself in the header. With some cleverness, it is possible to optimize the header size to about 10M bits, where M is the number of distinct byte values that actually appear in the input file. This write-up may be helpful to learn about how to "serialize" the tree structure itself.
