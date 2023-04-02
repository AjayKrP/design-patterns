# Design Patterns
Have you ever built something with Legos or blocks? Design patterns are like building instructions for software developers. Just like how you can follow instructions to build a cool Lego house, software developers can follow design patterns to build better software.

Design patterns are like a toolbox for developers. Inside the toolbox, there are different tools for solving different problems. Design patterns are like the tools inside the toolbox that developers can use to solve problems in their code.

For example, let's say a developer is building a new app, and they need to figure out how to create a new object in their code. They could spend a lot of time figuring out the best way to do it, or they could use a design pattern like the Factory Method, which is like a set of instructions for creating objects in a specific way.

Just like how you can use building instructions to build a really cool Lego house, software developers can use design patterns to build really cool software that's easy to understand, maintain, and improve over time.

1. Creational Design Patterns

Creational design patterns are a set of patterns in software engineering that deal with object creation mechanisms. These patterns provide a way to create objects in a manner suitable to the situation, while also hiding the complexity of the creation process from the user.

In general, creational design patterns aim to separate the process of object creation from the rest of the code, so that changes to the creation process do not affect other parts of the program. This makes the code more modular, easier to maintain, and more flexible.

There are several types of creational design patterns, including:

    - Singleton - Ensures that only one instance of a class can be created.
    - Factory Method - Provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created.
    - Abstract Factory - Provides an interface for creating related or dependent objects without specifying their concrete classes.
    - Builder - Separates the construction of a complex object from its representation, allowing the same construction process to create different representations.
    - Prototype - Allows new objects to be created from existing objects by cloning them, rather than by calling a constructor.

These design patterns are widely used in software development, and they can help to improve the quality of code by making it more modular, maintainable, and flexible.

2. Structural Design Patterns

A structural design pattern deals with class and object composition, or how to assemble objects and classes into larger structures.

    - Adapter: How to change or adapt an interface to that of another existing class to allow incompatible interfaces to work together.
    - Bridge: A method to decouple an interface from its implementation.
    - Composite: Leverages a tree structure to support manipulation as one object.
    - Decorator: Dynamically extends (adds or overrides) functionality.
    - Façade: Defines a high-level interface to simplify the use of a large body of code.
    - Flyweight: Minimize memory use by sharing data with similar objects.
    - Proxy: How to represent an object with another object to enable access control, reduce cost and reduce complexity.

3. Behavioral Design Patterns

A behavioral design pattern is concerned with communication between objects and how responsibilities are assigned between objects.

    - Chain of Responsibility: A method for commands to be delegated to a chain of processing objects.
    - Command: Encapsulates a command request in an object.
    - Interpreter: Supports the use of language elements within an application.
    - Iterator: Supports iterative (sequential) access to collection elements.
    - Mediator: Articulates simple communication between classes.
    - Memento: A process to save and restore the internal/original state of an object.
    - Observer: Defines how to notify objects of changes to other object(s).
    - State: How to alter the behavior of an object when its stage changes.
    - Strategy: Encapsulates an algorithm inside a class.
    - Visitor: Defines a new operation on a class without making changes to the class.
    - Template Method: Defines the skeleton of an operation while allowing subclasses to refine certain steps.

# [1.A.] Factory Method
Imagine you're playing a game where you can create different types of animals - a lion, a tiger, or a bear. But every time you want to create one, you have to figure out how to make it from scratch using all sorts of different parts. It's fun, but it can get pretty complicated and time-consuming!

So, your friend suggests a new tool called the "Animal Factory". This is a special tool that you can use to create any animal you want, just by telling it what kind of animal you want to make.

Here's how you might use the Animal Factory in TypeScript:

First, you would create a class for the Animal Factory itself. This class would have a method called "createAnimal" that takes in a string representing the type of animal you want to create.


```typescript
class AnimalFactory {
  createAnimal(type: string): Animal {
    // code to create the animal goes here
  }
}
```

Next, you would create classes for each type of animal you want to create - Lion, Tiger, and Bear. Each of these classes would implement a common interface called "Animal", which would define the methods and properties that all animals have.

