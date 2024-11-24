# Adapter Pattern

## Purpose

- Converts the interface of one class into another interface the client expects. It acts as a bridge between two incompatible interfaces.

## Use Case

- Integrating legacy code with new systems.

```php
interface PaymentGateway {
    public function pay(float $amount);
}

class OldPaymentSystem {
    public function processPayment(float $amount) {
        echo "Processing payment of $amount through OldPaymentSystem.\n";
    }
}

class PaymentAdapter implements PaymentGateway {
    private OldPaymentSystem $oldPayment;

    public function __construct(OldPaymentSystem $oldPayment) {
        $this->oldPayment = $oldPayment;
    }

    public function pay(float $amount) {
        $this->oldPayment->processPayment($amount);
    }
}

```
