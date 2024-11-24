# Decorator Pattern

## Purpose

- Dynamically adds additional responsibilities to an object without modifying its code.

## Use Case

- Adding behaviors to UI components or functionalities like logging or data compression.

```php
interface Coffee {
    public function cost(): float;
    public function description(): string;
}

class BasicCoffee implements Coffee {
    public function cost(): float {
        return 10;
    }

    public function description(): string {
        return "Basic Coffee";
    }
}

class MilkDecorator implements Coffee {
    private Coffee $coffee;

    public function __construct(Coffee $coffee) {
        $this->coffee = $coffee;
    }

    public function cost(): float {
        return $this->coffee->cost() + 2;
    }

    public function description(): string {
        return $this->coffee->description() . ", Milk";
    }
}

```
