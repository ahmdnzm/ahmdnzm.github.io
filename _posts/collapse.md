# How to add a `collapsible` section in markdown.
## Example
<details>
  <summary>Click me</summary>

  ### Heading
  1. Foo
  2. Bar
     * Baz
     * Qux

  ### Some Code
  ```js
  function logSomething(something) {
    console.log('Something', something);
  }
  ```
</details>


## Code
````md
<details>
  <summary>Click me</summary>
  
  ### Heading
  1. Foo
  2. Bar
     * Baz
     * Qux

  ### Some Code
  ```js
  function logSomething(something) {
    console.log('Something', something);
  }
  ```
</details>
````

## Rules (If you don't do this, your code may not work)
1. Always have an **empty line** after the `</summary>` tag
1. Always have an **empty line** after each `</details>` tag