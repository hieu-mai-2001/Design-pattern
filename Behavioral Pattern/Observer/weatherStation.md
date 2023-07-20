```php
// Subject (Observable) Interface
interface Subject {
    public function addObserver(Observer $observer);
    public function removeObserver(Observer $observer);
    public function notifyObservers();
}

// Observer Interface
interface Observer {
    public function update($temperature, $humidity, $pressure);
}

// Weather Station (Concrete Subject)
class WeatherStation implements Subject {
    private $observers = [];
    private $temperature;
    private $humidity;
    private $pressure;

    public function addObserver(Observer $observer) {
        $this->observers[] = $observer;
    }

    public function removeObserver(Observer $observer) {
        $index = array_search($observer, $this->observers);
        if ($index !== false) {
            array_splice($this->observers, $index, 1);
        }
    }

    public function setWeatherData($temperature, $humidity, $pressure) {
        $this->temperature = $temperature;
        $this->humidity = $humidity;
        $this->pressure = $pressure;
        $this->notifyObservers();
    }

    public function notifyObservers() {
        foreach ($this->observers as $observer) {
            $observer->update($this->temperature, $this->humidity, $this->pressure);
        }
    }
}

// Display (Concrete Observer)
class Display implements Observer {
    private $name;

    public function __construct($name) {
        $this->name = $name;
    }

    public function update($temperature, $humidity, $pressure) {
        echo "[$this->name] - Temperature: $temperature°C, Humidity: $humidity%, Pressure: $pressure hPa\n";
    }
}

// Usage
$weatherStation = new WeatherStation();

$display1 = new Display("Display 1");
$display2 = new Display("Display 2");

$weatherStation->addObserver($display1);
$weatherStation->addObserver($display2);

$weatherStation->setWeatherData(25, 60, 1013);

// Output:
// [Display 1] - Temperature: 25°C, Humidity: 60%, Pressure: 1013 hPa
// [Display 2] - Temperature: 25°C, Humidity: 60%, Pressure: 1013 hPa

$weatherStation->removeObserver($display2);

$weatherStation->setWeatherData(30, 55, 1010);

// Output:
// [Display 1] - Temperature: 30°C, Humidity: 55%, Pressure: 1010 hPa

```