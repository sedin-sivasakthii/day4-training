# ES6+ Programming Exercises

## Exercise 1: Dynamic Component Generator

### Problem Statement
Create a function that generates a semantic HTML product card. This exercise tests your ability to handle conditional rendering and array mapping directly within template literals.

### Starter Code
```javascript
const product = {
  title: "Mechanical Keyboard",
  price: 150,
  isSale: true,
  features: ["Mechanical Switches", "RGB Backlit", "Programmable Keys"]
};

function renderProductCard(product) {
  // Your code here
}

console.log(renderProductCard(product));
```

### Constraints

-   Use a single template literal for the entire return value.
    
-   Do not use `if/else` statements inside the function body; use ternary operators for conditional logic within the template.
    
-   Use `Intl.NumberFormat` to format the price as USD currency.
    
-   If the `features` array is empty, the UI must display "No features listed."
    
-   Use `.map()` and `.join('')` to render the list items.
    

### Question

When using `.map()` inside a template literal to render an array of HTML elements, why is it necessary to use `.join('')` at the end of the expression? What happens to the UI if you omit it?

----------

## Exercise 2: Immutable State Merger

### Problem Statement

Write a utility function that merges multiple configuration objects into a final application state. This exercise focuses on non-destructive data handling and the use of rest/spread syntax.

### Starter Code

```javascript
const defaultConfig = {
  theme: "light",
  notifications: true,
  version: "1.0.0",
  retries: 3
};

const userOverrides = {
  theme: "dark",
  retries: 5
};

function processSettings(defaultConfig, userOverrides, ...plugins) {
  // Your code here
}

const finalOutput = processSettings(defaultConfig, userOverrides, { cache: true }, { version: "1.1.0" });
console.log(finalOutput);

```

### Constraints

-   Use the **spread operator** to merge all objects.
    
-   Order of priority (last value wins): `plugins` > `userOverrides` > `defaultConfig`.
    
-   Use the **rest operator** to extract the `version` property from the merged result.
    
-   The function must return an object with two keys: `version` (the extracted string) and `finalConfig` (an object containing all remaining properties).
    
-   **Immutability Check:** The `defaultConfig` object must remain identical to its original state after the function runs.
