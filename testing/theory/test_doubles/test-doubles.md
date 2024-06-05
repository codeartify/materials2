# Test Doubles
## What are Test Doubles?
* An object or function that can stand in for a real implementation in a test.
* Often referred to as mocking (though not all test doubles are mocks).
* Example: in-memory version of a database.
* Allow to write tests that execute quickly and are not flaky compared to the real implementation.

## What are Test Double Trade-Offs?
* **Testability**: a codebase needs to be designed to be _testable_ (e.g. dependency injection).
* **Applicability**: improper use of test doubles (e.g. through mocking frameworks) can lead to brittle and complex tests.
* **Fidelity**: test doubles should mimic the real implementation as closely as possible. However, simpler implementations mean they cannot give 100% fidelity. Unit tests that use test doubles need to be supplemented by larger-scope tests to exercise the real implementation.

# When is Code Testable?
* using a _seam_: allows the use of test doubles, e.g. Dependency injection

## Techniques for Test Doubles
### Fake
* a simplified version of a real implementation that is easier to set up and use. e.g. in-memory database.
* a system under test should not be able to tell whether it's interacting with a fake or the real implementation.
```
// This fake implements the FileSystem interface. This interface is also
// used by the real implementation.
public class FakeFileSystem implements FileSystem {
  // Stores a map of file name to file contents. The files are stored in
  // memory instead of on disk since tests shouldn’t need to do disk I/O.
  private Map<String, String> files = new HashMap<>();
  @Override
  public void writeFile(String fileName, String contents) {
    // Add the file name and contents to the map.
    files.add(fileName, contents);
  }
  @Override
  public String readFile(String fileName) {
    String contents = files.get(fileName);
    // The real implementation will throw this exception if the
    // file isn’t found, so the fake must throw it too.
    if (contents == null) { throw new FileNotFoundException(fileName); }
    return contents;
  }
}
```
### Stub
* a test double that provides canned responses to calls. e.g. a stub that always returns the same value.
```
// Pass in a test double that was created by a mocking framework.
AccessManager accessManager = new AccessManager(mockAuthorizationService):

// The user ID shouldn’t have access if null is returned.
when(mockAuthorizationService.lookupUser(USER_ID)).thenReturn(null);
assertThat(accessManager.userHasAccess(USER_ID)).isFalse();

// The user ID should have access if a non-null value is returned.
when(mockAuthorizationService.lookupUser(USER_ID)).thenReturn(USER);
assertThat(accessManager.userHasAccess(USER_ID)).isTrue();
```
* **Interaction Testing**: validate how a function is called without actually calling the implementation of the function
```
// Pass in a test double that was created by a mocking framework.
AccessManager accessManager = new AccessManager(mockAuthorizationService);
accessManager.userHasAccess(USER_ID);

// The test will fail if accessManager.userHasAccess(USER_ID) didn’t call
// mockAuthorizationService.lookupUser(USER_ID).
verify(mockAuthorizationService).lookupUser(USER_ID);
```

## Real Implementations
* Prefer realism over isolation
* A good test should use as many real objects as possible
* Advantage:  test will fail if there is a bug in a real implementation

### When to use a real implementation?
* when it is fast, deterministic, and has simple dependencies
* _fast_: the more test cases, the higher the impact may be on test execution times when using a real implementation
* _deterministic_: the test should always return the same result for the same input
  * nondeterminism leads to flakiness - if this happens often, use a test double
  * nondeterminism can be caused by e.g. multithreading, system clock, network calls, etc.
  * nondeterminism happens when code is not hermetic: the dependencies on external services are outside the control of the test
