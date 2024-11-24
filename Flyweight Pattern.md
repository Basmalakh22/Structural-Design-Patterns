# Flyweight Pattern

## Purpose

- Minimizes memory usage by sharing objects where possible.

## Use Case

- Large datasets with repeating data, such as rendering fonts or icons.

```php
class Character {
    private string $symbol;

    public function __construct(string $symbol) {
        $this->symbol = $symbol;
    }

    public function render(): string {
        return "Rendering character: $this->symbol\n";
    }
}

class CharacterFactory {
    private array $characters = [];

    public function getCharacter(string $symbol): Character {
        if (!isset($this->characters[$symbol])) {
            $this->characters[$symbol] = new Character($symbol);
        }
        return $this->characters[$symbol];
    }
}

```
