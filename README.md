
# diskio2log

Monitor and log some current I/O metrics for selected block device.

## Options

```
$ diskio2log -h
usage: diskio2log [-h] [-i INTERVAL] [-l LOG] [-d DEV]

optional arguments:
  -h, --help            show this help message and exit
  -i INTERVAL, --interval INTERVAL
                        interval in sec
  -l LOG, --log LOG     path to log file
  -d DEV, --dev DEV     device name
```

## Requirements

- Python 3.3+

## Installation

Install
```
$ git clone https://github.com/hakavlad/diskio2log.git
$ cd diskio2log
$ sudo make install
```

Uninstall
```
$ sudo make uninstall
```

## Resources

- [Block layer statistics in /sys/block/<dev>/stat](https://github.com/torvalds/linux/blob/master/Documentation/block/stat.rst)
- [I/O statistics fields](https://github.com/torvalds/linux/blob/master/Documentation/admin-guide/iostats.rst)

