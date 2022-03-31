---
layout: home
---

FernIvy is a command-line tool for measuring energy consumption, with the same interface for both MacOS and Linux.

The following configurations are possible:

```
syntax:
    fernivy [-h] [-l]
            [-s seconds_to_run | -c command_to_run]
            [-r number_of_runs] [-b seconds_between_runs]
            [-e] [-p] [-t]
            [-o output_file_name | -f output_file_folder]
options:
b     Set the number of second to pause between runs.
c     Run for specified command.
      Put the entire command in quotation marks if it is longer than one word.
e     Print total energy consumption.
f     Set the folder in which to save the output file.
      If it does not exist, it will be created.
h     Print this Help.
l     Run in logging mode.
o     Set output file.
      The path to the file has to exist.
      It cannot start with "temp".
p     Print average power.
r     Set the number of times to run.
s     Run for specified number of seconds.
t     Print total execution time.
```

### Example

The following command will:
* run the experiment 5 times,
* each time measure for 2 seconds,
* take a 1 second break in between,
* print the average
    * power,
    * energy consumed,
    * time elapsed,
* and save the result in "result.csv".

```bash
fernivy -s 1 -r 5 -b 1 -p -e -t -o result
```

You will get the following output on your console:

```
|#####| 5/5

Average total energy consumption: 31.290000000000003 J
Average power: 31.24840119389636 W
Average total time elapsed: 1.0013329858 s

Results exported to: result.csv
```

The `result.csv` file will have the following data:

```csv
index,timestamp,total_energy_consumption,average_power,time_elapsed
0,Thu Mar 31 08:51:49 2022,30.42,30.37519801056872,1.001474953
1,Thu Mar 31 08:51:51 2022,34.1,34.05739069632765,1.001251103
2,Thu Mar 31 08:51:53 2022,30.77,30.730595632289305,1.001282252
3,Thu Mar 31 08:51:56 2022,31.03,30.98722257305901,1.001380486
4,Thu Mar 31 08:51:58 2022,30.13,30.091599057237094,1.001276135
,,,,
avg,,31.290000000000003,31.24840119389636,1.0013329858
```
## Installation

Please follow the installation guide for your operating system, since FernIvy depends on different libraries for each of them.

### MacOS

### Linux (Debian / Ubuntu)

You first need to install the following dependencies:

* `python3`: you can follow [this](https://docs.python-guide.org/starting/install3/linux/) guide.
* `perf`:

```bash
sudo apt install linux-perf
```

Download [this](https://www.flaticon.com/free-icon/work-in-progress_5578703) `.deb` package and run the following command to install it:

```bash
sudo dpkg -i fernivy_1.0.0_all.deb
alias fernivy="fernivy.sh"
```

## License

This work is open sourced under the Apache License, Version 2.0.

Copyright 2022 FernIvy

This site uses <a href="https://github.com/sighingnow/jekyll-gitbook" target="_blank">GitBook</a>, a documentation theme for Jekyll. 

[gitbook]: https://github.com/sighingnow/jekyll-gitbook
