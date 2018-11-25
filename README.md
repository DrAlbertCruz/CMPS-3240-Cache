# CMPS-3240-Cache

Lab 10 - Caches

## Requirements

This lab *must* be completed on the department's `odin.cs.csubak.edu`. It is only guaranteed to work this way. If you try to get it to work on your own local machine (linux, mac, win) you are on your own.

## Objectives

* Implement code that reduces the effectiveness of the cache.
* Collect experimental results to investigate the performance of the cache.

## Required files

As a necessary first step, clone this repository:

```shell
$ https://github.com/DrAlbertCruz/CMPS-3240-Cache.git
...
$ cd CMPS-3240-Cache
```
To compile all of the programs for this lab, give the command:

```shell
$ make all
```

# Approach

## Part 1 - Cache info

The `cache_info.out` program prints out information about the cache on the current system. On Linux systems, this information can also be found in the /sys subsystem in the directories:

/sys/devices/system/cpu/cpu*/cache/index*/

Run the code with the command:

./cache_info

Program 2 - cache_off

This program defeats the L2 cache on Sleipnir to give really poor memory bandwidth (e.g. poor performance).

Run the program with:

./cache_off

Note the poor performance, as this might be useful when evaluating the next program, which is the bulk of this lab.
Program 3 - cache

This program allocates a very large array and then accesses indexes using a skip amount specified on standard in to the program. For example, if you specify a skip amount of 127, it will access j, then j+127, and so on. For this portion of the lab, we will investigate the effects of giving different skip values (the line_offset variable in the program).

To run this program, you will give the following shell command:

while true; do echo "127" | ./cache | grep Bandwidth; sleep 10; done

where 127 is the skip value. Let this loop run for about a dozen iterations before hitting CTRL-C, so that you can gather an observed average (removing any outliers that may have been caused by other running programs). The results of the last iteration will be stored in the logfile cache_<skipValue>.log.

Use the following skip values when running the program (note that these are pairs of similar numbers where the second number is a power of 2 and the first number is a prime close to the second number):

127 128 251 256 509 512 1021 1024 2039 2048 4093 4096

Lab Writeup

Create a table of the number of runs, and the maximum, minimum, average, and standard deviation for the memory bandwidth in each of the runs of the cache program that was requested above.

Note any trends between the pairs of values (e.g. between 127 and 128 or between 1021 and 1024) you saw when compiling this table. Try to explain these trends.

Upload your writeup to Moodle.

M. Danforth, revised by A. Cruz 8/17