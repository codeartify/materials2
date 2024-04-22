# Long Method / Function and Loop Split
> **Exercise**
> 
> Exercise branch: **exercise_6**
>
> Solution branch: **exercise_7**
> 
> The ```countContainedPoints``` method has two separate concerns:
> * Concern 1: creation of points (including validation of inputs)
> * Concern 2: counting the number of points contained within the circle.
> 
> To solve this, split the loop into two separate loops:
>  * Loop 1 creates a list of ```Point```s with a ```Point``` for each ```xCoords[i]``` and ```yCoords[i]```
>  * Loop 2 iterates over this list of points and counts points contained within the circle.
