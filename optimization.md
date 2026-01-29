## For /events
- The bottleneck was a wasteful computation loop iterating 3 million times performing modulo operations with no purpose.
- I removed this entire loop (lines 64-66). 
- Performance improved because the CPU no longer wastes time on 3 million unnecessary arithmetic operations before responding to the request.

## For /my-events
- The bottleneck was a dummy computation loop iterating 1.5 million times incrementing a counter that was never used.
- I removed this entire loop. 
- Performance improved because the CPU no longer executes 1.5 million useless increment operations, allowing the route to return the database results immediately after the query completes.

Both routes had artificial delays that blocked the response. Removing them eliminated unnecessary CPU cycles, reducing response time from hundreds of milliseconds to just the database query time.
