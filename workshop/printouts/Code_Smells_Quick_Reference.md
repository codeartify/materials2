
# Quick Reference to Code Smells

1. **Magic Number/String**: Unclear what it means. Replace with variable, constant, or enum.
2. **Redundant Comment**: Only repeats what is obvious from the code. Remove it.
3. **Complicated Boolean Expression**: Introduce brackets, explaining variables or methods, apply DeMorgan’s laws, remove double negations.
4. **Deeply-Nested Control Flow**: Missing abstractions, procedural code. Introduce guards, combine nested ifs, create composed methods (and move them to separate classes if possible for testing) to ensure every method has only a single level of abstraction.
5. **Long Method**: Usually contains small one-line comments indicating what the next part of the method is going to do. Wrap and move methods to meaningful classes, replace generic with specific names.
6. **Side Effect**: Method sets an unexpected state. Declare it in the method’s name and eventually split the method and make callers invoke them explicitly (Duplicate and Reduce refactoring may help).
7. **Temporary Field**: The constructor finishes without initializing all fields. The other fields are initialized by another method later (as a side effect) and are typically used as a side channel to transfer data between two methods. Remove the side effect and make the call explicit or extend the return value.
8. **Primitive Obsession**: Usage of primitives (int, double, Boolean, arrays, collections, etc.) instead of higher-level abstractions. Create abstractions to wrap primitives and functionality on them.
9. **Data Clump**: Primitives occur together in groups but are not wrapped in a higher-level abstraction. Wrap them in an own class together with behavior on them.
10. **Data Class**: Classes with instance variables and getters/setters, but no actual functionality. Look for feature envy on that class, wrap and extract methods for them and move it to that class.
11. **Feature Envy**: A method uses another class’s data extensively for some calculations (getters/setters). Wrap and extract method and move it to the data(-providing) class (mind SoC).
12. **Inappropriate Intimacy**: Public access to members that should be private. Encapsulate field and consider redistributing responsibilities between classes.
13. **Flag Parameters**: Any Boolean, enum, null check, etc., that makes a method/class behave differently depending on its value (can simulate polymorphic behavior). Introduce meaningful enums, wrap constructors in specific factory methods, split methods, introduce polymorphism.
14. **Long Parameter List**: Remove primitive obsession/data class smells, remove flag parameters, consider splitting method/class (assure SRP).
15. **Deep Inheritance Hierarchy**: Hierarchy makes it hard to understand, test, and extend subclasses. Solution depends on other smells (see below).
16. **Unnecessary Inheritance**: There are no overridden methods in the subclass (code reuse). Replace inheritance with delegation.
17. **Refused Bequest**: The overriding method never calls the overridden method (`x() { super.x(); }`). Add super call or redesign code (replace inheritance with delegation).
18. **Simulated Polymorphic Behavior**: Switch-case or if-else to decide the methods’ behaviors (simulates polymorphism). Usually accompanied with flag parameter smell. Replace with polymorphism.
19. **Lazy Class**: Class that does not do enough to justify its existence (e.g., static helpers, interfaces with only constants). Inline.
20. **Speculative Generality**: Anything speculated to be required in the future. E.g., if there is an interface with only a single implementation, the interface can usually be inlined. Mind Separation of Concern!
21. **Alternative Class with Different Interface**: Replace duplicated code with one version and inline.
22. **Inconsistent Solution**: Decide on one solution in the team/project and stick with it.
23. **Dead Code**: Use tools to detect it, mind (framework) reflection calls, and remove it.
24. **Large Class**: Try to use composition, summarize homogenous callers, define interfaces, and split class accordingly.
