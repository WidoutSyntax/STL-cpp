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
// declaration and initialization
vector<int> vec; // vec is a vector variable
vector<int> vec_1 (5); // vec_1 is a vector of 0, 0, 0, 0, 0
vector<int> vec_2 (4,100); // vec_2 is a vector of 100, 100, 100, 100

vector<int>::iterator vec_iter; // vec_iter is an iterator for vector<int>
vec_iter = vec_2.begin(); // vec_2.begin() is the address of its first element, *vec_iter contains 100

vector<int> vec_3 (vec_2.begin(), vec_2.end()); // initializes from another vector
vector<int> vec_4 (vec_3); // copies entire vec_3 vector

int arr[] = {1,2,3};
vector<int> vec_5 (arr, arr+2); // initializes from arr array, vec_5 is a vector of 1, 2

// size() - O(1) - returns size of vector
int vec_size = vec_5.size(); // vec_size contains 2

// empty() - O(1) - returns 1 if vector is empty, 0 otherwise
bool vec_empty = vec.empty(); // vec_empty contains 1

// access - O(1)
int value = vec_5[0]; // similar to array, value contains 1

// front() - O(1) - returns reference to first element
value = vec_5.front(); // value contains 1 

// back() - O(1) - returns reference to last element
value = vec_5.back(); // value contains 2 

// push_back() - O(1) - inserts new element at the end
vec_5.push_back(3); // vec_5 contains 1, 2, 3

// pop_back() - O(1) - removes last element
vec_5.pop_back(); // vec_5 contains 1, 2

// insert() -  inserts elements at desired positions. Moves the elements after "position" accordingly.
// insert(position, value) - O(n-position) - due to moving elements after position
vec_5.insert(vec_5.begin()+1, 4); // vec_5 contains 1, 4, 2

// insert(position, repetitions, value) - O(repetitions+n-position)
vec_5.insert(vec_5.begin(), 3, 2); // vec_5 contains 2, 2, 2, 1, 4, 2

// insert(position, start, end) - O(end-start+n-position)
vec_5.insert(vec_5.begin(), vec_2.begin(), vec_2.begin()+2); // vec_5 contains 100, 100, 2, 2, 2, 1, 4, 2

// assign() - overwrites values from the beginning
// assign(repetitions, value) - O(n') where n' is final size
vec_5.assign(1, 5); // vec_5 contains 5

// assign(start, end) - O(n') - n' is final size
vec_5.assign(vec_2.begin(), vec_2.begin()+3); // vec_5 contains 100, 100, 100

// erase() - erases elements at desired positions
// erase(position) - O(n-position) - due to moving elements after position
vec_5.erase(vec_5.begin()); // vec_5 contains 100, 100

// erase(start, end) - O(end-start+n-end) - due to elements erased and moving 
vec_5.erase(vec_5.begin(), vec_5.begin()+1); // vec_5 is 100

// swap() - O(1) - swaps the contents of vectors
vec_1.swap(vec_2); // vec_1 contains 100, 100, 100, 100 and vec_2 contains 0, 0, 0, 0, 0

// clear() - O(n) delete the vector
vec_5.clear(); // vec_5 is empty

// accumulate - O(n) accumulate(first, last, sum) 
// this function returns sum all elements lying in range [first, last) with variable sum
int sum = 0;
cout<<accumulate(vec_1.begin(), vec_1.end(), sum); // this will print 400
sum = 2;
cout<<accumulate(vec_1.begin(), vec_1.end(), sum); // this will print 402

// relational - O(n)
bool status;
status = (vec_3 == vec_4); // status contains 1
status = (vec_3 != vec_4); // status contains 0
status = (vec_1 < vec_2); // status contains 0, lexicographically compares elements from left
```


### List
A doubly linked list with discontiguous storage. 

```c++
// declaration and initialization
list<int> mylist; // mylist is a list variable
list<int> mylist_1 (4,100); // mylist_1 contains 100, 100, 100, 100
list<int> mylist_2 (mylist_1); // mylist_2 is a copy of mylist_1
int arr[] = {1,4,3};
list<int> mylist_3 (arr, arr+3); // mylist_3 contains 1, 4, 3

// size() - O(1) - returns size of list
int mylist_size = mylist_1.size(); // mylist_size contains 4

// empty() - O(1) - returns 1 if list is empty, 0 otherwise
bool mylist_empty = mylist.empty(); // mylist_empty contains 1

// front() - O(1) - returns reference to first element
int value = mylist_1.front(); // value contains 100

// back() - O(1) - returns reference to last element
value = mylist_1.back(); // value contains 100

// assign() - overwrites values from the beginning
// assign(repetitions, value) - O(n') - n' is final size
mylist_1.assign(1, 5); // mylist_1 contains 5

// assign(start, end) - O(n') - n' is final size
mylist_2.assign(mylist_3.begin(), mylist_3.end()); // mylist_2 contains 1, 4, 3

// push_front() - O(1) - inserts new element at the start
mylist_3.push_front(2); // mylist_3 contains 2, 1, 4, 3

// pop_front() - O(1) - removes first element
mylist_3.pop_front(); // mylist_3 contains 1, 4, 3

// push_back() - O(1) - inserts new element at the end
mylist_3.push_back(2); // mylist_3 contains 1, 4, 3, 2

