# Facade Pattern

## Purpose

- Provides a unified interface to a set of interfaces in a subsystem.

## Use Case

- Simplifying complex systems, such as database operations or third-party libraries.

```php
class Database {
    public function connect() {
        echo "Connecting to Database.\n";
    }

    public function disconnect() {
        echo "Disconnecting from Database.\n";
    }
}

class Logger {
    public function log(string $message) {
        echo "Logging: $message\n";
    }
}

class ApplicationFacade {
    private Database $db;
    private Logger $logger;

    public function __construct() {
        $this->db = new Database();
        $this->logger = new Logger();
    }

    public function start() {
        $this->db->connect();
        $this->logger->log("Application started.");
    }

    public function stop() {
        $this->logger->log("Application stopped.");
        $this->db->disconnect();
    }
}

```
