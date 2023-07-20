```php
// Subject (Observable) Interface
interface Subject {
    public function addObserver(Observer $observer);
    public function removeObserver(Observer $observer);
    public function notifyObservers();
}

// Observer Interface
interface Observer {
    public function update($article);
}

// News Agency (Concrete Subject)
class NewsAgency implements Subject {
    private $observers = [];
    private $latestArticle;

    public function addObserver(Observer $observer) {
        $this->observers[] = $observer;
    }

    public function removeObserver(Observer $observer) {
        $index = array_search($observer, $this->observers);
        if ($index !== false) {
            array_splice($this->observers, $index, 1);
        }
    }

    public function setLatestArticle($article) {
        $this->latestArticle = $article;
        $this->notifyObservers();
    }

    public function notifyObservers() {
        foreach ($this->observers as $observer) {
            $observer->update($this->latestArticle);
        }
    }
}

// News Outlet (Concrete Observer)
class NewsOutlet implements Observer {
    private $name;

    public function __construct($name) {
        $this->name = $name;
    }

    public function update($article) {
        echo "[$this->name] - New article: $article\n";
    }
}

// Usage
$newsAgency = new NewsAgency();

$outlet1 = new NewsOutlet("TV News");
$outlet2 = new NewsOutlet("Online News");

$newsAgency->addObserver($outlet1);
$newsAgency->addObserver($outlet2);

$newsAgency->setLatestArticle("Breaking News: Earthquake in City XYZ");

// Output:
// [TV News] - New article: Breaking News: Earthquake in City XYZ
// [Online News] - New article: Breaking News: Earthquake in City XYZ

$newsAgency->removeObserver($outlet1);

$newsAgency->setLatestArticle("Sports News: Team ABC wins the championship");

// Output:
// [Online News] - New article: Sports News: Team ABC wins the championship

```