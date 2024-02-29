# Implementation
- Python
	- CPython Implementation - https://github.com/python/cpython/blob/main/Include/cpython/listobject.h
	```C
	typedef struct {
		PyObject_VAR_HEAD
	    /* Vector of pointers to list elements.  list[0] is ob_item[0], etc. */
	    PyObject **ob_item;
	
	    /* ob_item contains space for 'allocated' elements.  The number
	     * currently in use is ob_size.
	     * Invariants:
	     *     0 <= ob_size <= allocated
	     *     len(list) == ob_size
	     *     ob_item == NULL implies ob_size == allocated == 0
	     * list.sort() temporarily sets allocated to -1 to detect mutations.
	     *
	     * Items must normally not be NULL, except during construction when
	     * the list is not yet visible outside the function that builds it.
	     */
	    Py_ssize_t allocated;
	} PyListObject;
	```
	- `PyObject_VAR_HEAD` is a macro used when declaring new types which represent objects with a length that varies from instance to instance. It expands to `PyVarObject ob_base;`, where `PyVarObject` is an extension to `PyObject` that adds the `ob_size` field.
		```C
		typedef struct {
		    PyObject ob_base;
		    Py_ssize_t ob_size; /* Number of items in variable part */
		} PyVarObject;
		```
- C++
	- Static (fixed-length) arrays could be implemented with the in-built C++ types `<T>[]`
	```C++
	#define ARR_LEN 10
	
	int main() {
		int arr[ARR_LEN] = {0};
		
		return 0;
	}
	```
	- Arrays could also be implemented with `vectors`, which are dynamic arrays
	```C++
	#include <vector>
	
	int main() {
		std::vector<int> v = {1, 2, 3, 4, 5};
		
		return 0;
	}
	```
# Operations
- Access
- Search
- Search (sorted array)
- Insert
- Insert (at the end)
- Remove
- Remove (at the end)
# LeetCode Problems
- [[Two Sum]]
- [[Best Time to Buy and Sell Stock]]
- [[Product of Array Except Self]]
- [[Maximum Subarray]]
- [[Contains Duplicate]]
- [[Maximum Product Subarray]]
- [[Search in Rotated Sorted Array]]
- [[3Sum]]
- [[Container With Most Water]]
- [[Sliding Window Maximum]]
- [[Valid Anagram]]
- [[Valid Palindrome]]
- [[Longest Substring Without Repeating Characters]]
- [[Longest Repeating Character Replacement]]
- [[Find All Anagrams in a String]]
- [[Minimum Window Substring]]
- [[Group Anagrams]]
- [[Longest Palindromic Substring]]
- [[Majority Element]]
- [[Roman to Integer]]
- [[Backspace String Compare]]
- [[Longest Common Prefix]]
- [[Move Zeroes]]
- [[Squares of Sorted Array]]
- [[Sort Colors]]
- [[String to Integer (atoi)]]
- [[Gas Station]]
- [[Next Permutation]]
- [[Find Duplicate Number]]
- [[Longest Consecutive Sequence]]
- [[Rotate Array]]
- [[Contiguous Array]]
- [[Subarray Sum Equals K]]
- [[Random Pick with Weight]]
- [[Largest Number]]
- [[3Sum Closest]]
- [[Zigzag Conversion]]