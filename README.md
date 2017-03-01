# doctrine-dbal-clickhouse

Doctrine DBAL driver for ClickHouse database (https://clickhouse.yandex/)

It is alpha-version!

## Initialization
### Custom PHP script
```
$connectionParams = [
    'host' => 'localhost',
    'port' => 8123,
    'user' => 'default',
    'password' => '',
    'dbname' => 'default',
    'driverClass' => 'Mochalygin\DoctrineDBALClickHouse\Driver',
    'wrapperClass' => 'Mochalygin\DoctrineDBALClickHouse\Connection'
];
$conn = \Doctrine\DBAL\DriverManager::getConnection($connectionParams, new \Doctrine\DBAL\Configuration());
```

### Symfony 2/3
configure...
```
# app/config/config.yml
doctrine:
    dbal:
        connections:
            clickhouse:
                host:     localhost
                port:     8123
                user:     default
                password: null
                dbname:   default
                driver_class: Mochalygin\DoctrineDBALClickHouse\Driver
                wrapper_class: Mochalygin\DoctrineDBALClickHouse\Connection
            #mysql:
            #   ...
```
...and get from the service container
```
$conn = $this->get('doctrine.dbal.clickhouse_connection');
```

## Usage
```
$stmt = $conn->query('SELECT SUM(views) FROM articles');
var_dump($stmt->fetchAll());
```
