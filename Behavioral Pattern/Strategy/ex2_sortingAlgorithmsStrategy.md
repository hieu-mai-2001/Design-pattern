###Example: Sorting Algorithms
In this example, we'll demonstrate how to implement different sorting algorithms (e.g., Bubble Sort, Quick Sort, Merge Sort) using the Strategy Pattern. This will allow us to switch between sorting algorithms without modifying the client code.

1. Create the Strategy interface:
```php
interface SortingStrategy
{
    public function sort(array &$data);
}

```

2. Implement the concrete strategies:
```php
class BubbleSort implements SortingStrategy
{
    public function sort(array &$data)
    {
        // Implement Bubble Sort algorithm
        $n = count($data);
        for ($i = 0; $i < $n - 1; $i++) {
            for ($j = 0; $j < $n - $i - 1; $j++) {
                if ($data[$j] > $data[$j + 1]) {
                    $temp = $data[$j];
                    $data[$j] = $data[$j + 1];
                    $data[$j + 1] = $temp;
                }
            }
        }
    }
}

class QuickSort implements SortingStrategy
{
    public function sort(array &$data)
    {
        // Implement Quick Sort algorithm
        sort($data);
    }
}

class MergeSort implements SortingStrategy
{
    public function sort(array &$data)
    {
        // Implement Merge Sort algorithm
        sort($data);
    }
}

```
3. Create the Context class that utilizes the Strategy:
```php
class SortContext
{
    private $sortingStrategy;

    public function setSortingStrategy(SortingStrategy $sortingStrategy)
    {
        $this->sortingStrategy = $sortingStrategy;
    }

    public function sortData(array &$data)
    {
        $this->sortingStrategy->sort($data);
    }
}

```
4. Now, you can use the PaymentContext to change the payment strategy at runtime:
```php
// Client code
$sortContext = new SortContext();

$data = [5, 2, 8, 3, 1, 7];

// Sort using Bubble Sort
$sortContext->setSortingStrategy(new BubbleSort());
$sortContext->sortData($data);
print_r($data);

// Sort using Quick Sort
$sortContext->setSortingStrategy(new QuickSort());
$sortContext->sortData($data);
print_r($data);

// Sort using Merge Sort
$sortContext->setSortingStrategy(new MergeSort());
$sortContext->sortData($data);
print_r($data);

```