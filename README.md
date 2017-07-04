It is used for generating load graphs of benchmark, e.g. database benchmark.

Currently supported:

- CPU load lines graph
- Disk load lines graph

# Usage

Before using it, you should make sure of that `gunplot` is installed.

1. collect load information of CPU and disk

    use command `sar` like this: `sar -ud 1 > stats_file`

    the output looks like following:
    ```
    Linux 3.10.0-327.el7.x86_64 (xxx.xxx.xxx.xxx)      07/04/2017      _x86_64_        (48 CPU)

    05:47:57 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
    05:47:58 PM     all      0.35      0.00      0.25      0.00      0.00     99.39

    05:47:57 PM       DEV       tps  rd_sec/s  wr_sec/s  avgrq-sz  avgqu-sz     await     svctm     %util
    05:47:58 PM    dev8-0      2.00      0.00     24.00     12.00      0.00      0.00      0.00      0.00
    05:47:58 PM   dev8-16      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00

    05:47:58 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
    05:47:59 PM     all      0.31      0.00      0.17      0.00      0.00     99.52

    05:47:58 PM       DEV       tps  rd_sec/s  wr_sec/s  avgrq-sz  avgqu-sz     await     svctm     %util
    05:47:59 PM    dev8-0      2.00      0.00     24.00     12.00      0.00      0.00      0.00      0.00
    05:47:59 PM   dev8-16      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00

    05:47:59 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
    05:48:00 PM     all      0.17      0.00      0.06      0.00      0.00     99.77

    05:47:59 PM       DEV       tps  rd_sec/s  wr_sec/s  avgrq-sz  avgqu-sz     await     svctm     %util
    05:48:00 PM    dev8-0      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
    05:48:00 PM   dev8-16      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
    ```

2. run benchmark

3. stop load collection

4. generate graphs

    ```
    # cd benchmark-graph-generator
    # ./bin/graph_gen -n mongodb -f stats_file -d dev8-16

    ```
    
    Usage of `graph_gen` as follows:
    ```
    # ./bin/graph_gen -h
    Usage: ./bin/graph_gen -n NAME -f SRCFILE -d DEVID [-o OUTDIR] [-h]
    Options:
      -n=NAME    name of current benchmark
      -f=SRCFILE source file that cantains system/benchmark statistics data
      -d=DEVID   device id of disk
      -o=OUTDIR  optional output directory, default is ./result
      -h         help information
    ```
