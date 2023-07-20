```
# Step 1: Create the Strategy Interface or Abstract Class
interface Strategy {
    method execute(data)  # The method that represents the behavior or algorithm
}

# Step 2: Implement Concrete Strategies
class ConcreteStrategyA implements Strategy {
    method execute(data) {
        # Implement specific behavior/algorithm A
    }
}

class ConcreteStrategyB implements Strategy {
    method execute(data) {
        # Implement specific behavior/algorithm B
    }
}

# Step 3: Create the Context Class
class Context {
    private strategy  # Reference to the Strategy interface or abstract class

    method setStrategy(strategy) {
        # Setter to set the concrete strategy to be used
    }

    method executeStrategy(data) {
        strategy.execute(data)  # Delegate the execution to the concrete strategy
    }
}

# Step 4: Client Code
context = new Context()

# Use ConcreteStrategyA
context.setStrategy(new ConcreteStrategyA())
context.executeStrategy(data)

# Use ConcreteStrategyB
context.setStrategy(new ConcreteStrategyB())
context.executeStrategy(data)

```