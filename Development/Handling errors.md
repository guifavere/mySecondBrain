# Handling errors

Typically, we should aim to reserve try-catch blocks for operations that interact with the outside world.

When dispatch errors:
1. When we're working on a library, or a tool to be used by other developers.
2. When we encounter errors that we don't expect or know how to deal with.