# Completely-Fair-Scheduler-CFS

The first part of the program involved implementing a multimap from a Left-Leaning Red-Black Tree (LLRB) The multimask was then used to store tasks for the CFS. 

The program was written in C++11 in accordance to the Google C++ Style Guide. It is run from the command line and must be given a file containing the tasks to be scheduled.

NOTE: The code for this project has NOT been uploaded to GitHub publicly, as it was done for my data structures class. This was done to avoid future students from using my code as a violation of academic code conduct.

## Multimap Implementation 
Each node in the LLRB tree is a key and contains a std::vector which allows one key to refer to multiple values. Removing a key will only remove the first value in the list. If a key only refers to one value, that node is deleted and the tree is restructured appropriately.

### Testing the Multimap 
I ran unit tests on the multimap using Google Test, in order to test that the various methods for insertion and deletion were working correctly. A total of 17 tests were written to test the 7 methods in the multimap. A summary of the test cases used is provided below: 

<ul>
  <li>Empty: Tests if the multiset is initially empty </li>
  <li>Error: Makes sure std::runtime_error is thrown when the multimap is empty</li>
  <li>SameKey, RemovalAllKeys, RemoveAllKeyValues1-2, RemoveSomeKeyValues1-2,
RemovalAllReinsert, AlternateInsertion, AlternateRemoval: Tests a mix of Insert() and
Remove() functions being called, including testing that a key can refer to multiple values, values
can be removed individually. </li>
  <li> SameKey, RemovalAllKeys, RemoveAllKeyValues1-2, RemoveSomeKeyValues1-2,
RemovalAllReinsert, AlternateInsertion, AlternateRemoval: Tests a mix of Insert() and
Remove() functions being called, including testing that a key can refer to multiple values, values
can be removed individually. </li>
  <li>RemovalAll: Tests that the multimap is empty after all values initially inserted are deleted</li>
  <li>Min, MinRemoval, Max, MaxRemoval: Tests Min(), Max() respectively with and without
removals from the multimap</li>
</ul>

## Completely Fair Scheduler 
The program uses two user-defined objects: a Tak object and Scheduler object. Task objects are added to the scheduler when the current tick equals their start time, remain in the scheduler as other tasks are processed, and purged when they are finished. Tasks are read in from a file that is provided in the command line when the program is run. The vector sorts the tasks by their start time (if the start times are the same, the alphabetical identifiers are used first). When tasks are completed, they are marked with an asterisk. 

## End Lessons + Notable Skills
Demonstration of ability to:
<ul>
  <li>Write clean, well-documented, industry-standard code adhering to the Google C++ Style Guide</li>
  <li>Write and run unit tests on code to test individual functions</li>
</ul>

Showcases an understanding of:
<ul>
  <li>Data Structures, particularly binary trees, maps, multimaps, and vectors </li>
  <li>Object Oriented Programming Concepts; program employs the use of 2 user-defined objects</li>
  <li>Operator overloading (overloaded << operator for testing) </li>
  <li>Using std library sort functions </li>
</ul>


## Example
$ ./cfs_sched tasks1.dat </br>
0 [0]: _ </br>
1 [1]: A </br>
2 [3]: B </br>
3 [3]: C </br>
4 [3]: C </br>
5 [3]: A </br>
6 [3]: B </br>
7 [3]: B </br>
8 [3]: C* </br>
9 [2]: A* </br>
10 [1]: B* </br>

tasks1.dat </br>
A 1 3 </br>
B 2 4 </br>
C 2 3 </br>

