# web perf analysis tools

## webpack "dynamic import chaos monkey"

- builds the codebase
- removes a single dynamic `import()` at a time
- rebuilds the codebase
- checks the diff
- ideally, the only diff should be the disapperance of the dynamic chunk whose `import` was removed
- any other diff means that some imported variables/methods are in an indivisible parent chunk, instead of being directly in the dynamic chunk.
This variables/methods should be moved down to the async child chunk.
