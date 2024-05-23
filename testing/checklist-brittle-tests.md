
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
- [ ] Only behaviors

#### * **Don't put logic in tests**
- [ ] Lots of logic
- [ ] Some logic
- [ ] Neutral
- [ ] Little logic
- [ ] No logic

#### * **Write clear failure messages**
- [ ] Unclear
- [ ] Somewhat unclear
- [ ] Neutral
- [ ] Fairly clear
- [ ] Clear

### 4. **Tests and Code Sharing: DAMP, Not DRY**
#### * **DAMP vs. DRY** (desirable: Balanced)
- [ ] Entirely DRY (lots of logic in tests, no duplications, concise but incomplete tests)
- [ ] Mostly DRY
- [ ] Balanced (useful helper functions, parameters are passed to accommodate completeness, limited logic in tests nor helper functions)
- [ ] Mostly DAMP
- [ ] Entirely DAMP (lots of duplication, but complete tests)

#### * **Common Patterns for sharing code across tests**
##### * **Shared Values**
- [ ] All declared values use generic and context-free names
- [ ] Mostly generic and context-free value names
- [ ] both equally
- [ ] Mostly specific and configurable values
- [ ] Entirely specific and configurable values used specifically for each test

##### * **Shared Setup**
- [ ] All tests depend on values from the setup method (violates completeness)
- [ ] Most tests depend on values from the setup method
- [ ] Neutral
- [ ] Mostly complete tests (most values are (re-)declared/visible if the test depends on them)
- [ ] Complete: shared setup does not hide any important values

##### * **Shared Helpers and Validation**
- [ ] Obscured
- [ ] Mostly obscured
- [ ] Neutral
- [ ] Mostly concise and complete
- [ ] Concise and complete
