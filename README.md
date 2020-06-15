# Cabal

this project has a couple of goals:

1. break [lich](https://gswiki.play.net/Horned_Cabal) into groups of files
2. prune deadcode
3. create a way forward for development
4. provide a bin `gem`
5. use more gems to do the heavy lifting instead of own-rolled code

My previous attempts at a complete rewrite have been seriously hampered by MapDB's absolute necessity to navigate the game world in a reasonable manner, and the fact than any Lich api can exist within it.  Without a way to isolate and refactor we will never be able to improve.

**backwards compatibility with all systems and features is not a design goal**

### Differences Between Cabal & Lich

1. the `Script` class is a true `Thread` object
2. `Script.run` returns a handle to the `Script` instance
3. scripts have `exit_codes` like processes in *nix environments
4. scripts use significantly fewer threads (has taken my average playing session from 30% memory usage to 18%)
5. scripts are currently not "pausable"
6. significantly fewer tight loops
7. `wait_while` accepts a `timeout:` keyword
8. `wait_until` accepts a `timeout:` keyword