
# TypeScript Interview Questions and Answers



### Q1: List the built-in types in Typescript ⭐

**Answer:**
TypeScript includes several built-in types that provide a foundation for defining data structures and variables. Here's a list of some of the core built-in types in TypeScript:

1. **Number**: Represents both integer and floating-point numbers.

   ```typescript
   let num: number = 42;
   ```

2. **String**: Represents textual data.

   ```typescript
   let str: string = "Hello, TypeScript!";
   ```

3. **Boolean**: Represents true or false values.

   ```typescript
   let isTrue: boolean = true;
   ```

4. **Array**: Represents a list of values of the same type.

   ```typescript
   let numbers: number[] = [1, 2, 3, 4, 5];
   ```

5. **Tuple**: Represents an array with a fixed number of elements, where each element can have a different type.

   ```typescript
   let tuple: [number, string] = [42, "Hello"];
   ```

6. **Enum**: Represents a set of named numeric values.

   ```typescript
   enum Color {
       Red,
       Green,
       Blue
   }
   let color: Color = Color.Red;
   ```

7. **Any**: Represents a dynamic or untyped value. Use sparingly, as it bypasses TypeScript's type checking.

   ```typescript
   let dynamicValue: any = 42;
   ```

8. **Void**: Represents the absence of a value. Typically used as the return type of functions that don't return anything.

   ```typescript
   function logMessage(): void {
       console.log("This function doesn't return anything.");
   }
   ```

9. **Null and Undefined**: Represent the absence of a value or uninitialized variables.

   ```typescript
   let nullValue: null = null;
   let undefinedValue: undefined = undefined;
   ```

10. **Never**: Represents a value that never occurs, often used for functions that throw errors or enter infinite loops.

    ```typescript
    function throwError(message: string): never {
        throw new Error(message);
    }
    ```

11. **Object**: Represents any non-primitive type (i.e., not number, string, boolean, null, or undefined).

    ```typescript
    let obj: object = { key: "value" };
    ```

12. **Symbol**: Represents unique and immutable values used as object property keys.

    ```typescript
    const uniqueKey = Symbol("unique");
    let obj = {
        [uniqueKey]: "This is a unique key",
    };
    ```

These are some of the core built-in types in TypeScript. TypeScript also allows you to define custom types using interfaces, classes, and unions to create complex data structures tailored to your needs.


### Q2: What are Modules in Typescript? ⭐

**Answer:**

Modules in Typescript helps in organizing the code. There are 2 types of Modules — Internal and External

* **Internal Modules** are now replaceable by using Typescript’s namespace.

* **External Modules** used to specify and load dependencies between multiple external js files. If there is only one js file used, then external modules are not relevant.

