# Long Method / Function
> **Exercise**
> 
> Exercise branch: **exercise_7**
>
> Solution branch: **exercise_8**
> 
> Creation of points (including validation of inputs) should happen outside of “countContainedPoints” as it is not in the responsibility of that method.
> 
> * Create a new ```Points``` class with a constructor ```Points(List<Point> points)``` and one public method ```public List<Point> asList()``` that returns the list passed to the constructor.
> * Instantiate ```Points points2 = new Points(points)``` right after creation of the ```points``` list.
> * Replace the ```points``` variable within the second loop with ```points2.asList()```. Make sure to run the tests. 
> * wrap validation logic for coordinates,
creation of the points array, and creation of the Points object into a static method 
```Points from(xCoordinates, yCoordinates)```. You may need to use a combination of extract method and inline to achieve this.
> * Move this method to the ```Points``` class. 
> * Use the "Parallel Change" refactoring
> 
> 
> *Separating creation of points from counting contained points*
> * Wrap the second loop for counting points into a public method ```int countContainedPoints(Points points)``` 
> * Remove ```Points.from(xCoordinates, yCoordinates)``` from this method (either use inline refactoring or extract parameter), 
> such that only the test calls ```Points.from(xCoordinates, yCoordinates)``` and passes the ```Points``` to ```countContainingPoints``` in the test.
> * Simplify any code, make it more readable using the Composed Method refactoring where useful.
