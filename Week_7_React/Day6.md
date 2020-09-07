# Unit & Integration Testing

### Diff Types of Testing

- Static - fast, cheap
- Manual - slow, expensive
- Unit - fast, cheap
- Integration - slow, medium expensive / take longer to run (press button by code)
- End to End (E2E) - slowest, expensive (still cheaper than manual) / Cyress, test user story

### Tools for testing React

- Jest (Mocha equivalent) test-runner / right out of box from create-react-app
- Testing library (testing-library.com) for DOM testing / matchers check if result match the expect
  - React Testing Library
  - Jest-dome

#### When given an app to work on

- Check Chrome Dev , Components tab
  - see the tree (Parent - child relation)
  - check state and props(what is passed on or not, what data used)
- Check Test suites - Jest
  - test file should always inside test folder **tests**/ so Jest can find
  - each test file is a test suit
  - npm test -- (tell npm the flag is not for npm) --verbose
  - npm test -- --coverage --watchAll=false(turn watcher off so coverage can work)
    - Statements (Stmts) : statement you write, kinda like line
    - Branch (Branch) : evaluation login in code if..else / switch
    - Functions
    - Lines
    * Go to cover directory, inside has a index.html, run in browser to see details
    * Click file name on browser to see which line got test, how many times, which line didn't test

### Writing Unit Test

- Use human readable statement in description
- Take advantage of named variable to make test easy to follow

### Writing Integrate Test

- User doesn't not have access to state -> test things that visble/ in DOM
- Check if a class has/has not been applied
- Check if an element can/cannot be found
- Check if an element is/is not visible
- { render } from `@testing-library/react` -> const { debug } = render(<Component/>)
- { prettyDOM } from `@testing-library/react` -> console.log(prettyDOM(container))
- { getByTestid } = render(<Component/>) -> data-testid = "test id" -> an attribute you add to an element so jest can search for it by

  > 'data-' will hide from DOM display, but can search by query -> \$.data('text id')

- If we get fireEvent/ getByTestId from render(<Component/>), they are bound, thus no need to specific container
- If we get fireEvent/ getByTestId from @test-library, they are generic, thus need to specific container -> const container = render(<Component/>) -> getByTestId(container, 'text id')

### Mock Axios Request

- Isolate the test by mocking
- Axios return is non controlled and may affect test result

* Import function to be mock
* Tell jest to mock the function jest.mock('function') <- string function name, not actual function
* Fake data to be return by Jest
* Use findBy....(e.g. findByText) for async test -> will wait for axios calls etc
* Use getBy...(e.g. getByTestId) for sync test -> check if already in DOM, will throw err if not found
* Use queryBy... (e.g. queryBy???) for sync test -> check if already in DOM, will return null if not found, no err thrown

#### Async/Await

- make your async code behave like sync
- inside an Async, where is an await, that hold the code on that line, until the async return (promise resolve/ reject)
