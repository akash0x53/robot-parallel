# robot-parallel
Run robot test suite parallel, example.

How to use SplitSuite.py?
---

```
akash@SkyFall:~/robot$ robot --dryrun --prerunmodifier SplitSuite.py:3:1 tests/
Visiting SUITE: Tests
Total number of suites: 36
number of suites: 12.0
Suites in this part: 12
...
```

This script takes two argument, “number of groups” and which group do you want execute. 
Note that passing argument is different here, e.g “3:1”. 
Above snippet will divide suite into 3 groups and run 1st group.

Now,if you want to execute 2nd group you will run

```
akash@SkyFall:~/robot$ robot --dryrun --prerunmodifier SplitSuite.py:3:2 tests/
```
