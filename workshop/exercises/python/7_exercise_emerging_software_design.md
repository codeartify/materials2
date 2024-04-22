# Long Method / Function
 
> Exercise branch: **exercise_7**
> 
> Solution part 1: **exercise_7_part_1**
> 
> Solution part 2: **exercise_7_part_2**
>
> Solution part 3: **exercise_8**

## Exercise

### Apply the emerging software design algorithm (wrap + move to class) to separate concerns of ```count_contained_points``` into different classes!

## Exercise part 1
> Creation of points (including validation of inputs) 
> should not be done within ```count_contained_points```, as it is not in the responsibility of that method.
> 
> 1. Create a new ```Points``` class in a ```points.py``` file with a constructor ```Points(points[])```.
> 2. Use ```Parallel Change``` to replace the ```points```variable used within the second loop with ```Points(points).points```.

## Exercise part 2
> Wrap 
> * validation logic for coordinates (```validate_coordinates```) and 
> * creation of the ```Points``` object
> * into a static method ```create_points_from``` in the ```Points``` class.
> * ```count_points_within_circle``` should not contain any points creation or 
> validation logic anymore and instead take a ```Points``` object!
> 
> You may need Duplicate & Reduce, Parallel Change, and extract method to wrap the related concerns.

## Exercise part 3
> As a last step, we need to separate creation of points from counting contained points:
> * if you have an automatic ```ìnline``` refactoring, use it to inline ```count_contained_points``` 
> such that creation of points is done in the tests, not in the ```Circle``` anymore.
> * if you don't have an automatic ```ìnline``` refactoring, use ```Parallel Change``` 
> to replace ```count_contained_points``` step-by-step in the tests 
>  with ```circle.count_points_within_circle(Points.create_points_from(..., ...))```
> * finally, rename ```count_points_within_circle``` to ```count_contained_points```.