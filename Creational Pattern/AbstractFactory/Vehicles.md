## Example : types of vehicles: cars and motorcycles.

```php
// Abstract Factory
interface VehicleFactory {
    public function createCar(): Car;
    public function createMotorcycle(): Motorcycle;
}

// Concrete Factories
class HondaFactory implements VehicleFactory {
    public function createCar(): Car {
        return new HondaCar();
    }

    public function createMotorcycle(): Motorcycle {
        return new HondaMotorcycle();
    }
}

class YamahaFactory implements VehicleFactory {
    public function createCar(): Car {
        return new YamahaCar();
    }

    public function createMotorcycle(): Motorcycle {
        return new YamahaMotorcycle();
    }
}

// Abstract Products
interface Car {
    public function start();
}

interface Motorcycle {
    public function start();
}

// Concrete Products
class HondaCar implements Car {
    public function start() {
        echo "Starting a Honda car.\n";
    }
}

class YamahaCar implements Car {
    public function start() {
        echo "Starting a Yamaha car.\n";
    }
}

class HondaMotorcycle implements Motorcycle {
    public function start() {
        echo "Starting a Honda motorcycle.\n";
    }
}

class YamahaMotorcycle implements Motorcycle {
    public function start() {
        echo "Starting a Yamaha motorcycle.\n";
    }
}

// Usage
$factory = new HondaFactory();
$car = $factory->createCar();
$motorcycle = $factory->createMotorcycle();

$car->start();        // Output: "Starting a Honda car."
$motorcycle->start(); // Output: "Starting a Honda motorcycle."

$factory = new YamahaFactory();
$car = $factory->createCar();
$motorcycle = $factory->createMotorcycle();

$car->start();        // Output: "Starting a Yamaha car."
$motorcycle->start(); // Output: "Starting a Yamaha motorcycle."

```