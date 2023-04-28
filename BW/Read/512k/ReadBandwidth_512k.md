# Read Plotting Result

For Read Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=read
runtime=60
direct=1 
bs=512k
iodepth=32
numjobs=n(starting from 2,4,8,16)
threads=n(starting from 2,4)
time_based=1
thread
group_reporting
norandommap=1
randrepeat=0
size=1G

[nvme]
filename=/dev/nvme0n1 
```

# Result

# Blocksize 512k
## QD=2 (numjobs=2, threads=2)
```
seq_read: (groupid=0, jobs=2): err= 0: pid=2437: Thu Apr 27 09:46:17 2023
  read: IOPS=8834, BW=4417MiB/s (4632MB/s)(259GiB/60004msec)
    slat (usec): min=12, max=22809, avg=52.98, stdev=81.90
    clat (usec): min=1058, max=32463, avg=7187.19, stdev=2518.55
     lat (usec): min=1109, max=34208, avg=7240.57, stdev=2518.45
    clat percentiles (usec):
     |  1.00th=[ 1958],  5.00th=[ 3032], 10.00th=[ 3589], 20.00th=[ 4228],
     | 30.00th=[ 6128], 40.00th=[ 6849], 50.00th=[ 7767], 60.00th=[ 8160],
     | 70.00th=[ 8717], 80.00th=[ 9110], 90.00th=[ 9372], 95.00th=[ 9503],
     | 99.00th=[14877], 99.50th=[15926], 99.90th=[20317], 99.95th=[21365],
     | 99.99th=[26870]
   bw (  MiB/s): min= 2434, max= 5750, per=99.98%, avg=4416.45, stdev=475.76, samples=240
   iops        : min= 4868, max=11500, avg=8832.83, stdev=951.53, samples=240
  lat (msec)   : 2=1.06%, 4=18.08%, 10=77.33%, 20=3.42%, 50=0.11%
  cpu          : usr=2.64%, sys=27.51%, ctx=26047, majf=0, minf=8192
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=530090,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4417MiB/s (4632MB/s), 4417MiB/s-4417MiB/s (4632MB/s-4632MB/s), io=259GiB (278GB), run=60004-60004msec

Disk stats (read/write):
  nvme0n1: ios=537738/0, merge=0/0, ticks=3426048/0, in_queue=2433832, util=99.91%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607542/Research/IOUring/NEW/BW/read/BW/read_512_2_2.eps_jmqcyu.png" alt="ReadBW-512-n2-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607569/Research/IOUring/NEW/BW/read/IOPS/read_512_2_2_webhcb.jpg" alt="ReadIOPS-512-n2-t2" width="600"/>
<br><br>

