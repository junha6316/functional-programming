Functional Programming
Eliminating State as much as possible, Tightly Control State

- 2. Primitive Data Types

  - undefined
  - Number
  - String
  - Boolean
  - Objects Literal
  - Arrays

- 3. Immutable Data

  - String is immutable
  - constant is protected?
    - protected from reassigning data
    - almost never for mutable
  - Update Object in an immutable way

    - using spread operator, deconstruct

    ```javascript
    const meal = { id: 1, description: "Test" };
    const updatedMeal = { ...meal, addProperty: "abs" };
    ```

    - using map

    ```javascript
    const arr = [1, 2, 3];
    function dobleNumber(number) {
      return number * 2;
    }
    const doubledArr = arr.map(double);
    ```

    - using filter for removing

    ```javascript
    const arr = [1, 2, 3];
    const filteredArr = arr.filter((number) => number >= 2);
    ```

- 4. Types of Functions

  - High Order Function(HOF)
    1.  function that receive one more function arguments
    2.  function that return function
  - Closure

  - Currying and Partial Application

    - Currying: Creating Function, No Data

      - using HOF feature, decomposite the arguments

        ```javascript
        const greet = (greet, name) => `${greeting} ${name}`;
        console.log(greet("Good Morning", "junha"));
        // currying
        const curryGreet = (greet) => (name) => `${greeting} ${name}`;
        console.log(greet("Good Morning")("junha"));
        ```

        - general parameter first, specialized paramter next
        - Using Rambda

        ```javascript
        const greet = R.curry((greet, name) => `${greeting} ${name}`);
        greet("Good Morning")("Junha"); // it works
        ```

    - Partial Application: Using Function With Data

      - partial Application without currying

      ```javascript
      const add = (x, y) => x + y;
      const add3 = partial(add, [3]);
      ```

    - Pure/Impure(Procedure) Function
    - Pure Function : Creates & Returns Value Based On Input No side Effects
      - side effects : Code causes change outside itself
      - Have Inpute Parameters
      - No StateFul Value
      - Reusable, Composable, Easy To Test, Easy To Cache
    - Impure Function: Procedure

- Function Composition

  ```javascript
  const sentence = "Hi My Name is Junha";
  const wordList = R.split(" ", sentence);
  const wordCount = R.length(R.split(" ", sentence));

  const countWords1 = R.compose(R.length, R.split);
  const countWords2 = R.compose(R.lenght, R.split(" "));
  const countWords3 = R.compose(R.split(" "), R.length); // =>
  ```
