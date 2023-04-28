# FEMU - FIO IOUring Result 2
This repository will show the result of the new configuration that felt suitable with the hardware spesification of the computer. As far this benchmarking running on Ubuntu 20.04 focal fosa with kernel linux 5.4.0 FIO Version 3.1.6 and FEMU on run-nossd.sh configuration. For the hardware spesification it use Intel Xeon Silver 4114 with 10 cores and 20 threads with 64GB RAM. This Result will show both of IOPS and Bandwidth result for each benchmarking that have been tested out.

In conclusion, the results of this benchmarking result in an IOPS that can touch figures of up to> 500KIOPS with an average value of 300KIOPS, this is when compared to the previous benchmarking results. Then as for bandwidth testing the results of benchmarking are only able to touch the maximum number at 5600 MiB/s with an average value of around > 4000 MiB/s.

For the result of benchmarking i've been made a seperate folder for write and read bandwidth result also a quick access for IOPS result, to make it easy to understand the result, here for quick access :
## Bandwidth :
### Read
Read with 128k blocksize - [Here](https://github.com/Villaneuvo/FEMU_FIO_IO_Uring_Result2/blob/main/BW/Read/128k/ReadBandwidth_128k.md) <br>
Read with 512k blocksize - [Here](https://github.com/Villaneuvo/FEMU_FIO_IO_Uring_Result2/blob/main/BW/Read/512k/ReadBandwidth_512k.md) <br>
Read with 1M blocksize - [Here](https://github.com/Villaneuvo/FEMU_FIO_IO_Uring_Result2/blob/main/BW/Read/1M/ReadBandwidth_1M.md) <br>
### Write
Write with 128k blocksize - [Here](https://github.com/Villaneuvo/FEMU_FIO_IO_Uring_Result2/blob/main/BW/Write/128k/WriteBandwidth_128k.md) <br>
Write with 512k blocksize - [Here](https://github.com/Villaneuvo/FEMU_FIO_IO_Uring_Result2/blob/main/BW/Write/512k/WriteBandwidth_512k.md) <br>
Write with 1M blocksize - [Here](https://github.com/Villaneuvo/FEMU_FIO_IO_Uring_Result2/blob/main/BW/Write/1M/WriteBandwidth_1M.md) <br>

## IOPS :
### Read - [Here](https://github.com/Villaneuvo/FEMU_FIO_IO_Uring_Result2/blob/main/IOPS/Read/README.md)

### Write - [Here](https://github.com/Villaneuvo/FEMU_FIO_IO_Uring_Result2/blob/main/IOPS/Write/README.md)

