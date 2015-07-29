# Steps to setup swift cluster

## Swift Common tasks (all nodes)
  * Install Swift (from source or from rpms)
    * TODO: install from source
  * Install other dependencies
  * create /etc/swift directory
  * create swift.conf in /etc/swift
  * TODO: setup ntp server
  * TODO: create memcache.conf in /etc/swift
  * create /var/cache/swift
  * create /var/run/swift

## Proxy nodes
  * create proxy-server.conf in /etc/swift
  * create object-expirer.conf in /etc/swift
  * TODO: make sure memcache is running
  * TODO: start proxy server
  * TODO: start object-expirer server

## Storage nodes
  * setup disks
  * setup rsync
  * TODO (fix templates):create *-server.conf in /etc/swift
  * TODO: create *-replication.conf in /etc/swift ???
  * TODO: create container-reconciler.conf in /etc/swift ???
  * TODO: any other conf files?
  * TODO: start storage services

## Monitoring nodes
  * TODO: add graphite nodes
  * TODO: setup statsd

## Maintenance
  * TODO: Disk clean-up
  * TODO: deploy new rings
