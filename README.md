
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

# Usage

Run the script at least with `-d` option.

Output example:
```
$ diskio2log --dev sdb --interval 10
Starting diskio2log, block device: sdb, interval: 10.0s
Process memory locked with MCL_CURRENT | MCL_FUTURE | MCL_ONFAULT
--
R 0.0M/s, 0r/s, await 5% | W 0.3M/s, 8r/s, await 10% | in_fl 0r
R 11.2M/s, 159r/s, await 2768% | W 0.1M/s, 3r/s, await 18% | in_fl 14r
R 4.7M/s, 69r/s, await 509% | W 0.0M/s, 2r/s, await 4% | in_fl 0r
^C--
In the last 34.4s:
R: 166.8MiB, 2439 requests, await 333.0s (avg 4.8M/s, 70.8r/s, 967.0%)
W: 3.7MiB, 129 requests, await 3.2s (avg 0.1M/s, 3.7r/s, 9.3%)
```

## Requirements

- Linux kernel with `/proc/diskstats` available
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

