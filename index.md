---
layout: home
---

FernIvy is a command-line tool for measuring energy consumption, with the same interface for both MacOS and Linux.

The following options are possible:

```
syntax: prototype [-h] [-l] [-s seconds_to_run | -c command_to_run]
            [-e] [-p] [-t] [-o output_file_name] [-f output_file_folder]
options:
c     Run for specified command.
      Put the entire command in quotation marks if it is longer than one word.
e     Print total energy consumption.
f     Set the folder in which to save the output file.
      If it does not exist, it will be created.
h     Print this Help.
l     Run in logging mode.
o     Set output file. The path to the file has to exist. Cannot be "temp".
p     Print average power.
s     Run for specified amount of seconds.
t     Print total execution time.
```

## Installation

Please follow the installation guide for your operating system, since FernIvy depends on different libraries for each of them.

### MacOS

### Linux

## License

This work is open sourced under the Apache License, Version 2.0.

Copyright 2022 FernIvy

This site uses <a href="https://github.com/sighingnow/jekyll-gitbook" target="_blank">GitBook</a>, a documentation theme for Jekyll. 

[gitbook]: https://github.com/sighingnow/jekyll-gitbook