```typescript
interface Animal {
  name: string;
  makeSound(): void;
}

class Lion implements Animal {
  name: string = "Lion";
  makeSound(): void {
    console.log("Roar!");
  }
}

class Tiger implements Animal {
  name: string = "Tiger";
  makeSound(): void {
    console.log("Rawr!");
  }
}

class Bear implements Animal {
  name: string = "Bear";
  makeSound(): void {
    console.log("Growl!");
  }
}
```
Finally, you would use the Animal Factory to create new animals whenever you wanted. To create a lion, for example, you would call the createAnimal method on the Animal Factory and pass in the string "Lion":

```typescript
const animalFactory = new AnimalFactory();
const myLion = animalFactory.createAnimal("Lion");
console.log(myLion.name); // Output: Lion
myLion.makeSound(); // Output: Roar!
```
And just like that, you've created a lion without having to worry about all the details of how it's made! If you ever want to change how the Lion is created, you can just update the code in the Lion class, and the Animal Factory will use the new version the next time you create a Lion.

# [1.B.] Abstract Factory
Imagine you're playing a game where you can create different types of animals, just like before. But this time, there are different types of environments - a jungle, a forest, or a desert - and each environment has its own set of animals that live there.

So, your friend suggests a new tool called the "Animal Habitat Factory". This is a special tool that you can use to create animals that are specifically designed to live in a certain environment.

Here's how you might use the Animal Habitat Factory in TypeScript:

First, you would create a class for the Animal Habitat Factory itself. This class would have a method called "createAnimalHabitat" that takes in a string representing the type of environment you want to create animals for.

```typescript
class AnimalHabitatFactory {
  createAnimalHabitat(type: string): AnimalHabitat {
    // code to create the animal habitat goes here
  }
}
```
Next, you would create a set of interfaces for each type of animal that you want to create, just like before. But this time, you would also create a new interface called "AnimalHabitat" that defines the methods for creating each type of animal.

```typescript
interface Animal {
  name: string;
  makeSound(): void;
}

interface Lion extends Animal {
  // additional properties and methods specific to a lion
}

interface Tiger extends Animal {
  // additional properties and methods specific to a tiger
}

interface Bear extends Animal {
  // additional properties and methods specific to a bear
}

interface AnimalHabitat {
  createLion(): Lion;
  createTiger(): Tiger;
  createBear(): Bear;
}
```
Now, you would create a set of classes that implement the AnimalHabitat interface, one for each type of environment you want to create animals for.

```typescript
class JungleHabitat implements AnimalHabitat {
  createLion(): Lion {
    return new JungleLion();
  }

  createTiger(): Tiger {
    return new JungleTiger();
  }

  createBear(): Bear {
    return new JungleBear();
  }
}

class ForestHabitat implements AnimalHabitat {
  createLion(): Lion {
    return new ForestLion();
  }

  createTiger(): Tiger {
    return new ForestTiger();
  }

  createBear(): Bear {
    return new ForestBear();
  }
}

class DesertHabitat implements AnimalHabitat {
  createLion(): Lion {
    return new DesertLion();
  }

  createTiger(): Tiger {
    return new DesertTiger();
  }

  createBear(): Bear {
    return new DesertBear();
  }
}
```
Each of these classes creates animals that are specifically designed to live in their respective environments. For example, a JungleHabitat creates animals like the JungleLion, JungleTiger, and JungleBear, which all have specific characteristics that make them well-suited for life in the jungle.

Finally, you would use the Animal Habitat Factory to create new animals in a specific environment whenever you wanted.

```typescript
const animalHabitatFactory = new AnimalHabitatFactory();
const myJungle = animalHabitatFactory.createAnimalHabitat("Jungle");
const myLion = myJungle.createLion();
console.log(myLion.name); // Output: Jungle Lion
myLion.makeSound(); // Output: Roar!
```
And just like that, you've created a Jungle Lion without having to worry about all the details of how it's made! If you ever want to change how the Jungle Lion is created, you can just update the code in the JungleLion class, and the Animal Habitat Factory

