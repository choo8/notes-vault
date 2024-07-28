On a **single-threaded** CPU, we execute a program containing `n` functions. Each function has a unique ID between `0` and `n-1`.

Function calls are **stored in a [call stack](https://en.wikipedia.org/wiki/Call_stack)**: when a function call starts, its ID is pushed onto the stack, and when a function call ends, its ID is popped off the stack. The function whose ID is at the top of the stack is **the current function being executed**. Each time a function starts or ends, we write a log with the ID, whether it started or ended, and the timestamp.

You are given a list `logs`, where `logs[i]` represents the `ith` log message formatted as a string `"{function_id}:{"start" | "end"}:{timestamp}"`. For example, `"0:start:3"` means a function call with function ID `0` **started at the beginning** of timestamp `3`, and `"1:end:2"` means a function call with function ID `1` **ended at the end** of timestamp `2`. Note that a function can be called **multiple times, possibly recursively**.

A function's **exclusive time** is the sum of execution times for all function calls in the program. For example, if a function is called twice, one call executing for `2` time units and another call executing for `1` time unit, the **exclusive time** is `2 + 1 = 3`.

Return _the **exclusive time** of each function in an array, where the value at the_ `ith` _index represents the exclusive time for the function with ID_ `i`.
# Solution Complexity
# Thought Process 
# Solution
- asdasd
```Python
class Solution:
	def exclusiveTime(self, n: int, logs: List[str]) -> List[int]:
		exclusive_time = [0] * n
		stack = []
		prev_end = None

		for log in logs:
			func_id, state, timestamp = log.split(":")
			func_id, timestamp = int(func_id), int(timestamp)

			# Call to another func_id or recursive call
			if len(stack) == 0 or stack[-1][0] != func_id or state == "start":
				# If previous function not updated before
				if len(stack) > 0:
					if stack[-1][2] is None:
						stack[-1] = [stack[-1][0], stack[-1][1], timestamp - 1]
					else:
						stack[-1][2] += timestamp - prev_end - 1
				stack.append([func_id, timestamp, None])
			# End current function call on stack
			else:
				func_id, init, end = stack.pop()

				# No other functions calls between starting and ending
				if end is None:
					exclusive_time[func_id] += timestamp - init + 1
				else:
					exclusive_time[func_id] += end - init + 1 + timestamp - prev_end

				prev_end = timestamp

		return exclusive_time
```