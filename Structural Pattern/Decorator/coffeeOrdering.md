### Example: Sorting Algorithms
An example of using the Decorator Pattern in PHP for a simple coffee ordering system.

1. Step 1: Define the Component interface (CoffeeInterface) representing the core functionality.
```php
 // Component interface
interface CoffeeInterface {
    public function cost(): float;
    public function description(): string;
}

```
2. Step 2: Implement the Concrete Component (SimpleCoffee) representing a basic cup of coffee.
```php
// Concrete Component
class SimpleCoffee implements CoffeeInterface {
    public function cost(): float {
        return 3.0;
    }

    public function description(): string {
        return "Simple Coffee";
    }
}

```
3. Step 3: Create the Decorator base class (CoffeeDecorator) that implements the Component interface and maintains a reference to the Component object.
```php
// Decorator base class
abstract class CoffeeDecorator implements CoffeeInterface {
    protected $coffee;

    public function __construct(CoffeeInterface $coffee) {
        $this->coffee = $coffee;
    }

    public function cost(): float {
        return $this->coffee->cost();
    }

    public function description(): string {
        return $this->coffee->description();
    }
}

```
4. Step 4: Implement the Concrete Decorators (Milk and Vanilla) that add specific extras to the coffee.
```php
// Concrete Decorator - Milk
class Milk extends CoffeeDecorator {
    public function cost(): float {
        return $this->coffee->cost() + 1.0;
    }

    public function description(): string {
        return $this->coffee->description() . ", Milk";
    }
}

// Concrete Decorator - Vanilla
class Vanilla extends CoffeeDecorator {
    public function cost(): float {
        return $this->coffee->cost() + 0.5;
    }

    public function description(): string {
        return $this->coffee->description() . ", Vanilla";
    }
}

```
5. Step 5: Compose decorators to achieve the desired combination of functionalities.
```php
// Usage example
$coffee = new SimpleCoffee();

// Apply decorators
$coffeeWithMilk = new Milk($coffee);
$coffeeWithMilkAndVanilla = new Vanilla($coffeeWithMilk);

// Output
echo $coffee->description(); // Output: Simple Coffee
echo $coffee->cost(); // Output: 3.0

echo $coffeeWithMilk->description(); // Output: Simple Coffee, Milk
echo $coffeeWithMilk->cost(); // Output: 4.0

echo $coffeeWithMilkAndVanilla->description(); // Output: Simple Coffee, Milk, Vanilla
echo $coffeeWithMilkAndVanilla->cost(); // Output: 4.5

```