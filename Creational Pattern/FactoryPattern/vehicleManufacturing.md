1. Product Interface: Vehicle.php
```php
// Product Interface
interface Vehicle {
    public function assemble();
    public function paint();
}

```

2. Concrete Products: Car.php and Motorcycle.php
```php
// Concrete Product: Car
class Car implements Vehicle {
    public function assemble() {
        return "Assembling car parts.";
    }

    public function paint() {
        return "Painting the car.";
    }
}

// Concrete Product: Motorcycle
class Motorcycle implements Vehicle {
    public function assemble() {
        return "Assembling motorcycle parts.";
    }

    public function paint() {
        return "Painting the motorcycle.";
    }
}

```

3. Creator (Factory) Interface: VehicleFactory.php
```php
// Creator (Factory) Interface
interface VehicleFactory {
    public function createVehicle(): Vehicle;
}

```

4. Concrete Creators (Factories): CarFactory.php and MotorcycleFactory.php
```php
// Concrete Creator: CarFactory
class CarFactory implements VehicleFactory {
    public function createVehicle(): Vehicle {
        return new Car();
    }
}

// Concrete Creator: MotorcycleFactory
class MotorcycleFactory implements VehicleFactory {
    public function createVehicle(): Vehicle {
        return new Motorcycle();
    }
}

```

5. Now, let's see how we can use the Factory Method pattern to create vehicles in the client code:
```php
// Client Code
function manufactureVehicle(VehicleFactory $factory) {
    $vehicle = $factory->createVehicle();
    echo $vehicle->assemble() . "\n";
    echo $vehicle->paint() . "\n";
}

// Creating a Car
$carFactory = new CarFactory();
manufactureVehicle($carFactory);

// Creating a Motorcycle
$motorcycleFactory = new MotorcycleFactory();
manufactureVehicle($motorcycleFactory);

```

6. Output:
```php
Assembling car parts.
Painting the car.
Assembling motorcycle parts.
Painting the motorcycle.

```