## QD=4 (numjobs=4, threads=4)
```
seq_read: (groupid=0, jobs=4): err= 0: pid=2627: Thu Apr 27 10:15:14 2023
  read: IOPS=8567, BW=4284MiB/s (4492MB/s)(251GiB/60015msec)
    slat (usec): min=17, max=14254, avg=54.64, stdev=103.06
    clat (usec): min=1066, max=48381, avg=14875.13, stdev=5646.11
     lat (usec): min=1156, max=50556, avg=14930.15, stdev=5646.09
    clat percentiles (usec):
     |  1.00th=[ 6325],  5.00th=[10028], 10.00th=[10552], 20.00th=[10683],
     | 30.00th=[10814], 40.00th=[10945], 50.00th=[11076], 60.00th=[13304],
     | 70.00th=[20317], 80.00th=[21365], 90.00th=[22152], 95.00th=[22676],
     | 99.00th=[30540], 99.50th=[34341], 99.90th=[38536], 99.95th=[40109],
     | 99.99th=[44303]
   bw (  MiB/s): min= 2048, max= 6080, per=99.98%, avg=4283.16, stdev=306.85, samples=480
   iops        : min= 4096, max=12160, avg=8566.22, stdev=613.71, samples=480
  lat (msec)   : 2=0.05%, 4=0.04%, 10=5.08%, 20=64.04%, 50=30.79%
  cpu          : usr=1.16%, sys=14.02%, ctx=18039, majf=0, minf=16384
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=514199,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4284MiB/s (4492MB/s), 4284MiB/s-4284MiB/s (4492MB/s-4492MB/s), io=251GiB (270GB), run=60015-60015msec

Disk stats (read/write):
  nvme0n1: ios=513050/0, merge=0/0, ticks=7056126/0, in_queue=6213956, util=100.00%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607542/Research/IOUring/NEW/BW/read/BW/read_512_4_4.eps_ys1efp.png" alt="ReadBW-512-n4-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607569/Research/IOUring/NEW/BW/read/IOPS/read_512_4_4.eps_yq1nhi.png" alt="ReadIOPS-512-n4-t4" width="600"/>
<br><br>

## QD=8 (numjobs=8, threads=4)
```
seq_read: (groupid=0, jobs=8): err= 0: pid=2562: Thu Apr 27 10:03:41 2023
  read: IOPS=8451, BW=4226MiB/s (4431MB/s)(248GiB/60012msec)
    slat (usec): min=14, max=23241, avg=56.81, stdev=101.52
    clat (usec): min=889, max=79230, avg=30214.45, stdev=10809.60
     lat (usec): min=1759, max=79282, avg=30271.62, stdev=10809.35
    clat percentiles (usec):
     |  1.00th=[18744],  5.00th=[19792], 10.00th=[20317], 20.00th=[21890],
     | 30.00th=[22414], 40.00th=[23987], 50.00th=[25560], 60.00th=[26608],
     | 70.00th=[32113], 80.00th=[44827], 90.00th=[47973], 95.00th=[49021],
     | 99.00th=[53740], 99.50th=[57934], 99.90th=[63701], 99.95th=[67634],
     | 99.99th=[79168]
   bw (  MiB/s): min= 2388, max= 5918, per=99.97%, avg=4224.41, stdev=121.96, samples=957
   iops        : min= 4776, max=11836, avg=8448.12, stdev=243.94, samples=957
  lat (usec)   : 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.03%, 10=0.03%, 20=6.94%, 50=91.07%
  lat (msec)   : 100=1.92%
  cpu          : usr=0.51%, sys=6.77%, ctx=17606, majf=0, minf=32768
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=507181,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4226MiB/s (4431MB/s), 4226MiB/s-4226MiB/s (4431MB/s-4431MB/s), io=248GiB (266GB), run=60012-60012msec

Disk stats (read/write):
  nvme0n1: ios=505561/0, merge=0/0, ticks=14282916/0, in_queue=13327216, util=99.86%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607542/Research/IOUring/NEW/BW/read/BW/read_512_8_4.eps_iql729.png" alt="ReadBW-512-n8-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607569/Research/IOUring/NEW/BW/read/IOPS/read_512_8_4.eps_ql4apc.png" alt="ReadIOPS-512-n8-t4" width="600"/>
<br><br>

## QD=16 (numjobs=16, threads=2)
```
seq_read: (groupid=0, jobs=16): err= 0: pid=2527: Thu Apr 27 09:57:37 2023
  read: IOPS=8576, BW=4288MiB/s (4497MB/s)(251GiB/60039msec)
    slat (usec): min=13, max=39392, avg=67.19, stdev=246.29
    clat (usec): min=1017, max=147577, avg=59537.68, stdev=20986.99
     lat (usec): min=1864, max=150471, avg=59605.27, stdev=20987.37
    clat percentiles (msec):
     |  1.00th=[   42],  5.00th=[   44], 10.00th=[   45], 20.00th=[   46],
     | 30.00th=[   47], 40.00th=[   48], 50.00th=[   48], 60.00th=[   51],
     | 70.00th=[   54], 80.00th=[   92], 90.00th=[   95], 95.00th=[   97],
     | 99.00th=[  107], 99.50th=[  112], 99.90th=[  124], 99.95th=[  128],
     | 99.99th=[  144]
   bw (  MiB/s): min= 2206, max= 5664, per=99.89%, avg=4283.81, stdev=71.63, samples=1916
   iops        : min= 4410, max=11328, avg=8566.14, stdev=143.24, samples=1916
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.02%, 20=0.04%, 50=59.48%
  lat (msec)   : 100=37.43%, 250=3.03%
  cpu          : usr=0.28%, sys=3.80%, ctx=17905, majf=0, minf=65536
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=99.9%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=514935,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4288MiB/s (4497MB/s), 4288MiB/s-4288MiB/s (4497MB/s-4497MB/s), io=251GiB (270GB), run=60039-60039msec

Disk stats (read/write):
  nvme0n1: ios=512983/0, merge=0/0, ticks=27921432/0, in_queue=26862388, util=99.88%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607542/Research/IOUring/NEW/BW/read/BW/read_512_16_2.eps_ytmlvi.png" alt="ReadBW-512-n16-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607569/Research/IOUring/NEW/BW/read/IOPS/read_512_16_2.eps_iajhqz.png" alt="ReadIOPS-512-n16-t2" width="600"/>
<br><br>

