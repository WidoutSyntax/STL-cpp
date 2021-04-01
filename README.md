# Contents
1. Standard Template Library

# Standard Template Library
The Standard Template Library(STL) is a set of C++ template classes to provide common data structures. One can easily implement data structures like stack, queue, list, etc and one important thing is using STL reduces programming time as well. 

The C++ STL grouped into following three categories
1) Sequences              - [Vector](#Vector), [List](#List), [Doubly ended queue](#Deque)<br/>
2) Container Adapters     - [Stack](#Stack), [Queue](#Queue), [Priority Queue](#Priority-Queue)<br/>
3) Associative Containers - [Set](#Set), [Unordered Set](#Unordered-Set), [Map](#Map), [Unordered Map](#Unordered-Map),  
                            Multimap, Multiset, Bitset   

There are some STL that can be used as well - [String](#String), [Pair](#Pair)<br/>
Usage of several STL classes are illustrated. For convenience and ease of learning, examples are also provided along with syntax.

## Sequences
### Vector
A vector is similar to an array but with dynamic size. Elements can be accessed in O(1) and insert, delete operations will take O(n) time.

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
// this function returns sum of all elements lying in range [first, last) with variable sum
int sum = 0;
cout<<accumulate(vec_1.begin(), vec_1.end(), sum); // this will print 400
sum = 2;
cout<<accumulate(vec_1.begin(), vec_1.end(), sum); // this will print 402

// resize - O(n)
vec.resize(5); // this will print 0 0 0 0 0
vec.resize(7, 1); // this will print 0 0 0 0 0 1 1
vec.resize(4, 1); //this will print 0 0 0 0

// fill - O(n)
fill(vec.begin(), vec.end(), 9); // this will print 9 9 9 9

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
## Container Adapters
### Stack
It is a last in first out container.

```c++
// declaration and initialization
stack<int> sta; // sta is a stack variable
vector<int> vec (2,100);
stack<int, vector<int> > sta_1 (vec); // sta_1 is a copy of vec

// empty() - O(1) - returns 1 if stack is empty, 0 otherwise
bool sta_empty = sta.empty(); // sta_empty contains 1

// size() - O(1) - returns size of stack
int sta_size = sta_1.size(); // sta_size contains 2

// top() - O(1) - returns reference to top element
int sta_top = sta_1.top(); // sta_top is 100

// push() - O(1) - pushes new element from the top
sta.push(5); // sta is 5
sta_1.push(5); // sta_1 is 5, 100, 100

// pop() - O(1) - removes top element
sta_1.pop(); // sta_1 is 100, 100

// swap() - O(1) - swaps the contents of stacks
sta.swap(sta_1); // sta_1 is 5, sta is 100, 100

// relational - O(n)
bool status;
status = (sta == sta_1); // status contains 0
status = (sta != sta_1); // status contains 1
status = (sta < sta_1); // status contains 0, lexicographically compares elements from left
```

### Queue
It is a first in first out container.

```c++
// declaration and initialization
queue<int> que; // que is a queue variable
vector<int> vec (2,100);
queue<int> que_1;
for(int i=0; i<vec.size(); i++)
    que_1.push(vec[i]);

// empty() - O(1) - returns 1 if queue is empty, 0 otherwise
bool que_empty = que.empty(); // que_empty contains 1

// size() - O(1) - returns size of queue
int que_size = que_1.size(); // que_size contains 2

// front() - O(1) - returns reference to first element
int que_front = que.front(); // que_front is 100

// push() - O(1) - pushes new element from the end
que.push(5); // que is 5
que_1.push(5); // que_1 is 100, 100, 5

// back() - O(1) - return reference to last element
int que_back = que.back(); // que_back is 5

// pop() - O(1) - removes first element
que_1.pop(); // que_1 is 100, 5

// swap() - O(1) - swaps the contents of stacks
que.swap(que_1); // que_1 is 5, que is 100, 5

// relational - O(n)
bool status;
status = (que == que_1); // status contains 0
status = (que != que_1); // status contains 1
status = (que < que_1); // status contains 0, lexicographically compares elements from left 
```

### Priority Queue
It is implemented as max heap by default. We can also tweak it to implement as min heap. It will sort itself after adding an elemnt in descending order. 

```c++
// declaration and initialization
priority_queue<int> pq; // pq is a priority_queue variable
int arr[] = {3,6,4};
priority_queue<int> pq_1 (arr, arr+3); // pq_1 contains 6, 4, 3

// empty() - O(1) - returns 1 if priority_queue is empty, 0 otherwise
bool pq_empty = pq.empty(); // pq_empty contains 1

// size() - O(1) - returns size of priority_queue
int pq_size = pq_1.size(); // pq_size contains 3

// top() - O(1) - return reference to first element
int pq_front = pq_1.top(); // pq_front is 6

// push() - O(log n) - pushes element into priority queue
pq.push(5); // pq is 5
pq_1.push(5); // pq_1 is 6, 5, 4, 3

// pop() - O(log n) removes first element
pq_1.pop(); // pq_1 is 5, 4, 3

// swap() - O(1) - swaps the contents of priority queues
pq.swap(pq_1); // pq_1 is 5, pq is 5, 4, 3

// changing order to least element first
priority_queue<int, vector<int>, greater<int> > pq_2;
pq_2.push(5);
pq_2.push(3); // pq_2 is 3, 5
```

## Associative Containers
### Set
It is implemented as Red-Black tree. It contains unique elements with least element first by default.

```c++
// declaration and initialization
set<int> myset; // myset is a set variable
int arr[] = {4,2,1,2};
set<int> myset_1 (arr, arr+4); // myset_1 is a set of 1, 2, 4
set<int> myset_2 (myset_1); // myset_2 is a copy of myset_1

// empty() - O(1) - returns 1 if set is empty, 0 otherwise
bool myset_empty = myset.empty(); // myset_empty contains 1

// size() - O(1) - returns size of set
int myset_size = myset_1.size(); // myset_size contains 3

// insert() - inserts new elements into the set
// insert(value) - O(log n)
myset.insert(3); // myset contains 3

// insert(start, end) - O(N log(N+n)) where N = end-start
int arr_1[] = {4,3,4};
myset_1.insert(arr_1, arr_1+3); // myset_1 contains 1, 2, 3, 4

// clear() - O(n) - delete the set
myset.clear(); // myset is empty

// erase() - erase elements at desired positions
myset.insert(arr_1, arr_1+3); // myset contains 3, 4
// erase(position) - O(1)
set<int>::iterator set_iter;
set_iter = myset.begin();
myset.erase(set_iter); // myset contains 4

// erase(value) - O(log n)
myset.insert(arr_1, arr_1+3); // myset contains 3, 4
myset.erase(4); // myset contains 3

// erase(start, end) - O(end-start)
myset.insert(arr_1, arr_1+3); // myset contains 3, 4
myset.erase(myset.begin(), myset.end()); // myset is empty

// find(value) - O(log n) - returns iterator to element if found, end() otherwise
set_iter = myset_1.find(3); // *set_iter outputs 3
set_iter = myset_1.find(5); // set_iter is myset_1.end()

// count(value) - O(log n) returns 1 if the element is present, 0 otherwise
int set_count = myset_1.count(4); // set_count contains 1
set_count = myset_1.count(10); // set_count contains 0

// lower_bound(value) - O(log n) - returns iterator to element equal to or immediately greater than value. Returns end otherwise
set_iter = myset_1.lower_bound(3); // *set_iter outputs 3
set_iter = myset_2.lower_bound(3); // *set_iter outputs 4

// upper_bound(value) - O(log n) - returns iterator to element immediately greater than value. Returns end otherwise
set_iter = myset_1.upper_bound(3); // *set_iter outputs 4
set_iter = myset_2.upper_bound(3); // *set_iter outputs 4

// equal_range(value) - O(log n) - returns pair of iterators to elements equal to value. In other words, returns lower_bound and upper_bound as a pair.
pair<set<int>::iterator,set<int>::iterator> set_iter_pair;
set_iter_pair = myset_1.equal_range(3); // *(set_iter_pair.first) outputs 3 and *(set_iter_pair.second) outputs 4

// swap() - O(1) - swaps the contents of sets
myset_1.swap(myset_2); // myset_1 contains 1, 2, 4 and myset_2 contains 1, 2, 3, 4

// changing order to greatest element first
set<int, greater<int> > myset_3 (arr, arr+4); // myset_3 contains 4, 2, 1
```

### Unordered Set
It is implemented as hash map. It contains unique elements with no specific order.

```c++
// declaration and initialization
unordered_set<int> myset; // myset is an unordered set variable
int arr[] = {4,2,1,2};
unordered_set<int> myset_1 (arr, arr+4); // myset_1 is an unordered set of 2, 1, 4 (random order)
unordered_set<int> myset_2 (myset_1); // myset_2 is a copy of myset_1

// empty() - O(1) - returns 1 if unordered set is empty, 0 otherwise
bool myset_empty = myset.empty(); // myset_empty contains 1

// size() - O(1) - returns size of unordered set
int myset_size = myset_1.size(); // myset_size contains 3

// insert() - inserts new elements into the unordered set
// insert(value) - O(1) on average
myset.insert(3); // myset contains 3

// insert(start, end) - O(N) where N = end-start
int arr_1[] = {4,3,4};
myset_1.insert(arr_1, arr_1+3); // myset_1 contains 4, 2, 1, 3

// clear() - O(n) - delete the unordered set
myset.clear(); // myset is empty

// erase() - erase elements at desired positions
myset.insert(arr_1, arr_1+3); // myset contains 4, 3
// erase(position) - O(1)
unordered_set<int>::iterator set_iter;
set_iter = myset.find(4);
myset.erase(set_iter); // myset contains 3

// erase(value) - O(1)
myset.insert(arr_1, arr_1+3); // myset contains 3, 4
myset.erase(4); // myset contains 3

// erase(start, end) - O(end-start)
myset.insert(arr_1, arr_1+3); // myset contains 3, 4
myset.erase(myset.begin(), myset.end()); // myset is empty

// find(value) - O(1) - returns iterator to element if found, end() otherwise
set_iter = myset_1.find(3); // *set_iter outputs 3
set_iter = myset_1.find(5); // set_iter is myset_1.end()

// count(value) - O(1) returns 1 if the element is present, 0 otherwise
int set_count = myset_1.count(4); // set_count contains 1
set_count = myset_1.count(10); // set_count contains 0

// equal_range(value) - O(1) - returns pair of iterators to elements equal to value. In other words, returns lower_bound and upper_bound as a pair.
pair<unordered_set<int>::iterator,unordered_set<int>::iterator> set_iter_pair;
set_iter_pair = myset_1.equal_range(3); // *(set_iter_pair.first) outputs 3 and *(set_iter_pair.second) outputs 4

// swap() - O(1) - swaps the contents of unordered sets
myset_1.swap(myset_2); // myset_1 contains 4, 2, 1 and myset_2 contains 4, 2, 1, 3
```

### Map
This container has key value pairs with least value key in first position. It is implemented as Red-Black tree.

```c++
// declaration and initialization
map<int, int> mymap;
int keys[] = {3,1};
int values[] = {4,2};
map<int, int> mymap_1;
mymap_1[keys[0]] = values[0];
mymap_1[keys[1]] = values[1]; // mymap_1 contains {1,2},{3,4} pairs
map<int,int> mymap_2 (mymap_1); // mymap_2 is a copy of mymap_1

// empty() - O(1) - returns 1 if map is empty, 0 otherwise
bool mymap_empty = mymap.empty(); // mymap_empty contains 1

// size() - O(1) - returns size of map
int mymap_size = mymap_1.size(); // mymap_size contains 2

// insert() - inserts new elements into the map
// insert(pair) - O(log n) returns a pair. First is iterator to inserted element or already existing key and second is boolean - true if inserted or false if present already.
pair<map<int,int>::iterator, bool> map_insert;
map_insert = mymap.insert(pair<int, int>(1,6)); // map_insert.second contains true, map_insert.first points to element inserted, mymap contains {1,6}

map_insert = mymap_1.insert(pair<int, int>(1,6)); // map_insert.second contains false, map_intert.first points to the pair {1,2}. mymap_1 contains {1,2},{3,4}

// insert(start, end) - O(N log(N+n)) where N = end-start
mymap.insert(mymap_1.begin(), mymap_1.end()); // mymap contains {1,6}, {3,4}

// clear() - O(n) - delete the map
mymap.clear(); // mymap is empty

// erase() - erase elements at desired positions
mymap_1.insert(pair<int, int>(5,6)); // mymap_1 contains {1,2}, {3, 4}, {5,6}
// erase(position) - O(1)
map<int,int>::iterator map_iter;
map_iter = mymap_1.begin();
mymap_1.erase(map_iter); // mymap_1 contains {3,4}, {5,6}

// erase(key) - O(log n)
mymap_1.insert(pair<int, int>(1,2)); // mymap_1 contains {1,2}, {3, 4}, {5,6}
mymap_1.erase(1); // mymap_1 contains {3, 4}, {5,6}

// erase(start, end) - O(end-start)
mymap.insert(pair<int, int>(1,2)); // mymap contains {1,2}
mymap.erase(mymap.begin(), mymap.end()); // mymap is empty

// find(key) - O(log n) - returns iterator to element if found, end() otherwise
map_iter = mymap_1.find(3); // map_iter->first outputs 3, map_iter->second outputs 4
map_iter = mymap_1.find(1); // map_iter is mymap_1.end()

// count(key) - O(log n) returns 1 if the element is present, 0 otherwise
int map_count = mymap_1.count(3); // map_count contains 1
map_count = mymap_1.count(1); // map_count contains 0

// lower_bound(key) - O(log n) - returns iterator to element equal to or immediately greater than value. Returns end otherwise
map_iter = mymap_1.lower_bound(3); // map_iter->first outputs 3, map_iter->second outputs 4
map_iter = mymap_1.lower_bound(1); // map_iter->first outputs 3, map_iter->second outputs 4

// upper_bound(key) - O(log n) - returns iterator to element immediately greater than value. Returns end otherwise
map_iter = mymap_1.upper_bound(3); // // map_iter->first outputs 5, map_iter->second outputs 6

// equal_range(key) - O(log n) - returns pair of iterators to elements equal to value. In other words, returns lower_bound and upper_bound as a pair.
pair<map<int,int>::iterator,map<int,int>::iterator> map_iter_pair;
map_iter_pair = mymap_1.equal_range(3); // map_iter_pair.first->first outputs 3 and map_iter_pair.second->first outputs 5

// swap() - O(1) - swaps the contents of maps
mymap_1.swap(mymap_2); // mymap_1 contains {1,2}, {3, 4} and mymap_2 contains {3, 4}, {5,6}
```

### Unordered Map
This container stores key value pairs. It is implemented as hash map.

```c++
// declaration and initialization
unordered_map<int, int> mymap;
int keys[] = {3,1};
int values[] = {4,2};
unordered_map<int, int> mymap_1;
mymap_1[keys[0]] = values[0];
mymap_1[keys[1]] = values[1]; // mymap_1 contains {3,4}, {1,2} pairs
unordered_map<int,int> mymap_2 (mymap_1); // mymap_2 is a copy of mymap_1

// empty() - O(1) - returns 1 if unordered map is empty, 0 otherwise
bool mymap_empty = mymap.empty(); // mymap_empty contains 1

// size() - O(1) - returns size of unordered map
int mymap_size = mymap_1.size(); // mymap_size contains 2

// insert() - inserts new elements into the unordered map
// insert(pair) - O(1) returns a pair. First is iterator to inserted element or already existing key and second is boolean - true if inserted or false if present already.
pair<unordered_map<int,int>::iterator, bool> map_insert;
map_insert = mymap.insert(pair<int, int>(1,6)); // map_insert.second contains true, map_insert.first points to element inserted, mymap contains {1,6}

map_insert = mymap_1.insert(pair<int, int>(1,6)); // map_insert.second contains false, map_intert.first points to the pair {1,2}. mymap_1 contains {3,4}, {1,2}

// insert(start, end) - O(N) where N = end-start
mymap.insert(mymap_1.begin(), mymap_1.end()); // mymap contains {1,6}, {3,4}

// clear() - O(n) - delete the unordered map
mymap.clear(); // mymap is empty

// erase() - erase elements at desired positions
mymap_1.insert(pair<int, int>(5,6)); // mymap_1 contains {3, 4}, {1,2}, {5,6}
// erase(position) - O(1)
unordered_map<int,int>::iterator map_iter;
map_iter = mymap_1.find(3);
mymap_1.erase(map_iter); // mymap_1 contains {1,2}, {5,6}

// erase(key) - O(1) - where num is number of occurrences of value
mymap_1.insert(pair<int, int>(3,4)); // mymap_1 contains {1,2}, {5,6}, {3, 4}
mymap_1.erase(1); // mymap_1 contains {5,6}, {3, 4}

// erase(start, end) - O(end-start)
mymap.insert(pair<int, int>(1,2)); // mymap contains {1,2}
mymap.erase(mymap.begin(), mymap.end()); // mymap is empty

// find(key) - O(1) - returns iterator to element if found, end() otherwise
map_iter = mymap_1.find(3); // map_iter->first outputs 3, map_iter->second outputs 4
map_iter = mymap_1.find(1); // map_iter is mymap_1.end()

// count(key) - O(1) returns 1 if the element is present, 0 otherwise
int map_count = mymap_1.count(3); // map_count contains 1
map_count = mymap_1.count(1); // map_count contains 0

// equal_range(key) - O(1) - returns pair of iterators to elements equal to value. In other words, returns lower_bound and upper_bound as a pair.
pair<unordered_map<int,int>::iterator,unordered_map<int,int>::iterator> map_iter_pair;
map_iter_pair = mymap_1.equal_range(3); // map_iter_pair.first->first outputs 3 and map_iter_pair.second->first outputs 5

// swap() - O(1) - swaps the contents of unordered maps
mymap_1.swap(mymap_2); // mymap_1 contains {3,4}, {1,2} and mymap_2 contains {5,6}, {3, 4}
```

## Useful
### String

```c++
// declaration and initialization
string s;
string s_1 = "random string";
string s_2(s_1.begin(), s_1.begin() + 3); // s_2 contains ran
string s_3(5, '#'); // s_3 contains #####
string s_4(s_1); // s_4 is a copy of s_1

// length() - returns length of string
int s_length = s_3.length(); // s_length is 5

// access
char s_char = s_1[0]; // s_char contains r
s_4[0] = 'f'; // s_4 contains fandom string

// clear() - deletes the string
s_4.clear(); // s_4 is empty

// empty() - returns 1 if empty, 0 otherwise
int s_empty = s_4.empty(); // s_empty contains 1

//concatenate
s_2 += "d"; //s_2 contains rand

//append() - concatenates string to the end
s_4 = "om";
s_2.append(s_4); // s_2 contains random
// append(start, end)
s_2.append(s_3.begin(), s_3.begin() + 1); // s_2 contains random#

// assign() - replaces current string
s.assign(s_3); // s contains #####
// assign(start, end)
s.assign(s_2.begin(), s_2.end()); // s contains random#

// insert() - inserts string after position
// insert(position, string)
s.insert(0, s_3); // s contains #####random#
// insert(position, start, end)
s.insert(s.end(), s_3.begin(), s_3.end() - 1); // s contains #####random#####

// erase() - deletes character at the given position(s)
// erase(position)
s.erase(s.begin()); // s contains ####random#####
// erase(start, end)
s.erase(s.begin(), s.begin() + 4); // s contains random#####

// replace() - replaces from start to end with string
// replace(start, end, string)
s.replace(s.begin(), s.begin() + 3, s_3); // s contains #####dom#####
// replace(start, end, start_1, end_1)
s.replace(s.begin() + 1, s.end(), s_2.begin(), s_2.end()); // s contains #random#

// find() - returns position of occurrence of string, -1 otherwise
// find(string)
int position;
position = s.find("random"); // position contains 1
position = s.find("fandom");   // position contains -1
// find(string, position) - searches for occurrence from position. By default, position is 0 in the above case
position = s.find("random", 2); // position contains -1

// swap(string) - swaps contents of the strings
s.swap(s_2); // s contains random#, s_2 contains #random#

// relational operators
bool status;
status = (s_1 == s_4); // status contains 0
status = (s_1 != s_4); // status contains 1
status = (s_1 < s_4); // status contains 0

// conversions
// stoi - convert string to integer
int num = stoi("1998");

// stoll - convert string to long long int
long long int num_1 = stoll("19981998");

// stof - convert string to float
float num_2 = stof("1998.26");

// stod - convert string to double
double num_3 = stod("19981998.26");

// to_string - convert to string
s = to_string(num_3); // s contains 19981998.26

// transform() - convert string to upper or lower case
transform(s_4.begin(), s_4.end(), s_4.begin(), ::toupper);

// s1.compare(s2)
/*compare() - 0   : if strings are equal
            < 0 : (len(s1) < len(s2)) or (first different char of s1 < char of s2)
            > 0 : (len(s1) > len(s2)) or (first different char of s1 > char of s2)

*/
```

### Pair

```c++
pair<int, int> p; // declaration
pair<int, int> p_1 (3,5); // initialization
p = make_pair(2,4); // assign
int first, second;
first = p.first; // first contains 2
second = p.second; // second contains 4
p = {3, 5}; //p.first is 3 and p.second is 5
```
