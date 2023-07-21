1. Product Interface: Pizza.php
```php
// Product Interface
interface Pizza {
    public function prepare();
    public function bake();
    public function cut();
    public function box();
}

```

2. Concrete Products: MargheritaPizza.php and PepperoniPizza.php
```php
// Concrete Product: MargheritaPizza
class MargheritaPizza implements Pizza {
    public function prepare() {
        return "Preparing Margherita pizza.";
    }

    public function bake() {
        return "Baking Margherita pizza.";
    }

    public function cut() {
        return "Cutting Margherita pizza.";
    }

    public function box() {
        return "Packaging Margherita pizza.";
    }
}

// Concrete Product: PepperoniPizza
class PepperoniPizza implements Pizza {
    public function prepare() {
        return "Preparing Pepperoni pizza.";
    }

    public function bake() {
        return "Baking Pepperoni pizza.";
    }

    public function cut() {
        return "Cutting Pepperoni pizza.";
    }

    public function box() {
        return "Packaging Pepperoni pizza.";
    }
}

```

3. Creator (Factory) Interface: PizzaFactory.php
```php
// Creator (Factory) Interface
interface PizzaFactory {
    public function createPizza(): Pizza;
}

```

4. Concrete Creators (Factories): MargheritaPizzaFactory.php and PepperoniPizzaFactory.php
```php
// Concrete Creator: MargheritaPizzaFactory
class MargheritaPizzaFactory implements PizzaFactory {
    public function createPizza(): Pizza {
        return new MargheritaPizza();
    }
}

// Concrete Creator: PepperoniPizzaFactory
class PepperoniPizzaFactory implements PizzaFactory {
    public function createPizza(): Pizza {
        return new PepperoniPizza();
    }
}

```

5. Now, let's see how we can use the Factory Method pattern to create different types of pizzas in the client code:
```php
// Client Code
function orderPizza(PizzaFactory $factory) {
    $pizza = $factory->createPizza();
    echo $pizza->prepare() . "\n";
    echo $pizza->bake() . "\n";
    echo $pizza->cut() . "\n";
    echo $pizza->box() . "\n";
}

// Ordering a Margherita Pizza
$margheritaFactory = new MargheritaPizzaFactory();
orderPizza($margheritaFactory);

// Ordering a Pepperoni Pizza
$pepperoniFactory = new PepperoniPizzaFactory();
orderPizza($pepperoniFactory);

```

6. Output:
```php
Preparing Margherita pizza.
Baking Margherita pizza.
Cutting Margherita pizza.
Packaging Margherita pizza.
Preparing Pepperoni pizza.
Baking Pepperoni pizza.
Cutting Pepperoni pizza.
Packaging Pepperoni pizza.

```
