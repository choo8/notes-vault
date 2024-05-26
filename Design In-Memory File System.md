Design a data structure that simulates an in-memory file system.

Implement the FileSystem class:

- `FileSystem()` Initializes the object of the system.
- `List<String> ls(String path)`
    
    - If `path` is a file path, returns a list that only contains this file's name.
    - If `path` is a directory path, returns the list of file and directory names **in this directory**.
    
    The answer should in **lexicographic order**.
- `void mkdir(String path)` Makes a new directory according to the given `path`. The given directory path does not exist. If the middle directories in the path do not exist, you should create them as well.
- `void addContentToFile(String filePath, String content)`
    - If `filePath` does not exist, creates that file containing given `content`.
    - If `filePath` already exists, appends the given `content` to original content.
- `String readContentFromFile(String filePath)` Returns the content in the file at `filePath`.
# Solution Complexity
- $O(n + k)$ time complexity for `ls` operation and $O(k)$ time complexity for `mkdir`, `addContentToFile` and `readContentFromFile` operations
- $O(nk)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class FileSystem:
	def __init__(self):
		self.trie = {}

	def ls(self, path: str) -> List[str]:
		cur_trie = self.trie
		for directory in path.split("/"):
			if directory != "":
				cur_trie = cur_trie[directory]
		if "*" in cur_trie:
			return [directory]
		else:
			return [directory for directory in sorted(cur_trie.keys())]

	def mkdir(self, path: str) -> None:
		cur_dir = self.trie
		for directory in path.split("/"):
			if directory != "":
				if directory not in cur_dir:
					cur_dir[directory] = {}
				cur_dir = cur_dir[directory]

	def addContentToFile(self, filePath: str, content: str) -> None:
		cur_dir = self.trie
		for directory in filePath.split("/"):
			if directory != "":
				if directory not in cur_dir:
					cur_dir[directory] = {}
				cur_dir = cur_dir[directory]
		# New file
		if "*" not in cur_dir:
			cur_dir["*"] = {}
			cur_dir["content"] = content
		else:
			cur_dir["content"] += content

	def readContentFromFile(self, filePath: str) -> str:
		cur_dir = self.trie
		for directory in filePath.split("/"):
			if directory != "":
				cur_dir = cur_dir[directory]
		return cur_dir["content"]

# Your FileSystem object will be instantiated and called as such:
# obj = FileSystem()
# param_1 = obj.ls(path)
# obj.mkdir(path)
# obj.addContentToFile(filePath,content)
# param_4 = obj.readContentFromFile(filePath)
```