// pop_back() - O(1) - removes last element
mylist_3.pop_back(); // mylist_3 contains 1, 4, 3

// insert() - inserts elements at desired positions
// insert(position, value) - O(n-position) due to moving elements after position
mylist_3.insert(mylist_3.begin(), 2); // mylist_3 contains 2, 1, 4, 3

// insert(position, repetitions, value) - O(repetitions+n-position)
mylist_3.insert(mylist_3.begin(), 2, 2); // mylist_3 contains 2, 2, 2, 1, 4, 3

// insert(position, start, end) - O(end-start+n-position)
mylist_3.insert(mylist_3.begin(), mylist_1.begin(), mylist_1.end()); // mylist_3 contains 5, 2, 2, 2, 1, 4, 3

// erase() - erases elements at desired positions
// erase(position) - O(n-position)
mylist_3.erase(mylist_3.begin()); // mylist_3 contains 2, 2, 2, 1, 4, 3

// erase(start, end) - O(end-start+n-position)
list<int>::iterator list_iter;
list_iter = mylist_3.begin();
list_iter++; // only unary operator works on this iterator as opposed to mylist_3.begin()+1
mylist_3.erase(mylist_3.begin(), list_iter); // mylist_3 contains 2, 2, 1, 4, 3

// swap() - O(1) - swaps the contents of lists
mylist_1.swap(mylist_2); // mylist_1 contains 1, 4, 3 and mylist_2 contains 5

// clear() - O(n) - delete the list
mylist_3.clear(); // mylist_3 is empty

// relational - O(n)
bool status;
status = (mylist_1 == mylist_2); // status contains 0
status = (mylist_1 != mylist_2); // status contains 1
status = (mylist_1 < mylist_2); // status contains 1, lexicographically compares elements from left
```


### Deque
A deque is doubly ended queue similar to vector with an additional benefit where elements can be added from both start and end.

```c++
// declaration and initialization
deque<int> deq; // deq is a deque variable
deque<int> deq_1 (5); // deq_1 is a deque of 0, 0, 0, 0, 0
deque<int> deq_2 (4,100); // deq_2 is a deque of 100, 100, 100, 100

deque<int>::iterator deq_iter; // deq_iter is an iterator for deque<int>
deq_iter = deq_2.begin(); // deq_2.begin() is the address of its first element, *deq_iter contains 100

deque<int> deq_3 (deq_2.begin(), deq_2.end()); // initializes from another deque
deque<int> deq_4 (deq_3); // copies entire deq_3 deque

int arr[] = {1,2,3};
deque<int> deq_5 (arr, arr+2); // initializes from arr array, deq_5 is a deque of 1, 2

// size() - O(1) - returns size of deque
int deq_size = deq_5.size(); // deq_size contains 2

// empty() - O(1) - returns 1 if deque is empty, 0 otherwise
bool deq_empty = deq.empty(); // deq_empty contains 1

// access - O(1)
int value = deq_5[0]; // similar to array, value contains 1

// front() - O(1) - returns reference to first element
value = deq_5.front(); // value contains 1 

// back() - O(1) - returns reference to last element
value = deq_5.back(); // value contains 2 

// insert() - inserts elements at desired positions
// insert(position, value) - O(n-position) due to moving elements after position
deq_5.insert(deq_5.begin()+1, 4); // deq_5 contains 1, 4, 2

// insert(position, repetitions, value) - O(repetitions+n-position)
deq_5.insert(deq_5.begin(), 3, 2); // deq_5 contains 2, 2, 2, 1, 4, 2

// insert(position, start, end) - O(end-start+n-position)
deq_5.insert(deq_5.begin(), deq_2.begin(), deq_2.begin()+2); // deq_5 contains 100, 100, 2, 2, 2, 1, 4, 2

// assign() - overwrites values from the beginning
// assign(repetitions, value) - O(n') - n' is final size
deq_5.assign(1, 5); // deq_5 contains 5

// assign(start, end) - O(n')
deq_5.assign(deq_2.begin(), deq_2.begin()+3); // deq_5 contains 100, 100, 100

// push_front() - O(1) - inserts new element at the start
deq_5.push_front(3); // deq_5 contains 3, 100, 100, 100

// pop_front() - O(1) - removes first element
deq_5.pop_front(); // deq_5 contains 100, 100, 100

// push_back() - O(1) - inserts new element at the end
deq_5.push_back(3); // deq_5 contains 100, 100, 100, 3

// pop_back() - O(1) - removes last element
deq_5.pop_back(); // deq_5 contains 100, 100, 100

// erase() - erases elements at desired positions
// erase(position) - O(n-position)
deq_5.erase(deq_5.begin()); // deq_5 contains 100, 100

// erase(start, end) - O(end-start+n-position)
deq_5.erase(deq_5.begin(), deq_5.begin()+1); // deq_5 contains 100

// swap() - O(1) - swaps the contents of deques
deq_1.swap(deq_2); // deq_1 contains 100, 100, 100, 100 and deq_2 contains 0, 0, 0, 0, 0

// clear() - O(n) - delete the deque
deq_5.clear(); // deq_5 is empty

// relational - O(n)
bool status;
status = (deq_3 == deq_4); // status contains 1
status = (deq_3 != deq_4); // status contains 0
status = (deq_1 < deq_2); // status contains 0, lexicographically compares elements from left
```
