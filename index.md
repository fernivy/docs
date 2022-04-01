---
layout: home
---

FernIvy is a command-line tool for measuring energy consumption, with the same interface for both MacOS and Linux. The following configurations are possible:

```txt
syntax:
    fernivy [-h] [-l]
            [-s seconds_to_run | -c command_to_run]
            [-r number_of_runs] [-b seconds_between_runs]
            [-e] [-p] [-t]
            [-o output_file_name] [-f output_file_folder]
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

```txt
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

## Releases:

* <a href="https://github.com/fernivy/fernivy/releases/tag/v1.2.0" target="blank">v1.2.0</a>
    * Generation of packages both for installing from source (both OS) and using .deb binary (Linux) or homebrew (MacOS)
    * Up-to-date documentation (README, CONTRIBUTING, CHANGELOG)
    * Simplified generator
* <a href="https://github.com/fernivy/fernivy/releases/tag/v1.1.0" target="blank">v1.1.0</a>
    * Sudo access requested outside of script
    * Temporary files using `mktemp`
* <a href="https://github.com/fernivy/fernivy/releases/tag/v1.0.1-macos" target="blank">v1.0.1 for MacOS</a>
* <a href="https://github.com/fernivy/fernivy/releases/tag/v1.0.0" target="blank">v1.0.0</a>
    * Uniform data output for all supported tools
    * Command Mode vs Timed Mode
    * Varying number of runs + customisable sleep time
    * Averages over runs
    * Output file and output folder specification
    * Logging mode

For more information, you can check the <a href="https://github.com/fernivy/fernivy/releases" target="blank">overview of GitHub releases</a> and the <a href="https://github.com/fernivy/fernivy/blob/main/CHANGELOG.md" target="blank">`CHANGELOG.md`</a>.


## Installation

Please follow the installation guide for your operating system, since FernIvy depends on different libraries for each of them.

### MacOS

FernIvy has two dependencies when running on MacOS: PowerLog (the command line interface from Intel Power Gadget for energy consumption measurement) and Python 3 (for data processing). PowerLog can be installed with Intel Power Gadget according to these <a href="https://www.intel.com/content/www/us/en/developer/articles/tool/power-gadget.html" target="blank">installation instructions</a>. Installation instructions for Python 3 can be found for example <a href="https://docs.python-guide.org/starting/install3/osx/" target="blank">here</a>.

For `fernivy` to run properly, it is important to know the location where PowerLog was installed. This is usually within the `Applications` folder at `/Applications/Intel\ Power\ Gadget/PowerLog`. If that is the case, you can move on to the next step. However, if you installed PowerLog somewhere else, it is important to define an environment variable called `FERNIVY_POWERLOG_PATH` to inform `fernivy` where to look for it. This is done either by calling

```bash
export FERNIVY_POWERLOG_PATH=<path>
```

or by adding this line to your bash profile (usually `$HOME/.bashrc` or `$HOME/.zshrc`).

Now that all the dependencies are installed, `fernivy` can be installed using <a href="https://brew.sh" target="blank">Homebrew</a> with

```bash
brew tap fernivy/fernivy && brew install fernivy
```

### Linux (Debian / Ubuntu)

Go to the <a href="https://github.com/fernivy/fernivy/releases/latest" target="blank">latest release on GitHub</a> and download and depackage the `.deb` binary.

FernIvy has two dependencies when running on Linux: `linux-perf` (for measurement) and `python3` (for data processing). They are listed as dependencies in the `.deb` files, so running the following command after the depackaging should fix if they are missing:

```bash
sudo apt --fix-broken install
```

You can also choose to install them using the <a href="https://docs.python-guide.org/starting/install3/linux/" target="_blank">Installing Python 3 on Linux</a> guide and the following command:

```bash
sudo apt install linux-perf
```

**NOTE:** For Perf specifically, you need to run the tool using `sudo`, since Perf requires root access.

### Installing from source

It is also possible to download the `.zip` or `.tar.gz` file directly from the <a href="https://github.com/fernivy/fernivy/releases/latest" target="blank">latest release on GitHub</a>.

This can be done both for MacOS and Linux, but the dependency on Python 3 and PowerLog/`perf` remains the same. After downloading and unpacking the source, one can generate the necessary scripts using `make generate`. The correct scripts for running `fernivy` from source can then be found in either `powerlog/package` or `perf/package`.

Note that with this installation, it is necessary to call `fernivy` from the `package` folder with the following command:

```bash
./fernivy [options]
```

## License

This work is open sourced under the Apache License, Version 2.0.

Copyright 2022 FernIvy

This site uses <a href="https://github.com/sighingnow/jekyll-gitbook" target="_blank">GitBook</a>, a documentation theme for Jekyll.

[gitbook]: https://github.com/sighingnow/jekyll-gitbook