🔗 **Source:** [FullStack.Cafe](https://www.fullstack.cafe)


### Q3:  What is Typescript and why one should use it? ⭐

TypeScript is an open-source programming language developed by Microsoft. It is a statically typed superset of JavaScript, which means that it builds upon the syntax and features of JavaScript while adding optional static type checking. TypeScript code is transpiled (converted) into JavaScript, making it compatible with all JavaScript environments, including web browsers and Node.js.

Here are some key reasons why one should consider using TypeScript:

1. **Static Type Checking**: TypeScript introduces static type checking, allowing you to specify the types of variables, function parameters, and return values. This helps catch type-related errors at compile time rather than at runtime. Static typing can lead to more robust and maintainable code.

2. **Improved Code Quality**: With static typing, you can catch common programming errors, such as type mismatches and undefined values, early in the development process. This leads to fewer runtime errors and improved code quality.

3. **Enhanced Tooling**: TypeScript provides a rich development experience with features like code autocompletion, intelligent code navigation, and code refactoring support in modern code editors and IDEs. The TypeScript compiler can also provide helpful error messages.

4. **Readability and Maintainability**: By adding type annotations to your code, you make it more self-documenting. This can improve the readability of your code, making it easier for developers to understand and maintain.

5. **Large-Scale Projects**: TypeScript is particularly beneficial for large-scale projects with multiple developers. It helps prevent common errors and promotes code consistency and collaboration.

6. **Compatibility with JavaScript**: TypeScript is a superset of JavaScript, which means that you can gradually adopt TypeScript in an existing JavaScript codebase without rewriting everything. You can add type annotations incrementally to your code.

7. **Community and Ecosystem**: TypeScript has gained significant popularity in the web development community. It has a vibrant ecosystem with a growing number of libraries, frameworks (like Angular), and tools designed specifically for TypeScript.

8. **Strongly Typed Interfaces**: TypeScript supports the creation of interfaces, which allow you to define contracts for objects and classes. This is useful for ensuring that objects adhere to a specific structure.

9. **ES6+ Features**: TypeScript supports modern JavaScript features from ECMAScript 6 (ES6) and later versions, allowing you to use the latest language features even when targeting older JavaScript environments.

10. **Tooling for Migration**: TypeScript provides tools and resources to help migrate existing JavaScript codebases to TypeScript, making it easier to transition to a statically typed environment.

11. **Cross-Platform Development**: TypeScript is not limited to web development. It can be used for building both frontend and backend applications, mobile apps (with frameworks like React Native), and more.

In summary, TypeScript is a powerful tool for improving the quality, maintainability, and developer experience of your JavaScript projects. It's particularly valuable for larger projects and teams, but developers of all levels can benefit from using TypeScript to write safer and more reliable code.


### Q4: Explain generics in TypeScript ⭐

**Answer:**

Generics in TypeScript provide a way to write code that can work with different data types while maintaining type safety. They allow you to create reusable components, functions, or classes that can adapt to the specific data types you provide when you use them. Generics are often used to build data structures and higher-order functions that work with a variety of data.

Here's a basic introduction to generics in TypeScript:

1. **Creating Generic Functions:**

   You can define a generic function by using angle brackets `<T>` to declare a type variable `T`. This type variable `T` represents a placeholder for a specific data type that you'll provide when using the function.

   ```typescript
   function identity<T>(arg: T): T {
       return arg;
   }
   ```

   In this example, `T` is a generic type parameter. When you call `identity`, TypeScript infers the type of `T` based on the argument you provide:

   ```typescript
   let result = identity("Hello, TypeScript!"); // result is of type string
   let numberResult = identity(42); // numberResult is of type number
   ```

2. **Generic Interfaces:**

   You can also use generics with interfaces. This is useful when defining interfaces for data structures or classes that work with various data types.

   ```typescript
   interface Box<T> {
       value: T;
   }

   let box1: Box<number> = { value: 42 };
   let box2: Box<string> = { value: "Hello" };
   ```

   Here, `Box<T>` is a generic interface, and you specify the data type for `T` when creating instances of `Box`.

3. **Generic Classes:**

   Similar to interfaces, you can create generic classes in TypeScript:

   ```typescript
   class Pair<T, U> {
       constructor(public first: T, public second: U) {}
   }

   let pair1 = new Pair(42, "Hello");
   let pair2 = new Pair(true, 3.14);
   ```

   In this example, `Pair<T, U>` is a generic class that can hold two values of potentially different data types.

4. **Generic Constraints:**

   You can add constraints to generic types to restrict the types that can be used with generics. For example, you can ensure that a generic type must have certain properties or methods.

   ```typescript
   interface Lengthwise {
       length: number;
   }

   function logLength<T extends Lengthwise>(arg: T): void {
       console.log(arg.length);
   }
   ```

   The `extends` keyword is used here to specify that `T` must extend the `Lengthwise` interface, meaning it must have a `length` property.

Generics in TypeScript provide flexibility and type safety, allowing you to write reusable code that works with various data types while catching type errors at compile time. They are commonly used in libraries, data structures, and functions where you want to create code that is adaptable to different use cases without sacrificing type checking.

### Q7: What are the benefits of TypeScript? ⭐

**Answer:**

TypeScript offers several benefits that make it a valuable choice for many developers and projects. Here are some of the key advantages of using TypeScript:

1. **Static Typing**: TypeScript introduces static typing, allowing you to explicitly specify data types for variables, function parameters, and return values. This leads to early error detection and improved code quality by catching type-related errors at compile time rather than runtime.

2. **Enhanced Code Quality**: The use of types makes your code more self-documenting and easier to understand. Type annotations serve as documentation, making it clear what kind of data is expected, leading to improved code maintainability.

3. **Tooling Support**: TypeScript is supported by a wide range of code editors and IDEs (Integrated Development Environments). These tools provide features like code autocompletion, intelligent code navigation, and code refactoring support, which enhance developer productivity.

4. **Early Error Detection**: TypeScript can catch common programming errors, such as type mismatches and null/undefined errors, at compile time. This means you can identify and fix issues before they become runtime problems, resulting in more reliable software.

5. **Large-Scale Project Support**: TypeScript is particularly well-suited for large-scale projects with multiple developers. Strong typing, type inference, and the ability to define interfaces help maintain code quality and consistency as the codebase grows.

6. **ECMAScript Compatibility**: TypeScript supports modern JavaScript features from ECMAScript 6 (ES6) and later versions. You can write code using the latest JavaScript syntax and features, and TypeScript will transpile it to compatible JavaScript for older environments.

7. **Gradual Adoption**: You can introduce TypeScript incrementally into an existing JavaScript project without rewriting everything. TypeScript allows you to gradually add type annotations to your codebase as needed.

8. **Community and Ecosystem**: TypeScript has gained significant popularity in the web development community. It has a vibrant ecosystem with libraries, frameworks (e.g., Angular, React, Vue.js), and tools designed specifically for TypeScript.

9. **Cross-Platform Development**: TypeScript can be used for both frontend and backend development. You can use TypeScript to build web applications, server-side applications with Node.js, and even mobile applications using frameworks like React Native.

10. **Strongly Typed Interfaces**: TypeScript supports the creation of interfaces, allowing you to define contracts for objects and classes. This is useful for ensuring that objects adhere to a specific structure, improving code maintainability.

11. **Compatibility with Existing JavaScript Code**: TypeScript is a superset of JavaScript, which means that all JavaScript code is also valid TypeScript code. This makes it easy to integrate TypeScript into existing projects or libraries.

12. **TypeScript Definition Files**: TypeScript includes a feature called declaration files (`.d.ts` files) that can describe the shape of JavaScript libraries and APIs. These declaration files provide type information for external libraries, enabling better tooling support and type checking when using those libraries in TypeScript projects.

In summary, TypeScript offers a combination of static typing, tooling support, code quality improvements, and scalability benefits that make it a valuable choice for building modern web applications and large-scale software projects. Its flexibility also allows developers to gradually adopt it in existing codebases or projects of varying sizes and complexities.


### Q8: Do we need to compile TypeScript files and why? ⭐

**Answer:**

Yes we do. Typescript is just a language Extension browsers can't interpret it. Converting from TypeScript to JavaScript is called compiling. Compiling doesn't mean binary code is created in this case. For this kind of translation, also the term transpilation is used instead of compilation.

🔗 **Source:** [stackoverflow.com](https://stackoverflow.com/questions/45125284/why-is-angular-compiled)


### Q9: How to call base class constructor from child class in TypeScript? ⭐

**Answer:**

We can call base class constructor using `super()`.

🔗 **Source:** [http://www.talkingdotnet.com](http://www.talkingdotnet.com/typescript-interview-questions/)


### Q10: What are the difference beetween Typescript and JavaScript? ⭐⭐

**Answer:**

* It is an object oriented programming language (not pure).
* Here it is static typing (We can declare a variable in multiple ways). ex: var num : number.
* It has interfaces.
* It has optional parameter feature.
* It has Rest Parameter feature.
* Supports generics.
* Supports Modules
* Number, string etc. are the interfaces.


🔗 **Source:** [FullStack.Cafe](https://www.fullstack.cafe)


### Q11: What is Interface in TypeScript? ⭐⭐

**Answer:**
In TypeScript, an interface is a way to define a contract or a blueprint for the shape and structure of objects. It specifies the properties and methods that an object must have to be considered an instance of that interface. Interfaces are used to enforce a certain structure and type-checking for objects in your code.

Here's how you define and use interfaces in TypeScript:

```typescript
interface Person {
    firstName: string;
    lastName: string;
    age: number;
}

const person: Person = {
    firstName: "John",
    lastName: "Doe",
    age: 30,
};
```

In this example, we define an interface called `Person` that specifies the required properties: `firstName`, `lastName`, and `age`. The `person` object conforms to this interface because it has the expected properties with the correct data types.

Here are some key points about interfaces in TypeScript:

1. **Shape and Structure**: Interfaces define the expected shape and structure of an object. They don't provide implementations; they only describe the structure.

2. **Type Checking**: When you use an interface to define a type, TypeScript checks that objects of that type adhere to the interface's structure. If an object doesn't have the required properties or has properties of the wrong types, TypeScript will raise a type error.

3. **Optional Properties**: You can specify optional properties in an interface by using a `?` after the property name. For example:

   ```typescript
   interface Product {
       name: string;
       price?: number;
   }
   ```

   This means that an object of type `Product` can have a `price` property, but it's not required.

4. **Readonly Properties**: You can make properties in an interface read-only by using the `readonly` keyword:

   ```typescript
   interface Point {
       readonly x: number;
       readonly y: number;
   }
   ```

   This ensures that the properties cannot be modified after they are assigned.

5. **Function Signatures**: Interfaces can also define function signatures. This allows you to specify the shape of functions that objects implementing the interface must have:

   ```typescript
   interface MathFunction {
       (x: number, y: number): number;
   }
   ```

   Here, `MathFunction` describes a function that takes two numbers and returns a number.

6. **Extending Interfaces**: You can extend one interface from another to create a new interface that includes all the properties and methods from both:

   ```typescript
   interface Shape {
       color: string;
   }

   interface Circle extends Shape {
       radius: number;
   }
   ```

   The `Circle` interface inherits the `color` property from the `Shape` interface and adds the `radius` property.

7. **Implements Keyword**: You can use the `implements` keyword to specify that a class adheres to an interface:

   ```typescript
   class PersonClass implements Person {
       firstName: string;
       lastName: string;
       age: number;
   }
   ```

   This enforces that the `PersonClass` class must have the properties defined in the `Person` interface.

Interfaces in TypeScript are a powerful tool for enforcing type checking, creating contracts, and ensuring the expected structure of objects in your code, which can lead to more robust and maintainable software.


### Q12: When to use interfaces and when to use classes in TypeScript? ⭐⭐

**Answer:**

If you need/wish to create an instance of perhaps a custom object, whilst getting the benefits of type-checking things such as arguments, return types or generics - a class makes sense. 

If you’re not creating instances - we have interfaces at our disposal, and their benefit comes from not generating any source code, yet allowing us to somewhat “virtually” type-check our code.

🔗 **Source:** [toddmotto.com](https://toddmotto.com/classes-vs-interfaces-in-typescript)


### Q13: What is the difference between Classes and Interfaces in Typescript? ⭐⭐

**Answer:**
In TypeScript, both classes and interfaces are used to define the structure of objects and their types. However, they serve different purposes and have distinct characteristics. Here are the key differences between classes and interfaces in TypeScript:

1. **Purpose**:
   - **Classes**: Classes are used to define blueprints for creating objects (instances). They can include both property and method implementations. Classes can be instantiated to create objects with specific behavior.
   - **Interfaces**: Interfaces are used to define contracts or blueprints for the shape and structure of objects. They describe the properties and methods an object should have without providing the implementation. Interfaces focus on specifying the structure and type of objects.

2. **Implementation**:
   - **Classes**: Classes can include property and method implementations. You can define how properties are initialized and how methods behave within a class.
   - **Interfaces**: Interfaces do not provide implementations for properties or methods. They only specify the names, types, and structure of properties and method signatures.

3. **Instantiation**:
   - **Classes**: You can create instances (objects) from classes using the `new` keyword. Classes are typically used for creating and managing objects with behavior.
   - **Interfaces**: Interfaces themselves cannot be instantiated. They are used to define the shape of objects that implement them.

4. **Inheritance**:
   - **Classes**: Classes support inheritance. You can create subclasses that inherit properties and methods from a base class. TypeScript allows for single inheritance.
   - **Interfaces**: Interfaces support multiple inheritance. A class or object can implement multiple interfaces, inheriting the structure from each interface.

5. **Usage**:
   - **Classes**: Classes are used when you want to create objects with behavior. You can define classes for things like entities, components, services, or any objects that need to encapsulate state and behavior.
   - **Interfaces**: Interfaces are used to define contracts for objects. They are often used for defining data structures, ensuring objects adhere to certain structures, and promoting code consistency.

6. **Modifiers**:
   - **Classes**: You can use access modifiers (e.g., `public`, `private`, `protected`) to control the visibility and accessibility of class members (properties and methods). Classes also support instance and static members.
   - **Interfaces**: Interfaces do not include access modifiers or instance/static members. All members of an interface are assumed to be public.

7. **Extending**:
   - **Classes**: Classes can extend other classes using the `extends` keyword to inherit properties and methods from a parent class.
   - **Interfaces**: Interfaces can extend other interfaces using the `extends` keyword to inherit members from one or more parent interfaces.

In summary, classes are used for creating objects with behavior and encapsulating state, while interfaces are used for defining contracts and specifying the shape of objects. They serve different purposes and can be used together in TypeScript to achieve robust and maintainable code. Classes provide implementation, while interfaces provide structure and type information.


### Q14: What is "Decorators" in TypeScript? ⭐⭐

**Answer:**

Decorators in TypeScript are a powerful and flexible way to add metadata, behavior, and functionality to classes, methods, properties, or function parameters. They are a form of metaprogramming that allows you to annotate and modify the behavior of your code at design time (compile time). Decorators are typically prefixed with the `@` symbol and are placed immediately before the declaration they are decorating.

Decorators are a language feature inspired by the decorator pattern and are commonly used in various TypeScript and JavaScript frameworks and libraries, such as Angular and Nest.js.

Here are some key points about decorators in TypeScript:

1. **Types of Decorators**: TypeScript supports several types of decorators, including class decorators, method decorators, property decorators, and parameter decorators. Each type is used to annotate different parts of your code.

2. **Syntax**: Decorators are functions that are executed with specific parameters based on the type of declaration they are applied to. A decorator function receives either the constructor function (for class decorators), the target object (for method and property decorators), or the target function and its parameter index (for parameter decorators).

3. **Common Use Cases**:
   - **Class Decorators**: Used to modify or enhance the behavior of classes. They are often used in frameworks to add features like dependency injection, routing, and more.
   - **Method Decorators**: Applied to methods within a class to alter their behavior. They can be used for tasks like logging, authentication, or performance measurement.
   - **Property Decorators**: Applied to class properties to add metadata or behavior. For example, they can be used to mark a property as required in a serialization context.
   - **Parameter Decorators**: Used to access information about function parameters. They are less common but can be useful for advanced use cases.

4. **Decorator Composition**: You can apply multiple decorators to a single declaration, and they are executed in the order they are listed. This allows for flexible and composable behavior customization.

5. **Built-in and Custom Decorators**: TypeScript provides built-in decorators like `@deprecated` and `@experimental` for common scenarios. You can also create custom decorators tailored to your specific needs.

6. **Metadata Reflection**: Decorators can be used to add metadata to your code. The `reflect-metadata` library can be used to access this metadata at runtime. This is particularly useful in certain advanced scenarios, such as dependency injection.

Here's a basic example of a class decorator:

```typescript
function MyClassDecorator(target: Function) {
    // Modify or add behavior to the class here
    console.log(`Decorating class: ${target.name}`);
}

@MyClassDecorator
class MyClass {
    // Class definition here
}
```

In this example, `MyClassDecorator` is a custom class decorator function that logs a message when the class is decorated. The `@MyClassDecorator` syntax is used to apply the decorator to the `MyClass` class.

Decorators in TypeScript are a powerful tool for adding metadata, behavior, and features to your code in a modular and reusable way. They are commonly used in various application frameworks and can help you keep your codebase clean and organized while providing extensibility and customization points.


### Q15: What is getters/setters in TypeScript? ⭐⭐

**Answer:**
In TypeScript (and JavaScript), getters and setters are special methods that allow you to define the behavior for getting and setting the values of object properties. They provide a way to control access to the properties of an object and can be used to add validation, computation, or custom behavior when reading or writing property values.

Here's how you can define getters and setters in TypeScript:

**Getter**: A getter method is used to retrieve the value of a property. It is defined using the `get` keyword followed by the property name. Getters do not take any arguments and must have a return value.

```typescript
class Circle {
    private _radius: number = 0;

    get radius(): number {
        return this._radius;
    }
}

const circle = new Circle();
circle.radius = 5; // This sets the _radius property through the setter
console.log(circle.radius); // This retrieves the _radius property through the getter
```

In this example, the `radius` getter allows you to retrieve the value of the private `_radius` property.

**Setter**: A setter method is used to assign a value to a property. It is defined using the `set` keyword followed by the property name. Setters take one argument, which is the value you want to assign to the property.

```typescript
class Circle {
    private _radius: number = 0;

    get radius(): number {
        return this._radius;
    }

    set radius(value: number) {
        if (value >= 0) {
            this._radius = value;
        } else {
            console.error("Radius cannot be negative.");
        }
    }
}

const circle = new Circle();
circle.radius = 5; // This sets the _radius property through the setter
circle.radius = -1; // This triggers the setter and logs an error message
```

In this example, the `radius` setter allows you to assign a value to the private `_radius` property while performing a validation check to ensure that the value is not negative.

**Using Getters and Setters**:
- When you access a property with a getter, you do so as if it were a regular property, without using parentheses.
- When you assign a value to a property with a setter, you also do so as if it were a regular property assignment, without parentheses.

Getters and setters are often used to encapsulate the internal state of a class and provide controlled access to it. They allow you to maintain data integrity and add custom behavior when interacting with an object's properties.


### Q16: How could you check null and undefined in TypeScript? ⭐⭐

**Answer:**

JIn TypeScript, you can check for `null` and `undefined` using various techniques and operators. Here are some common approaches:

1. **Equality Check (== and !=)**:
   - You can use the equality operators `==` and `!=` to check if a value is equal to `null` or `undefined`. However, be cautious when using these operators, as they perform type coercion.

   ```typescript
   let value: string | null | undefined = null;

   if (value == null) {
       console.log("Value is null or undefined.");
   }
   ```

   Using `value == null` checks for both `null` and `undefined`.

2. **Strict Equality Check (=== and !==)**:
   - The strict equality operators `===` and `!==` do not perform type coercion. You can use them to explicitly check if a value is strictly `null` or `undefined`.

   ```typescript
   let value: string | null | undefined = null;

   if (value === null) {
       console.log("Value is strictly null.");
   }

   if (value === undefined) {
       console.log("Value is strictly undefined.");
   }
   ```

   Using `value === null` and `value === undefined` checks for strict equality.

3. **Type Guard Functions**:
   - You can create custom type guard functions that check for `null` or `undefined`. These functions help TypeScript narrow down the type of a variable within a specific code block.

   ```typescript
   function isNullOrUndefined(value: any): value is null | undefined {
       return value === null || value === undefined;
   }

   let value: string | null | undefined = null;

   if (isNullOrUndefined(value)) {
       console.log("Value is null or undefined.");
   }
   ```

   The `isNullOrUndefined` function acts as a type guard and narrows the type of `value` within the `if` block.

4. **Optional Chaining** (TypeScript 3.7+):
   - You can use the optional chaining operator (`?.`) to safely access properties or methods on an object that may be `null` or `undefined`. This operator prevents "nullish" errors.

   ```typescript
   let user = {
       name: "Alice",
       address: null,
   };

   let city = user.address?.city; // No error even if 'address' is null
   ```

   If `user.address` is `null` or `undefined`, `city` will be `undefined`, and no error will occur.

5. **Nullish Coalescing Operator** (TypeScript 3.7+):
   - The nullish coalescing operator (`??`) allows you to provide a default value if a variable is `null` or `undefined`. It checks for "nullish" values and provides a fallback if needed.

   ```typescript
   let value: string | null | undefined = null;
   let result = value ?? "Default Value";
   console.log(result); // "Default Value"
   ```

   In this example, `result` is assigned the default value because `value` is `null`.

Choose the approach that best suits your specific use case and coding style. Using strict equality checks (`===` and `!==`) is a common practice to ensure that you are explicitly checking for `null` or `undefined` without any type coercion.
### Q17: How to implement class constants in TypeScript? ⭐⭐

**Answer:**

In TypeScript, the `const` keyword cannot be used to declare class properties. Doing so causes the compiler to an error with "A class member cannot have the 'const' keyword." TypeScript 2.0 has the `readonly` modifier:

```js
class MyClass {
    readonly myReadonlyProperty = 1;

    myMethod() {
        console.log(this.myReadonlyProperty);
    }
}

new MyClass().myReadonlyProperty = 5; // error, readonly
```

🔗 **Source:** [stackoverflow.com](https://stackoverflow.com/questions/37265275/how-to-implement-class-constants-in-typescript)


### Q18: Could we use TypeScript on backend and how? ⭐⭐

**Answer:**

Typescript doesn’t only work for browser or frontend code, you can also choose to write your backend applications. For example you could choose Node.js and have some additional type safety and the other abstraction that the language brings.

1. Install the default Typescript compiler  

```sh
npm i -g typescript
```
2. The TypeScript compiler takes options in the shape of a tsconfig.json file that determines where to put built files and in general is pretty similar to a babel or webpack config.

```sh
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "declaration": true,
    "outDir": "build"
  }
}
```
3. Compile ts files

```sh
tsc
```
4. Run

```js
node build/index.js
```

🔗 **Source:** [jonathanmh.com](https://jonathanmh.com/typescript-node-js-tutorial-backend-beginner/)


### Q19: Does TypeScript support all object oriented principles? ⭐⭐

**Answer:**

The answer is **YES**. There are 4 main principles to Object Oriented Programming: 

* Encapsulation, 
* Inheritance, 
* Abstraction, and 
* Polymorphism. 

TypeScript can implement all four of them with its smaller and cleaner syntax.

🔗 **Source:** [jonathanmh.com](https://jonathanmh.com/typescript-node-js-tutorial-backend-beginner/)


### Q20: Which object oriented terms are supported by TypeScript? ⭐⭐

**Answer:**

TypeScript supports following object oriented terms:

*   Modules
*   Classes
*   Interfaces
*   Data Types
*   Member functions

🔗 **Source:** [http://www.talkingdotnet.com](http://www.talkingdotnet.com/typescript-interview-questions/)


### Q21: What is a TypeScript Map file? ⭐⭐

**Answer:**

`.map` files are source map files that let tools map between the emitted JavaScript code and the TypeScript source files that created it. Many debuggers (e.g. Visual Studio or Chrome's dev tools) can consume these files so you can debug the TypeScript file instead of the JavaScript file.

🔗 **Source:** [stackoverflow.com](https://stackoverflow.com/questions/17493738/what-is-a-typescript-map-file)


### Q22: Explain how and why we could use property decorators in TS? ⭐⭐⭐

 In TypeScript, property decorators are a feature used to modify or add behavior to class properties. They are a part of TypeScript's decorator system, which provides a way to annotate and modify the behavior of class members, such as properties and methods. Property decorators are typically prefixed with the @ symbol and are applied just before a property declaration within a class.

Here's how you can define and use property decorators in TypeScript:

typescript

```
function myPropertyDecorator(target: any, propertyKey: string) {
    // Modify or add behavior to the property here
    console.log(`Decorating property ${propertyKey} of class ${target.constructor.name}`);
}

class MyClass {
    @myPropertyDecorator
    myProperty: string = "Hello, world!";
}

const instance = new MyClass();

```


### Q23: Are strongly-typed functions as parameters possible in TypeScript? ⭐⭐⭐

**Questions Details:**

Consider the code:

```js
class Foo {
    save(callback: Function) : void {
        //Do the save
        var result : number = 42; //We get a number from the save operation
        //Can I at compile-time ensure the callback accepts a single parameter of type number somehow?
        callback(result);
    }
}

var foo = new Foo();
var callback = (result: string) : void => {
    alert(result);
}
foo.save(callback);
```
Can you make the result parameter in `save` a type-safe function? Rewrite the code to demonstrate.


 


### Q24: Is that TypeScript code valid? Explain why. ⭐⭐⭐

**Questions Details:**

Consider:
```js
class Point {
    x: number;
    y: number;
}

interface Point3d extends Point {
    z: number;
}

let point3d: Point3d = {x: 1, y: 2, z: 3};
```


 


### Q25: What are different components of TypeScript? ⭐⭐⭐

 TypeScript is a programming language that extends JavaScript by adding optional static typing and other features. Its components include:

1. **Type Annotations**: TypeScript allows you to specify data types for variables, function parameters, and return values. Type annotations help catch type-related errors at compile time.

   ```typescript
   let num: number = 42;
   function add(a: number, b: number): number {
       return a + b;
   }
   ```

2. **Interfaces**: Interfaces define contracts for the shape and structure of objects. They specify the properties and methods an object should have. Interfaces are used for enforcing structure and type checking.

   ```typescript
   interface Person {
       firstName: string;
       lastName: string;
   }
   ```

3. **Classes**: TypeScript supports object-oriented programming with classes. You can define classes, create instances, and use inheritance and access modifiers like `public`, `private`, and `protected`.

   ```typescript
   class Animal {
       constructor(public name: string) {}
       makeSound() {
           console.log("Animal sound");
       }
   }
   ```

4. **Generics**: Generics provide a way to create reusable code that can work with different data types while maintaining type safety.

   ```typescript
   function identity<T>(arg: T): T {
       return arg;
   }
   ```

5. **Enums**: Enums are used to define a set of named numeric values, making it easier to work with constants and improve code readability.

   ```typescript
   enum Color {
       Red,
       Green,
       Blue,
   }
   ```

6. **Decorators**: Decorators are used to add metadata and behavior to classes, methods, properties, or function parameters. They are commonly used in frameworks and libraries for tasks like dependency injection and routing.

   ```typescript
   function MyDecorator(target: Function) {
       // Modify or add behavior to the class
   }
   ```

7. **Modules**: TypeScript supports modularization using the `import` and `export` keywords. You can organize your code into reusable modules for better code structure and maintainability.

   ```typescript
   // Exporting module
   export function myFunction() {
       // Function definition
   }

   // Importing module
   import { myFunction } from "./myModule";
   ```

8. **Type Inference**: TypeScript's type inference feature infers types based on context when type annotations are not explicitly provided. This reduces the need for verbose type annotations.

   ```typescript
   let num = 42; // TypeScript infers the type as 'number'
   ```

9. **Type Assertion**: Type assertion allows you to tell TypeScript that you know more about a value's type than TypeScript does. It's a way to override TypeScript's type checking.

   ```typescript
   let value: any = "Hello, TypeScript!";
   let strLength: number = (value as string).length;
   ```

10. **Namespace (Module) Aliases**: You can use the `as` keyword to create aliases for namespaces (modules) when importing or referencing them.

   ```typescript
   import * as mathLib from "./mathLibrary";
   ```

These are some of the key components and features of TypeScript. TypeScript's rich set of features and static typing capabilities make it a valuable tool for building robust and maintainable applications, particularly in larger codebases and projects.


### Q26: How TypeScript is optionally statically typed language? ⭐⭐⭐

 TypeScript is often described as an "optionally statically typed" language because it offers developers the flexibility to choose when and where to apply static type annotations. Here's what this means in practice:

1. **Static Typing**: TypeScript allows developers to specify types for variables, function parameters, and return values using type annotations. For example:

   ```typescript
   function add(a: number, b: number): number {
       return a + b;
   }
   ```

   In this function, both `a` and `b` are explicitly annotated as `number` types. This is static typing because the types are known at compile time, and TypeScript performs type checking to catch type-related errors during development.

2. **Type Inference**: TypeScript also supports type inference. If you don't provide explicit type annotations, TypeScript will infer types based on the values and context. For example:

   ```typescript
   let num = 42; // TypeScript infers 'number' type
   ```

   Here, `num` is inferred to be of type `number` because its initial value is `42`.

3. **Optional Type Annotations**: TypeScript allows you to use type annotations when and where you see fit. If you want to specify types for variables and functions, you can do so. If you prefer not to use type annotations and rely on type inference, that's also perfectly valid. TypeScript doesn't require you to annotate every variable or function.

   ```typescript
   let name: string = "Alice"; // Explicit type annotation
   let age = 30; // Type inference

   function greet(person: string) {
       return `Hello, ${person}!`;
   }
   ```

   In this example, `name` has an explicit type annotation, while `age` relies on type inference. Similarly, the `greet` function has an explicit type annotation for the `person` parameter.

4. **Gradual Typing**: TypeScript allows for gradual adoption of static typing in existing JavaScript codebases. You can start with a JavaScript project and incrementally add type annotations to specific parts of the code where you want to introduce type checking.

5. **Type Any**: TypeScript includes a special type called `any` that can be used to opt out of type checking for a particular value. While it's generally recommended to avoid using `any` in favor of more specific types, it provides a way to work with dynamically typed or untyped JavaScript libraries.

   ```typescript
   let dynamicValue: any = "Hello, TypeScript!";
   ```

   Here, `dynamicValue` is of type `any`, meaning it doesn't undergo type checking.

Overall, TypeScript's "optional static typing" approach means that you have the freedom to choose the level of type safety you want in your code. You can opt for strong static typing where needed, rely on type inference for conciseness and readability, and gradually introduce static typing into your codebase as it makes sense for your project's requirements. This flexibility is one of the reasons why TypeScript is widely adopted and appreciated by developers working on a variety of projects.


### Q27: What is the default access modifier for members of a class in TypeScript? ⭐⭐⭐
In TypeScript, the default access modifier for members (properties and methods) of a class is `public`. This means that if you don't explicitly specify an access modifier for a member, it will be considered as `public` by default.

Here's an example:

```typescript
class MyClass {
    // This property is public by default
    myProperty: number;

    // This method is public by default
    myMethod() {
        // ...
    }
}
```

In this example, both `myProperty` and `myMethod` are considered `public` members because no access modifier (such as `public`, `private`, or `protected`) is explicitly specified. Public members can be accessed from outside the class.

However, it's considered a good practice to explicitly specify access modifiers for class members to make your code's intentions clear and to control the visibility and accessibility of those members. Depending on your design, you may want to use `private` or `protected` access modifiers to restrict access to certain members.
 


### Q28: How can you allow classes defined in a module to accessible outside of the module? ⭐⭐⭐

 In TypeScript, by default, classes, functions, and other entities defined in a module are not accessible outside of that module. However, if you want to make classes defined in a module accessible outside of the module (i.e., you want to export them), you can use the `export` keyword. Here's how you can do it:

1. **Exporting a Class**:

   ```typescript
   // MyClass.ts
   export class MyClass {
       // Class definition here
   }
   ```

   In this example, we have a module file named `MyClass.ts`, and we're exporting the `MyClass` class using the `export` keyword. This allows other modules to import and use `MyClass`.

2. **Importing a Class**:

   To access the exported class in another module, you can use the `import` statement:

   ```typescript
   // AnotherModule.ts
   import { MyClass } from "./MyClass";

   const instance = new MyClass();
   ```

   Here, we import `MyClass` from the `MyClass.ts` module and create an instance of it in the `AnotherModule.ts` module.

3. **Exporting Multiple Entities**:

   You can also export multiple classes, functions, or variables from a module in a single export statement:

   ```typescript
   // MyModule.ts
   export class Class1 {
       // Class definition here
   }

   export class Class2 {
       // Class definition here
   }

   export function myFunction() {
       // Function definition here
   }
   ```

   Then, you can import these entities individually in another module:

   ```typescript
   // AnotherModule.ts
   import { Class1, Class2, myFunction } from "./MyModule";

   const instance1 = new Class1();
   const instance2 = new Class2();
   const result = myFunction();
   ```

By using the `export` keyword, you can control which entities are accessible outside of a module, making them available for use in other parts of your TypeScript application. This modular approach helps organize and structure your code and enables you to reuse classes and functions across different parts of your application.


### Q29: What's wrong with that code? ⭐⭐⭐

**Questions Details:**

```js
// something is wrong
function reverse(s: String): String;
```


 


### Q30: Does TypeScript supports function overloading? ⭐⭐⭐

 Yes, TypeScript supports function overloading, which allows you to define multiple function signatures for a single function. Function overloading is a feature that helps improve type safety and code clarity when dealing with functions that can accept different sets of arguments or return different types based on the input.

To define function overloads in TypeScript, you use the `function` keyword with multiple signatures followed by the actual implementation of the function. Here's an example:

```typescript
function greet(name: string): string;
function greet(firstName: string, lastName: string): string;

function greet(arg1: string, arg2?: string): string {
    if (arg2) {
        return `Hello, ${arg1} ${arg2}!`;
    } else {
        return `Hello, ${arg1}!`;
    }
}

const result1 = greet("Alice"); // "Hello, Alice!"
const result2 = greet("John", "Doe"); // "Hello, John Doe!"
```

In this example, we have two function signatures for the `greet` function. The first signature takes a single `name` argument, and the second signature takes two arguments, `firstName` and `lastName`. The actual implementation of the function uses these signatures to determine how to generate the greeting message based on the provided arguments.

When you call the `greet` function, TypeScript analyzes the number and types of arguments and selects the appropriate signature to apply. This allows for type-safe function calls with different argument patterns.

Function overloading is particularly useful when you want to provide a clear and consistent API for a function that can handle various input scenarios, such as optional or variant arguments, while maintaining type safety and code readability.


### Q31: How To Use external plain JavaScript Libraries in TypeScript? ⭐⭐⭐

 


### Q32: What is Typings in Typescript? ⭐⭐⭐

 


### Q33: What is the difference between "interface vs type" statements? ⭐⭐⭐⭐

**Questions Details:**

```js
interface X {
    a: number
    b: string
}

type X = {
    a: number
    b: string
};
```


 


### Q34: How would you overload a class constructor in TypeScript? ⭐⭐⭐⭐

 


### Q35: Explain why that code is marked as WRONG? ⭐⭐⭐⭐

**Questions Details:**

```js
/* WRONG */
interface Fetcher {
    getObject(done: (data: any, elapsedTime?: number) => void): void;
}
```


 


### Q36: What is one thing you would change about TypeScript? ⭐⭐⭐⭐⭐

 


### Q37: Explain when to use "declare" keyword in TypeScript ⭐⭐⭐⭐⭐

 


### Q38: What are Ambients in TypeScripts and when to use them? ⭐⭐⭐⭐⭐

 


### Q39: Is it possible to generate TypeScript declaration files from JS library? ⭐⭐⭐⭐⭐

 






