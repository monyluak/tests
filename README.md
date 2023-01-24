# :person_fencing: Tests

> evaluate and verify software

### :nerd_face: Why test?

- Confirm software behaves as **intended** by verifying requirements and **edge cases**.
- Detect **bugs** and ensure changes don't introduce new bugs or **break** existing functionality.
- Facilitate code **refactoring** by providing confidence that **changes** don't introduce new bugs.
- Improve software **quality** by catching issues early and making it more **reliable** and robust.
- Speed up development by allowing developers to quickly **verify** changes don't break existing **functionality**.

### Types of tests
1. **Unit tests**
  - Assess individual functions or classes by supplying input and making sure the output is as expected.
  > Unit tests are like a treasure hunt for bugs!
2. **Integration tests**
  - Check how different parts of a system work together and ensure they are integrated correctly.
  > Integration tests are like a puzzle, where all the pieces fit together perfectly to create a complete and functional system.
3. **UI tests**
  - Analyze the user interface of an application, simulating user interactions and testing the application's behavior.
  > UI tests are like being a customer, where you get to try out the application and make sure it works as expected and is easy to use before it's released to the public.


### :hammer_and_wrench: Tools
**Structure**

```
describe('calculator', () => {
  // describes a module with nested "describe" functions
  describe('add', function() {
    // specify the expected behavior
    it('should add 2 numbers', () => {
       // Use assertion functions to test the expected behavior
       ...  
    })
  })
})
```

**Assertion functions**
```
// jest assertions
expect(2 + 2).toBe(4)
expect({one: 1, two: 2}).toEqual({one: 1, two: 2})
expect(["eggs", "milk"]).toContain("milk")
```

**Techniques**
1. **Spies**
  > objects or functions that record information about how they were called or what they returned

  **Example**
  > Imagine you are testing a function that calls another function. A spy for the called function would be a fake function that records with which parameters it was called. This way, you can test that the function under test is calling the other function with the correct parameters.
  ```
  const spySend = jest.fn();

  it("send email", () => {
    sendEmail("test@example.com", "Hello", "Hi", spySend);
    expect(spySend).toHaveBeenCalledWith("test@example.com", "Hello", "Hi");
  });
  ```
2. **Stubs**
  > objects or functions that return pre-determined values or behaviors in a test

**Example**
> Imagine you are testing a function that makes a network request. A stub for the network request function would be a fake function that always returns a pre-determined response. This way, you can test the function without actually making a network request.
```
const stubAPI = jest.fn();
stubAPI.mockReturnValue({temperature: 25});

it("get temperature", () => {
  expect(getTemperature("New York", stubAPI)).toBe(25);
  expect(stubAPI).toHaveBeenCalledWith("New York");
});
```
3. **Mocks**
  > objects or functions that simulate the behavior of other objects or functions in a test

**Example**
> Imagine you are testing a function that sends an email. A mock for the email sending function would be a fake function that simulates the behavior of sending an email, but doesn't actually send it. This way, you can test the function without actually sending any emails.
```
const mockSend = jest.fn();
mockSend.mockReturnValue(true);

it("send email", () => {
  expect(sendEmail("test@example.com", "Hello", "Hi", mockSend)).toBe(true);
  expect(mockSend).toHaveBeenCalledTimes(1);
});
```


