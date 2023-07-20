### Example: Sorting Algorithms
In this example, we'll create a basic text formatting system that allows us to decorate text with different styles such as bold and italic.

1. Step 1: Define the Component interface (TextInterface) representing the core functionality.
```php
   // Component interface
interface TextInterface {
    public function format(): string;
}

```
2. Step 2: Implement the Concrete Component (PlainText) representing the core text without any decoration.
```php
// Concrete Component
class PlainText implements TextInterface {
    private $text;

    public function __construct(string $text) {
        $this->text = $text;
    }

    public function format(): string {
        return $this->text;
    }
}

```
3. Step 3: Create the Decorator base class (TextDecorator) that implements the Component interface and maintains a reference to the Component object.
```php
// Decorator base class
abstract class TextDecorator implements TextInterface {
    protected $textComponent;

    public function __construct(TextInterface $textComponent) {
        $this->textComponent = $textComponent;
    }

    public function format(): string {
        return $this->textComponent->format();
    }
}

```
4. Step 4: Implement the Concrete Decorators (BoldText and ItalicText) that add specific styles to the Component.
```php
// Concrete Decorator - Bold Text
class BoldText extends TextDecorator {
    public function format(): string {
        return "<b>" . parent::format() . "</b>";
    }
}

// Concrete Decorator - Italic Text
class ItalicText extends TextDecorator {
    public function format(): string {
        return "<i>" . parent::format() . "</i>";
    }
}

```
5. Step 5: Compose decorators to achieve the desired combination of functionalities.
```php
// Usage example
$plainText = new PlainText("Hello, World!");

// Apply decorators
$boldText = new BoldText($plainText);
$italicText = new ItalicText($plainText);
$boldItalicText = new BoldText(new ItalicText($plainText));

// Output
echo $boldText->format(); // Output: <b>Hello, World!</b>
echo $italicText->format(); // Output: <i>Hello, World!</i>
echo $boldItalicText->format(); // Output: <b><i>Hello, World!</i></b>

```