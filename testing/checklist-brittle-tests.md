
## Checklist Brittle Tests
* **bold** = desirable
### 1. **Test via the public API**
- [ ] Only public API
- [ ] **Mostly public API, some important public methods not part of the public API with lots of logic**
- [ ] Equally split
- [ ] Mostly each method (public, but even some package-private or protected)
- [ ] Each method (public, package-private or protected)

### 2. **Test state, not interactions**
- [ ] Only interactions
- [ ] **Mostly interactions, some useful state**
- [ ] Equally split
- [ ] Mostly state, some useful interactions
- [ ] Only state

### 3. **Write clearer tests**
#### * **Make tests complete and concise**
- **Conciseness:**
    - [ ] Not concise
    - [ ] Somewhat concise
    - [ ] Neutral
    - [ ] Fairly concise
    - [ ] **Concise**

- **Completeness:**
    - [ ] Not complete
    - [ ] Somewhat complete
    - [ ] Neutral
    - [ ] Fairly complete
    - [ ] **Complete**

#### * **Test behaviors, not methods**
- [ ] Only methods
- [ ] Mostly methods
- [ ] Equally split
- [ ] Mostly behaviors
- [ ] **Only behaviors**

#### * **Don't put logic in tests**
- [ ] Lots of logic
- [ ] Some logic
- [ ] Neutral
- [ ] Little logic
- [ ] **No logic**

#### * **Write clear failure messages**
- [ ] Unclear (misses all: desired outcome, actual outcome, relevant parameters)
- [ ] Somewhat unclear
- [ ] Neutral
- [ ] Fairly clear
- [ ] **Clear (clearly distinguishes desired outcome from actual outcome and expresses any relevant parameters)**

### 4. **Tests and Code Sharing: DAMP, Not DRY**
#### * **DAMP and DRY**
- [ ] TOO DRY (lots of logic in tests, almost no duplications, often concise (only relevant information) but incomplete tests (missing information))
- [ ] Neither DRY nor DAMP (messy, various solutions to the same problem)
- [ ] **Mostly DAMP (concise helper functions, parameters are passed for completeness, only absolutely necessary logic in tests/helper functions)**

#### * **Common Patterns for sharing code across tests**
##### * **Shared Values**
- [ ] All test values are shared globally and have generic and context-free names
- [ ] Mostly global, shared test values with generic and context-free names
- [ ] equally global, context-free and local, context-specific test values
- [ ] Mostly context-specific and configurable values, some global context-free, generic values
- [ ] **Entirely specific and configurable values used specifically for each test**

##### * **Shared Setup**
- [ ] All tests depend on values from the setup method (violates completeness)
- [ ] Most tests depend on values from the setup method
- [ ] Neutral
- [ ] Mostly complete tests (most values are (re-)declared/visible if the test depends on them)
- [ ] **Complete: shared setup does not hide any important values**

##### * **Shared Helpers and Validation**
- [ ] Validate method called at the end of every test method, which performs a fixed set of checks against the SUT
- [ ] Mostly multiple assertions in a validation method
- [ ] equally single and multiple assertions in a validation method
- [ ] Mostly focused validation methods asserting a single conceptual fact about their inputs
- [ ] **Focused validation methods assert a single conceptual fact about their inputs**
