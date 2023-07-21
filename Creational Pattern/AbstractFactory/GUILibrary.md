## Example: GUI Library with Buttons and Checkboxes
Suppose you are developing a GUI library that supports creating buttons and checkboxes for different operating systems: Windows and macOS.

```php
// Abstract Factory
interface GUIFactory {
    public function createButton(): Button;
    public function createCheckbox(): Checkbox;
}

// Concrete Factories
class WindowsGUIFactory implements GUIFactory {
    public function createButton(): Button {
        return new WindowsButton();
    }

    public function createCheckbox(): Checkbox {
        return new WindowsCheckbox();
    }
}

class MacOSGUIFactory implements GUIFactory {
    public function createButton(): Button {
        return new MacOSButton();
    }

    public function createCheckbox(): Checkbox {
        return new MacOSCheckbox();
    }
}

// Abstract Products
interface Button {
    public function render();
}

interface Checkbox {
    public function render();
}

// Concrete Products
class WindowsButton implements Button {
    public function render() {
        echo "Rendering a Windows-style button.\n";
    }
}

class MacOSButton implements Button {
    public function render() {
        echo "Rendering a macOS-style button.\n";
    }
}

class WindowsCheckbox implements Checkbox {
    public function render() {
        echo "Rendering a Windows-style checkbox.\n";
    }
}

class MacOSCheckbox implements Checkbox {
    public function render() {
        echo "Rendering a macOS-style checkbox.\n";
    }
}

// Usage
$factory = new WindowsGUIFactory();
$button = $factory->createButton();
$checkbox = $factory->createCheckbox();

$button->render();    // Output: "Rendering a Windows-style button."
$checkbox->render();  // Output: "Rendering a Windows-style checkbox."

$factory = new MacOSGUIFactory();
$button = $factory->createButton();
$checkbox = $factory->createCheckbox();

$button->render();    // Output: "Rendering a macOS-style button."
$checkbox->render();  // Output: "Rendering a macOS-style checkbox."

```

