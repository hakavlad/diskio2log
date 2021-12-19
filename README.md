
# diskio2log

[![Total alerts](https://img.shields.io/lgtm/alerts/g/hakavlad/diskio2log.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/hakavlad/diskio2log/alerts/)

Monitor and log some current I/O metrics for selected block device.

## Options

```
$ diskio2log -h
usage: diskio2log [-h] [-d DEV] [-i INTERVAL] [-m MODE] [-l LOG]

optional arguments:
  -h, --help            show this help message and exit
  -d DEV, --dev DEV     device name
  -i INTERVAL, --interval INTERVAL
                        interval in sec
  -m MODE, --mode MODE  mode (1, 2, 3 or 4); default: 1
  -l LOG, --log LOG     path to log file
```

# Usage

Run the script at least with `-d` option.

Output example:
```
$ diskio2log --dev sdb --interval 10
Starting diskio2log, block device: sdb, interval: 10.0s, mode: 1
Process memory locked with MCL_CURRENT | MCL_FUTURE | MCL_ONFAULT
--
R 0.0 MiB/s, await 0% | W 0.6 MiB/s, await 3% | util 0.9%
R 0.0 MiB/s, await 0% | W 0.6 MiB/s, await 4% | util 1.0%
R 0.0 MiB/s, await 0% | W 0.0 MiB/s, await 0% | util 0.1%
R 0.1 MiB/s, await 11% | W 0.6 MiB/s, await 6% | util 5.5%
R 5.5 MiB/s, await 472% | W 0.0 MiB/s, await 1% | util 75.2%
R 3.8 MiB/s, await 322% | W 0.0 MiB/s, await 3% | util 97.0%
R 5.0 MiB/s, await 320% | W 0.0 MiB/s, await 0% | util 87.3%
R 2.4 MiB/s, await 155% | W 0.0 MiB/s, await 0% | util 33.5%
R 3.1 MiB/s, await 102% | W 0.0 MiB/s, await 1% | util 39.1%
R 13.8 MiB/s, await 2253% | W 0.0 MiB/s, await 9% | util 99.0%
R 6.2 MiB/s, await 390% | W 0.0 MiB/s, await 1% | util 76.0%
^C--
I/O statistics for sdb in the last 113.2s:
  Read:
    404.9 MiB (avg 3.6 MiB/s)
    9063 requests processed (avg 80.0 rp/s)
    1748 requests merged with in-queue I/O (avg 15.4 rm/s)
    await 407.5s (avg 359.9%)
  Write:
    19.3 MiB (avg 0.2 MiB/s)
    210 requests processed (avg 1.9 rp/s)
    60 requests merged with in-queue I/O (avg 0.5 rm/s)
    await 2.9s (avg 2.6%)
  Utilization: 52.7s (avg 46.5%)
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

- [Block layer statistics in /sys/block/\<dev\>/stat](https://github.com/torvalds/linux/blob/master/Documentation/block/stat.rst)
- [I/O statistics fields](https://github.com/torvalds/linux/blob/master/Documentation/admin-guide/iostats.rst)

