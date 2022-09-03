# Control Flow



There are two types of API functions in Nodejs:

1. asynchronous, non-blocking functions
2. synchronous, blocking functions



We need:

- a way to control the order in which the file reads are done
- some way to collect the result data for processing
- Some way to restrict the concurrency of the file read operations to conserve limited system resources
- A way to determine when all the reads necessary for the `do_next_part()` are completed



Control Flow functions are lightweight, generic piece of code which runs in between serveral async function calls and which take care of the necessary housekeeping to:

1. control the order of execution
2. collect data
3. limit concurrency
4. call the next step in the program



##### Pattern:

**#1 Series** an asynchronous for loop:

Basically, we take a set of items and call the series control flow function with the first item. The series launches one async() operation, and passes a callback to it. 



This results in serial execution of the asynchronous function calls. Control is passed back to the Node event loop after each async I/O operation is completed, then returned back when the operation is completed.

**Characteristics:**

- Runs a number of operations sequentially
- Only starts one async operation at a time (no concurrency)
- Ensures that the async function complete in order

**Variations:**

- The way in which the result is collected (manual or via a “stashing” callback)
- How error handling is done (manually in each subfunction, or via a dedicated, additional function)
- Since execution is sequential, there is no need for a “final” callback

**Tags:** sequential, no-concurrency, no-concurrency-control



**#2 Full Parallel** an asynchronous, parallel for loop:

In other cases, we just want to take a small set of operations, launch them all in parallel and then do something when all of them are complete.



Since this means that all the I/O operations are started in parallel immediately, we need to be careful not to exhaust the available resources. For example, you probably don't want to start 1000's of I/O operations, since there are operating system limitations for the number of open file handles. You need to consider whether launching parallel tasks is OK on a case-by-case basis.



**Characteristics:**

- Runs a number of operations in parallel
- Starts all async operations in parallel (full concurrency)
- No guarantee of order, only that all the operations have been completed

**Variations:**

- The way in which the result is collected (manual or via a “stashing” callback)
- How error handling is done (via the first argument of the final function, manually in each subfunction, or via a dedicated, additional function)
- Whether a final callback can be specified

Tags: parallel, full-concurrency, no-concurrency-control



**#3 Limited parallel** an asynchronous, parallel, concurrency limited for loop

In this case, we want to perform some operations in parallel, but keep the number of running I/O operations under a set limit:



**Characteristics:**

- Runs a number of operations in parallel
- Starts a limited number of operations in parallel (partial concurrency, full concurrency control)
- No guarantee of order, only that all the operations have been completed









