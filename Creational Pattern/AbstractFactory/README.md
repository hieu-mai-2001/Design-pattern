# Intent
**Abstract Factory** is a creation's design pattern that lets you produce families of related objects without specifying their concrete classes.

# Examples

- **Database Connectivity**: You are building an application that needs to connect to different types of databases (e.g., MySQL, PostgreSQL, MongoDB, etc).
- **Banking System**: You are developing a banking system that supports different types of accounts (savings,checking) and different types of transactions (withdraw, deposit)
- **Restaurant Ordering System**: You are developing a restaurant ordering system that supports different types of menus (breakfast, lunch, dinner) and different types of cuisines (Italian, Chinese,Mexican, etc)

# PseudoCode
```php
// Abstract Factory Interface or Abstract Class
interface AbstractFactory {
    // Factory methods for creating different products (e.g., createProductA, createProductB)
    AbstractProductA createProductA();
    AbstractProductB createProductB();
}

// Concrete Factory Implementations
class ConcreteFactory1 implements AbstractFactory {
    AbstractProductA createProductA() {
        return new ConcreteProductA1();
    }

    AbstractProductB createProductB() {
        return new ConcreteProductB1();
    }
}

class ConcreteFactory2 implements AbstractFactory {
    AbstractProductA createProductA() {
        return new ConcreteProductA2();
    }

    AbstractProductB createProductB() {
        return new ConcreteProductB2();
    }
}

// Abstract Product Interface or Abstract Class (Products in Family A)
interface AbstractProductA {
    // Methods common to products in Family A
    void operationA();
}

// Concrete Product Implementations (Products in Family A)
class ConcreteProductA1 implements AbstractProductA {
    void operationA() {
        // Implement specific operation for Product A1
    }
}

class ConcreteProductA2 implements AbstractProductA {
    void operationA() {
        // Implement specific operation for Product A2
    }
}

// Abstract Product Interface or Abstract Class (Products in Family B)
interface AbstractProductB {
    // Methods common to products in Family B
    void operationB();
}

// Concrete Product Implementations (Products in Family B)
class ConcreteProductB1 implements AbstractProductB {
    void operationB() {
        // Implement specific operation for Product B1
    }
}

class ConcreteProductB2 implements AbstractProductB {
    void operationB() {
        // Implement specific operation for Product B2
    }
}

// Client Code
function clientCode(AbstractFactory factory) {
    AbstractProductA productA = factory.createProductA();
    AbstractProductB productB = factory.createProductB();

    // Use the products from the chosen factory
    productA.operationA();
    productB.operationB();
}

// Usage
AbstractFactory factory1 = new ConcreteFactory1();
clientCode(factory1);

AbstractFactory factory2 = new ConcreteFactory2();
clientCode(factory2);

```