# Implementation
- Python
	- CPython implementation - https://github.com/python/cpython/blob/main/Include/cpython/dictobject.h
	```C
	struct _dictkeysobject {
	    Py_ssize_t dk_refcnt;
	
	    /* Size of the hash table (dk_indices). It must be a power of 2. */
	    uint8_t dk_log2_size;
	
	    /* Size of the hash table (dk_indices) by bytes. */
	    uint8_t dk_log2_index_bytes;
	
	    /* Kind of keys */
	    uint8_t dk_kind;
	
	    /* Version number -- Reset to 0 by any modification to keys */
	    uint32_t dk_version;
	
	    /* Number of usable entries in dk_entries. */
	    Py_ssize_t dk_usable;
	
	    /* Number of used entries in dk_entries. */
	    Py_ssize_t dk_nentries;
	
	    /* Actual hash table of dk_size entries. It holds indices in dk_entries,
	       or DKIX_EMPTY(-1) or DKIX_DUMMY(-2).
	
	       Indices must be: 0 <= indice < USABLE_FRACTION(dk_size).
	
	       The size in bytes of an indice depends on dk_size:
	
	       - 1 byte if dk_size <= 0xff (char*)
	       - 2 bytes if dk_size <= 0xffff (int16_t*)
	       - 4 bytes if dk_size <= 0xffffffff (int32_t*)
	       - 8 bytes otherwise (int64_t*)
	
	       Dynamically sized, SIZEOF_VOID_P is minimum. */
	    char dk_indices[];  /* char is required to avoid strict aliasing. */
	
	    /* "PyDictKeyEntry or PyDictUnicodeEntry dk_entries[USABLE_FRACTION(DK_SIZE(dk))];" array follows:
	       see the DK_ENTRIES() macro */
	};
	```
	- asdsad
	```C
	/* The ma_values pointer is NULL for a combined table
	 * or points to an array of PyObject* for a split table
	 */
	typedef struct {
	    PyObject_HEAD
	
	    /* Number of items in the dictionary */
	    Py_ssize_t ma_used;
	
	    /* Dictionary version: globally unique, value change each time
	       the dictionary is modified */
	#ifdef Py_BUILD_CORE
	    uint64_t ma_version_tag;
	#else
	    Py_DEPRECATED(3.12) uint64_t ma_version_tag;
	#endif
	
	    PyDictKeysObject *ma_keys;
	
	    /* If ma_values is NULL, the table is "combined": keys and values
	       are stored in ma_keys.
	
	       If ma_values is not NULL, the table is split:
	       keys are stored in ma_keys and values are stored in ma_values */
	    PyDictValues *ma_values;
	} PyDictObject;
	```
- C++
	- 
# Operations
# LeetCode Problems
- [[Two Sum]]
- [[Ransom Note]]