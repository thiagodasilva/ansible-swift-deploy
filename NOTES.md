# Steps to setup swift cluster

## Swift Common tasks (all nodes)
  * [x] Install Swift (from source or from rpms)
  * [x] Install other dependencies
  * [x] create /etc/swift directory
  * [x] create swift.conf in /etc/swift
  * [ ] TODO: setup ntp server
  * [ ] TODO: create memcache.conf in /etc/swift
  * [x] create /var/cache/swift
  * [x] create /var/run/swift
  * [ ] TODO: distribute rings

## Proxy nodes
  * [x] create proxy-server.conf in /etc/swift
  * [x] create object-expirer.conf in /etc/swift
  * [ ] TODO: make sure memcache is running
  * [ ] TODO: start proxy server
  * [ ] TODO: start object-expirer server

## Storage nodes
  * [x] setup disks and mount points
  * [x] setup rsync
  * [x] create *-server.conf in /etc/swift
  * [ ] TODO: create *-replication.conf in /etc/swift ???
  * [ ] TODO: create container-reconciler.conf in /etc/swift ???
  * [ ] TODO: any other conf files?
  * [ ] TODO: start storage services
  * [ ] TODO: configure recon
    * [ ] TODO: cron job?

## Maintenance
  * [ ] TODO: Disk clean-up
  * [ ] TODO: deploy new rings
  * [x] update source, install and restart services

## Performance nodes
  * [ ] TODO: add performance measurement nodes (ssbench)

## Monitoring nodes
  * [ ] TODO: add graphite node
  * [ ] TODO: setup statsd

