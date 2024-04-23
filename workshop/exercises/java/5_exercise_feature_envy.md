# Feature Envy
> Exercise branch: **exercise_5**
> 
> Solution branch: **exercise_6**
>  
> **Exercise**
> 
> ```Circle::format()``` formats both point (x, y) as well as radius as a string. 
> However, in this case, point and radius could actually provide own format() method to separate that concern from circle.
>
>* Extract a variable for the part of the string that formats a point “(x, y)” within Circle::format()
>* Wrap the right side of the variable in an own “formatPoint()” method 
>* Move this method to the ```Point``` with an automatic refactoring
>* Clean up and inline any unused parameters and variables, and rename the method to format
>* Do the same with ```Radius``` formatting
>
> There is another feature envy. Can you spot it?
>* Refactor it if you see it.
