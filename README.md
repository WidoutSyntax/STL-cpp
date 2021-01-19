# Contents
1. Standard Template Library

# Standard Template Library
The Standard Template Library(STL) is a set of C++ template classes to provide common data structures. One can easily implement data structures like stack, queue, list and using STL reduces programming time as well. 

The C++ STL grouped into following three categories
1) Sequences              - Vector, List, Doubly ended queue<br/>
2) Container Adapters     - Stack, Queue, Prority queue<br/>
3) Associative Containers - Bitset, Set, Multiset, Map, Multimap 

Usage of several STL classes are illustrated. For convenience and ease of learning, examples are also provided along with syntax.

## Sequences
### Vector
A vector is similar to an array but with dynamic size. Elements can be accessed in O(1) and insert, delete operations will take O(n) time.<br/>

```c++
// declaration and initialization<br/>
vector<int> vec; // vec is a vector variable<br/>
vector<int> vec_1 (5); // vec_1 is a vector of 0, 0, 0, 0, 0<br/>
vector<int> vec_2 (4,100); // vec_2 is a vector of 100, 100, 100, 100<br/>

vector<int>::iterator vec_iter; // vec_iter is an iterator for vector<int><br/>
vec_iter = vec_2.begin(); // vec_2.begin() is the address of its first element, *vec_iter contains 100<br/>

vector<int> vec_3 (vec_2.begin(), vec_2.end()); // initializes from another vector<br/>
vector<int> vec_4 (vec_3); // copies entire vec_3 vector<br/>

int arr[] = {1,2,3};<br/>
vector<int> vec_5 (arr, arr+2); // initializes from arr array, vec_5 is a vector of 1, 2<br/>

// size() - O(1) - returns size of vector<br/>
int vec_size = vec_5.size(); // vec_size contains 2<br/>

// empty() - O(1) - returns 1 if vector is empty, 0 otherwise<br/>
bool vec_empty = vec.empty(); // vec_empty contains 1<br/>

// access - O(1)<br/>
int value = vec_5[0]; // similar to array, value contains 1<br/>

// front() - O(1) - returns reference to first element<br/><br/>
value = vec_5.front(); // value contains 1 <br/>

// back() - O(1) - returns reference to last element<br/>
value = vec_5.back(); // value contains 2 <br/>

// push_back() - O(1) - inserts new element at the end<br/>
vec_5.push_back(3); // vec_5 contains 1, 2, 3<br/>

// pop_back() - O(1) - removes last element<br/>
vec_5.pop_back(); // vec_5 contains 1, 2<br/>

// insert() -  inserts elements at desired positions. Moves the elements after "position" accordingly.<br/>
// insert(position, value) - O(n-position) - due to moving elements after position<br/>
vec_5.insert(vec_5.begin()+1, 4); // vec_5 contains 1, 4, 2<br/>

// insert(position, repetitions, value) - O(repetitions+n-position)<br/>
vec_5.insert(vec_5.begin(), 3, 2); // vec_5 contains 2, 2, 2, 1, 4, 2<br/>

// insert(position, start, end) - O(end-start+n-position)<br/>
vec_5.insert(vec_5.begin(), vec_2.begin(), vec_2.begin()+2); // vec_5 contains 100, 100, 2, 2, 2, 1, 4, 2<br/>

// assign() - overwrites values from the beginning<br/>
// assign(repetitions, value) - O(n') where n' is final size<br/>
vec_5.assign(1, 5); // vec_5 contains 5<br/>

// assign(start, end) - O(n') - n' is final size<br/>
vec_5.assign(vec_2.begin(), vec_2.begin()+3); // vec_5 contains 100, 100, 100<br/>

// erase() - erases elements at desired positions<br/>
// erase(position) - O(n-position) - due to moving elements after position<br/>
vec_5.erase(vec_5.begin()); // vec_5 contains 100, 100<br/>

// erase(start, end) - O(end-start+n-end) - due to elements erased and moving <br/>
vec_5.erase(vec_5.begin(), vec_5.begin()+1); // vec_5 is 100<br/><br/>

// swap() - O(1) - swaps the contents of vectors<br/>
vec_1.swap(vec_2); // vec_1 contains 100, 100, 100, 100 and vec_2 contains 0, 0, 0, 0, 0<br/>

// clear() - O(n) delete the vector<br/>
vec_5.clear(); // vec_5 is empty<br/>

// relational - O(n)<br/>
bool status;<br/>
status = (vec_3 == vec_4); // status contains 1<br/>
status = (vec_3 != vec_4); // status contains 0<br/>
status = (vec_1 < vec_2); // status contains 0, lexicographically compares elements from left<br/>
```
