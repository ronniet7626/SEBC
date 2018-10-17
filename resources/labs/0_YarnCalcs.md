Inspect the derived/default values. Adjust as necessary.
For example, if memory for the OS is too high or low, adjust the cell formula.
================================================================================


No inital adjustment as OS memory allocation is 10% of total memory

What criteria affects workload factor? What does a value of 1, 2, or 4 signify?
=================================================================================

Minimunm values for:

mapreduce.map.memory.mb
and
mapreduce.map.cpu.vcores

affect the workload factor.

A lower workload factor reduces the amount of map reduce map and reduce jobs that can be run

-D mapreduce.job.maps
-D mapreduce.job.maps

