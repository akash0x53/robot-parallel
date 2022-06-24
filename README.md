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
This script takes two arguments, “number of groups” and which group do you want execute. 
Note that passing argument is different here, e.g “3:1”. 
Above snippet will divide suite into 3 groups and run 1st group.

Now,if you want to execute 2nd group you will run

```
akash@SkyFall:~/robot$ robot --dryrun --prerunmodifier SplitSuite.py:3:2 tests/
```

How to use SplitSuite_v2.py?
---

```
bd@testing:~/robot$ robot --dryrun --prerunmodifier SplitSuite.py:3:1:4 tests/
```
This script takes three arguments, “number of groups”, which group do you want execute and the max level of depth the splitter will go through in your tests folder before performing the splitter.

Why version 2?
---
A use case explaining the differences between the 2 versions may help
```
tests/
   - 100_UI_testing/
         - Login.robot
         - Checkout.robot
   - 200_API_testing/
         - 201_Catalog/
            - Catalog.robot
            - Categories.robot
            - Images.robot
            - Upselling.robot
            - Prices.robot
         - Cart.robot
```
In the above example, the script version 1 would bring to 2 splits, where the first one would contain Login.robot and Checkout.robot, while the second split would contain a lot more suites to run.

The second version of the script lets you flatten the tree structure to a specified level. Let's say level 2. The script will take all the single .robot files and after that it will splits the suites into 2 runs.
