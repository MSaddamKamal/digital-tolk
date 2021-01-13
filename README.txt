# Comments On Code

Some functions are not properly handled the functions should return something in consistent format otherwise maintainability can be hard.
for example in book repository since the changeStatus function will not return array if the requested status and  old status are same so the error of undefined index can occur therefore try refactoring the changeStatus function accordingly otherwise if you don't want to refactor your code then the other way round in what i did in the code see comments.

Also some functions have logical error. for example if in ignoreExpired of book repository fails to save the job even then it will return true or throw exception, also some functions in helper file return value in the starting and after that the other logics are written which is surely not be executed.
index function of booking controller is not properly handled , if the conditions are not met the response variable will be undefined throwing error.

Validation and sanitization of inputs are not done

The variable names should be self explanatory for example use of variable like $cuser is ambiguous

Also Php variable naming conventions can be either camelcase or underscore separated, in code some variable names are not according to convention, if even you have your own naming convention then its should be consistent through out the code.

### Random Tips

Just a tip avoid using DB::table facade to do any query, instead use eloquent or query builder because if you query the database with DB::table facade then if you have some observers for the table then they will not run.


Just another tip , avoid making class base static helpers, instead make global function base helpers like laravel default helpers dd(), response() etc.
In my experience the static methods throw errors if they are called in background , for example when in queues.

Therefore function base helpers are more suitable infact it is easy to be made, a helper.php is made which is just autoloaded in composer.json file, and you can then make function in helper file which can be used globally without the need of aliasing them in config/app.php.


Although functions are by default public, so it depends upon the developer to declare public as its access type explicitly or not but in laravel coding convention
one should define the access type of any function explicitly.

Although use of syntax for arrays like array() and [] are same  but After php version 5.4 the use of array() has been depreciated, so since the code has also use [] syntax for arrays as well this means that php version is greater than 5.4 so for the sake of consistency the code should use either array() or [] but not both.

From maintainability point of view its is smarter to use curly braces with the if and else statements, for example if you want to add a second statement to the if or else clauses without remembering to add the curly braces, your code will break in unexpected and amusing ways. Also it some times creates ambiguity so {} must be used with conditional statements. For example
```bash
if(a == 1)
    if(b == 2)
        foo();
    else
        bar();

//and the other code

if(a == 1)
    if(b == 2)
        foo();
else
   bar();

```
both codes are same but if your editor does not indent the code well, then you will be confuse by the ambiguity in else statement.



