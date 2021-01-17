# naming-things

> There are only two hard things in Computer Science: cache invalidation and naming things.

-- Phil Karlton

Naming things is one of the 3 hardest problems in computer science. Here's an attempt at outlining a few guiding principles for determining how to name something.

1. **Concise and Accurate**
    1. A name needs to be concise.
        1. If it's too long it sacrifices the readability. It's like reading an essay for something that could be said in a few sentences yet carry the same meaning.
    2. Context of a name helps clarify its meaning
    3. A name must be accurate
        1. If the context in which a name is used is not enough to infer what the name refers to then the name should be lengthened to clarify its meaning.

        ```jsx
        // Bad
        const arrayOfNumbers = [1, 2, 3];
        // Bad
        const a = [], b = 3
        ```

    In this example, it is obvious that this array is an array of numbers. What isn't clear is what the array of numbers is used for

    ```jsx
    const ids = [1, 2, 3];
    ```

    This is slightly better, but it's still not clear what it means. Why? That is because it doesn't have any context. Let's add some:

    ```jsx
    function countUserIds() {
      const ids = [1, 2, 3];
    }
    ```

    What happens if this list can't be defined inside of a function? Then we rename the variable to clarify the context it is used in

    ```jsx
    const userIds = [1, 2, 3];

    function countUserIds() {
      // use `userIds` somewhere in this function
    }
    ```

    Note that modules can also provide context that can reduce variable names.

    ```jsx
    import { msToSec } from 'my-time-lib';
    ```

    This is also the case for classes.

    ```jsx
    class Time {
      toMs() {}
      toSec() {}
    }
    ```

2. **Verbs should read well**
    1. Variable names that are verbs should be named in such a way that they don't sound awkward.
    2. Example

    ```jsx
    // Bad
    timeConvert();

    // Good
    convertTime();
    ```

3. **Function and/or method names are decoupled from their implementation**
    1. When a user is invoking a function or a method, they should not need to know how it works in order to use it. This allows the internal implementation to change while still having the function or method's name remain accurate.
    2. Example

        ```jsx
        // Bad
        function padWithZeroIfLessThanTen(ms) {}

        // Better
        function padWithZero(ms) {}

        // Bad
        function timeConvert(minutes) {
          // Bad
          const absMinFloored = Math.floor(Math.abs(minutes));
        }

        // Good
        function timeConvert(minutes) {
          // Good
          const min = Math.floor(Math.abs(minutes));
          // ...
        }
        ```

4. **Use shorthands when possible**

```jsx
// Bad
function convertTimeToMinutesFromSeconds(min) {}

// Good
function minToSec(min) {}
```

**5. Consistency**

```jsx
// Bad
function msToSeconds() {}
function secToMili() {}

// Good
function msToSec() {}
function secToMs() {}
```

**6. Respect pre-existing naming conventions.**

Each programming language usually has its own naming conventions for things. Usually there are two kinds of conventions each language has:

1. casing conventions
2. API naming conventions
