# product-service

## Steps to install
Apache Kafka is a highly-scalable publish-subscribe messaging system that can serve as the data backbone in distributed applications. With Kafka’s Producer-Consumer model it becomes easy to implement multiple data consumers that do live monitoring as well persistent data storage for later analysis.

STEP 1: Installation, the best way to install the latest version of the Kafka server on OS X and to keep it up to date is via Homebrew.
```
$ brew search kafka
$ brew install kafka 
```

this will also install all dependencies, like zookeeper which is required to run kafka server.

STEP 2: we need to start Zookeeper before we can start Kafka.

```
$ zkserver start
```

STEP 3: Once Zookeeper is up start the Kafka server.

```
$ cd /usr/local/Cellar/kafka/0.10.1.0/bin
$ kafka-server-start.sh /usr/local/etc/kafka/server.properties
```

STEP 4: Install Maxwell as a data connector to mysql
```
docker run -it --rm osheroff/maxwell bin/maxwell --user=<user> --password=<pass> --host=<host> --producer=kafka --kafka.bootstrap.servers=<kafka ip>:9092
```

STEP 5: 
Start two deamons to listen data changes and pushlish to client sides
```
- php push-server.php (daemon to push to clients)
- php sendDataByMq.php (daemon to listen changes from mysql)
```

STEP 5:
open file index.html

STEP 5:
create a database and create a catalog_config table
```
CREATE TABLE `catalog_config` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `sku` varchar(256) DEFAULT NULL,
  `price` float DEFAULT NULL,
  `image` text,
  `desc` text,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8;
```

STEP 6:
try to change/insert a row in the table
```
INSERT INTO `catalog_config` (`id`, `sku`, `price`, `image`, `desc`)
VALUES
	(NULL, 'XYZ', 10, '/p/abercrombie-fitch-7370-345226-1.jpg', 'Ruffle Dress from Abercrombie & Fitch');
  ```
