# Brittle tests
* Tests that fail due to unrelated changes to production code that does not introduce any _real_ bugs.
* Tests need to be tweaked when changes are introduced: unproductive, especially in larger codebases.
* Tests should not have to change after writing them, unless the requirements change.

## 4 Types of Changes
1. **Pure refactorings**: Changes that do not affect the behavior of the code.
2. **New features**: Existing behaviors should be unaffected
3. **Bug fixes**: Existing behaviors should be unaffected
4. **Behavior changes**: only here the test should need to change. Change the contract with the user that called the code.

![4_types_of_changes.png](images/4_types_of_changes.png)

## How to Make Brittle Tests More Robust
1. [!**Unit Test via the Public API**](https://testing.googleblog.com/2015/01/testing-on-toilet-prefer-testing-public.html): 
    * Acceptance tests. 
    * Invoke the system like users would invoke it: call against public API, not implementation details.
    * If such a test fails, it implies that also an existing user of the system would be affected.
    * Internal refactorings can be done without affecting the tests.
    * "public API" can be small as a function or as broad as several related packages / modules. 
    * It's not "public" in the Java visibility sense. 
    * Public means API exposed by that unit to a third parties outside the team that owns the code
   

2. [**Test STATE, not interactions**](https://testing.googleblog.com/2013/03/testing-on-toilet-testing-state-vs.html):
    * **State** Testing: observe the system itself to see what it looks like after invoking it (e.g. after inserting into a DB, call the public API to see if the data is there).
    * [**Interaction**](https://martinfowler.com/articles/mocksArentStubs.html#ClassicalAndMockistTesting) Testing: check that a system took an expected sequence of actions on its collaborators in response to invoking it.
        * Only test interactions when
          1. Code under test call a method where the **difference in the number or order of calls** would cause undesired behaviors like sideeffects, latency, or multithreading errors
          2. Testing UIs where rendering details of the UI are abstracted away from the UI logic (e.g. only render(html)). Call is important, but not the actual state (html).
    * Avoid overmocking. Prefer real objects over mocks, as long as they are fast and deterministic.
    ![test_state_not_interactions.png](images/test_state_not_interactions.png)
3. **Write clearer tests**:
    * Test failures happen for 2 reasons: 
        1. The system under test has a problem or is incomplete (bug).
        2. The test itself is flawed. SUT ok, test was specified incorrectly.
    * A test needs to be clear enough to identify the reason for the test failure quickly!
    1. [**Make tests complete and concise**](https://testing.googleblog.com/2014/03/testing-on-toilet-what-makes-good-test.html):
   
       <img src="images/concise_complete.png" width="300" />
   
       * **complete**: body contains all the info a reader needs in order to understand how it arrives at its result.
       * **concise**: contains no other distracting or irrelevant information
       
       <img src="images/complete_concise_ex.png">
    2. [**Test Behaviors, not Methods**](https://testing.googleblog.com/2014/04/testing-on-toilet-test-behaviors-not.html):

       ![testing_methods.png](images/testing_methods.png) 
       
       ![behavior_driven_testing.png](images/behavior_driven_testing.png)
      * [**ZOMBIES**](https://blog.wingman-sw.com/tdd-guided-by-zombies): Zero, One, Many, Boundaries, Interfaces, Exceptions, Simple Scenarios
        
        <img src="images/zombies.png" width="300">
        
        1. [**Structure Tests according to Behaviors**](https://dannorth.net/introducing-bdd/):
            * **Given-When-Then** structure
            * From a user/business domain perspective 
            * Use whitespaces for given/when/then instead of writing it out
            
           ![given_when_then.png](images/given_when_then.png)
        
            * **Multistep** processes sometimes can have **multiple when and then**. 
            * Split them with **AND**. 
            * **BUT**: each test should only cover a **single behavior** still.
            * Most unit tests require only **one** given-when-then.
           
            * ![multiprocess_gwt.png](images/multiprocess_gwt.png)
        2. **Name tests after the behavior being tested**
            * When in doubt, start a new test case with "should", e.g. ```BankAccountShould.doSomething()```.
            * If you need to use "AND", e.g. ```BankAccountShould.doSomethingAndSomethingElse()```, you're most likely testing more than 1 behavior.
            
            * ![naming_patterns.png](images/naming_patterns.png)

   3. **Don't put logic in tests**:
        * Tests should not need their own tests.
      
        ![no_logic_in_tests.png](images/no_logic_in_tests.png)
   4. **Write clear failure messages**:
   
       ![clear_failure_message.png](images/clear_failure_message.png)
