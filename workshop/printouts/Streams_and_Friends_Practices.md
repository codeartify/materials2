
# Streams and Friends: Field-Tested Practices

## Best Practices (Do's) | Common Pitfalls (Don'ts)
--- | ---
✓ Use Streams and Lambdas to improve readability. | × Don’t use Streams and Lambdas just because it’s a newer concept!
✓ Keep Lambdas short (one or few lines) and self-explanatory (because there are no names nor documentation). | × Don’t use `forEach()` instead the older for/for-each loop statements just to use Streams (because it tends to be harder to debug than simple loops).
✓ Use self-explanatory names for Lambda parameters (“identifier -> …“ instead of “i -> …”). | × Try to avoid `forEach()` instead of `flatMap()` to perform an action on multidimensional collections.
✓ Use method references where applicable. | × Don’t specify parameter types.
✓ Write only one Stream expression per line (one new line for every expression). | × Avoid parentheses around single parameters.
✓ Chain multiple Stream expressions with short Lambdas instead of one large Lambda in a single Stream expression (think “pipes and filters”). | × Avoid return statements and braces for one-line lambda bodies.
✓ Wrap complicated Stream expressions and/or Lambdas in self-explanatory methods. Move methods to appropriate classes if applicable. | × Don’t store Lambdas in variables. Prefer self-explanatory methods and method references.
✓ Annotate interfaces with `@FunctionalInterface` to signal its usage for Lambdas and to prevent other developers from adding additional method declarations to the interface. | × Don’t declare variables used within a Lambda outside the Lambda scope as final (as they are effectively final).
✓ Use Optionals for return values. | × Avoid state changes of mutable objects initialized outside the Lambda scope (e.g., adding an object to a collection inside the Lambda).
✓ Use `orElse()`/`orElseGet()`/`orElseThrow()` instead of the combination of `isPresent()` and `get()`. | × Try to avoid default methods in functional interfaces (to avoid name collisions with other functional interfaces).
| | × Try to avoid Optionals for fields or method parameters.