# [1.C.] Builder
Let's say you're a pizza chef, and you want to create a pizza builder tool to help you build custom pizzas. The pizza builder tool would allow you to specify which toppings, cheese, sauce, and crust you want to use for each pizza.

Here's how you might use the Pizza Builder in TypeScript:

First, you would create a class for the Pizza Builder itself. This class would have methods for adding different types of toppings, cheese, sauce, and crust to the pizza.

```typescript
class PizzaBuilder {
  private toppings: string[] = [];
  private cheese: string = "mozzarella";
  private sauce: string = "tomato";
  private crust: string = "regular";

  addTopping(topping: string): void {
    this.toppings.push(topping);
  }

  setCheese(cheese: string): void {
    this.cheese = cheese;
  }

  setSauce(sauce: string): void {
    this.sauce = sauce;
  }

  setCrust(crust: string): void {
    this.crust = crust;
  }

  build(): string {
    const pizza = `Cheese: ${this.cheese}, Sauce: ${this.sauce}, Crust: ${this.crust}, Toppings: ${this.toppings.join(", ")}`;
    this.reset();
    return pizza;
  }

  private reset(): void {
    this.toppings = [];
    this.cheese = "mozzarella";
    this.sauce = "tomato";
    this.crust = "regular";
  }
}
```
Next, you would use the Pizza Builder to create a new pizza by adding the different ingredients you want to use.

```typescript
const pizzaBuilder = new PizzaBuilder();
pizzaBuilder.setCheese("cheddar");
pizzaBuilder.setSauce("alfredo");
pizzaBuilder.setCrust("thin");
pizzaBuilder.addTopping("pepperoni");
pizzaBuilder.addTopping("mushrooms");
const myPizza = pizzaBuilder.build();
console.log(myPizza); // Output: Cheese: cheddar, Sauce: alfredo, Crust: thin, Toppings: pepperoni, mushrooms
```
And just like that, you've created a custom pizza without having to worry about manually specifying each ingredient! If you ever want to change how the pizza is built, you can just update the code in the Pizza Builder class.

The Builder pattern is a flexible way to create complex objects by breaking them down into smaller parts and then assembling them step by step. It can be used in many different contexts, such as creating user interfaces, generating reports, or building complex data structures.

# [1.D.] Singleton
Imagine you have a special toy, like a remote control car, that you only want one of. You don't want your friends to accidentally create a duplicate of your toy, or for there to be multiple versions of it floating around.

In programming, we sometimes have objects like this that we only want one instance of. That's where the Singleton design pattern comes in! It ensures that we only have one instance of an object, no matter how many times we try to create it.

Here's an example of how you might use the Singleton design pattern in TypeScript:

```typescript
class RemoteControlCar {
  private static instance: RemoteControlCar;

  private constructor() {}

  static getInstance(): RemoteControlCar {
    if (!RemoteControlCar.instance) {
      RemoteControlCar.instance = new RemoteControlCar();
    }
    return RemoteControlCar.instance;
  }

  drive(): void {
    console.log("Driving the remote control car!");
  }
}
```
In this example, we have a class called RemoteControlCar that represents our special toy. The class has a private constructor, which means we can't create new instances of it directly.

Instead, we have a static method called getInstance() that checks whether an instance of RemoteControlCar has already been created. If it hasn't, it creates a new instance and returns it. If it has, it simply returns the existing instance.

Now let's see how we can use the RemoteControlCar class:

```typescript
const myCar = RemoteControlCar.getInstance();
myCar.drive(); // Output: "Driving the remote control car!"

const anotherCar = RemoteControlCar.getInstance();
console.log(myCar === anotherCar); // Output: true
```
As you can see, we can only create one instance of the RemoteControlCar class, even if we try to create it multiple times using the getInstance() method. When we check if myCar and anotherCar are equal, we see that they are, because they are both references to the same object.

So just like how you only have one special toy that you don't want duplicates of, the Singleton design pattern ensures that we only have one instance of an object, no matter how many times we try to create it.
