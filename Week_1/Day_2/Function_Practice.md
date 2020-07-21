# Best Function Practice
We learn about what is the best practice of writing a [function](https://eloquentjavascript.net/03_functions.html#h_eVDWIAuyBK)

If you can, write a pure function = it only does one thing and one thing only

And it is better if the function end goal is to return a value, and not just to print to console

Return value = you can work with the return value

Print = hard coded, less adeptative

## The 5 important rules

> 1. Give your functions precise verb/action based names
> 2. Use camelCasedNames (like this one)
> 3. Properly indent the function code
> 4. Functions should focus on a single task: returning a value or causing a side effect. Break your function into additional smaller functions if you find it doing two or more things
>    * One single task could be to compute and return a value (eg: zeroPad)
>    * Another single task could be to perform a side effect such as logging a message to the screen (eg: printFarmInventory)
> 5. Data needed by Functions should be passed in as parameters/arguments (i.e. local scope) instead of being accessed directly
