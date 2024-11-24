# Proxy Pattern

## Purpose

- Controls access to an object, providing a surrogate or placeholder.

## Use Case

- Security, lazy initialization, or logging.

```php
// Step 1: This interface defines the operations that both the real object and the proxy will implement
interface DocumentInterface
{
    public function display(): void;
}

// Step 2: the actual object that the proxy controls access to
class RealDocument implements DocumentInterface
{
    private string $filename;

    public function __construct(string $filename)
    {
        $this->filename = $filename;
        $this->loadFromDisk();
    }

    private function loadFromDisk(): void
    {
        echo "Loading document from disk: {$this->filename}\n";
    }

    public function display(): void
    {
        echo "Displaying document: {$this->filename}\n";
    }
}

// Step 3: The proxy adds a layer between the client and the real object. It loads the real document only when necessary
class DocumentProxy implements DocumentInterface
{
    private string $filename;
    private ?RealDocument $realDocument = null;

    public function __construct(string $filename)
    {
        $this->filename = $filename;
    }

    public function display(): void
    {
        if ($this->realDocument === null) {
            echo "Proxy initializing and loading document...\n";
            $this->realDocument = new RealDocument($this->filename);
        }
        $this->realDocument->display();
    }
}

// Step 4: Client Code (The client interacts with the proxy as if it's the real object)
echo "--- Proxy Pattern Example ---\n";
$document = new DocumentProxy("example.pdf");

// First call - initializes the RealDocument and loads from disk
$document->display();

// Second call - uses the already-loaded RealDocument
$document->display();

```
