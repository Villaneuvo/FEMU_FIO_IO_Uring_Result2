# Write Plotting Result

For write Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=write
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
seq_write: (groupid=0, jobs=2): err= 0: pid=1296: Thu Apr 27 11:23:02 2023
  write: IOPS=7666, BW=3833MiB/s (4019MB/s)(225GiB/60003msec); 0 zone resets
    slat (usec): min=23, max=13648, avg=96.31, stdev=74.93
    clat (usec): min=1459, max=29826, avg=8250.02, stdev=2528.05
     lat (usec): min=1518, max=29916, avg=8346.74, stdev=2526.50
    clat percentiles (usec):
     |  1.00th=[ 2999],  5.00th=[ 3359], 10.00th=[ 3589], 20.00th=[ 7701],
     | 30.00th=[ 8094], 40.00th=[ 8455], 50.00th=[ 8586], 60.00th=[ 9372],
     | 70.00th=[ 9896], 80.00th=[10028], 90.00th=[10159], 95.00th=[10290],
     | 99.00th=[14877], 99.50th=[16057], 99.90th=[20317], 99.95th=[21627],
     | 99.99th=[25297]
   bw (  MiB/s): min= 2760, max= 4631, per=99.97%, avg=3831.96, stdev=242.92, samples=240
   iops        : min= 5520, max= 9262, avg=7663.78, stdev=485.85, samples=240
  lat (msec)   : 2=0.01%, 4=16.53%, 10=58.75%, 20=24.60%, 50=0.11%
  cpu          : usr=27.44%, sys=14.25%, ctx=22388, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,459992,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3833MiB/s (4019MB/s), 3833MiB/s-3833MiB/s (4019MB/s-4019MB/s), io=225GiB (241GB), run=60003-60003msec

Disk stats (read/write):
  nvme0n1: ios=99/458812, merge=0/0, ticks=4/3227694, in_queue=2345504, util=99.98%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682608004/Research/IOUring/NEW/BW/write/IOPS/write_512_2_2.eps_bgyamk.png" alt="writeBW-512k-n2-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682609446/Research/IOUring/NEW/BW/write/BW/write_512_2_2_ap9urk.jpg" alt="writeIOPS-512k-n2-t2" width="600"/>
<br><br>

## QD=4 (numjobs=4, thwrites=4)
```
seq_write: (groupid=0, jobs=4): err= 0: pid=1360: Thu Apr 27 11:29:11 2023
  write: IOPS=7891, BW=3946MiB/s (4137MB/s)(231GiB/60008msec); 0 zone resets
    slat (usec): min=23, max=14218, avg=94.10, stdev=84.83
    clat (usec): min=1948, max=40364, avg=16122.79, stdev=5793.06
     lat (usec): min=1996, max=40445, avg=16217.34, stdev=5791.07
    clat percentiles (usec):
     |  1.00th=[ 4228],  5.00th=[ 7570], 10.00th=[10290], 20.00th=[10945],
     | 30.00th=[11600], 40.00th=[13960], 50.00th=[14877], 60.00th=[16909],
     | 70.00th=[19268], 80.00th=[23200], 90.00th=[24773], 95.00th=[25297],
     | 99.00th=[26870], 99.50th=[28967], 99.90th=[33817], 99.95th=[35914],
     | 99.99th=[39060]
   bw (  MiB/s): min= 2329, max= 5432, per=99.96%, avg=3944.05, stdev=226.87, samples=480
   iops        : min= 4659, max=10864, avg=7887.79, stdev=453.72, samples=480
  lat (msec)   : 2=0.01%, 4=0.71%, 10=6.82%, 20=65.68%, 50=26.79%
  cpu          : usr=13.33%, sys=8.43%, ctx=21254, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,473555,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3946MiB/s (4137MB/s), 3946MiB/s-3946MiB/s (4137MB/s-4137MB/s), io=231GiB (248GB), run=60008-60008msec

Disk stats (read/write):
  nvme0n1: ios=51/472365, merge=0/0, ticks=2/6888860, in_queue=6034552, util=100.00%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682672518/Research/IOUring/NEW/BW/write/BW/write_512_4_4_ho2jlf.jpg" alt="writeBW-512k-n4-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682608004/Research/IOUring/NEW/BW/write/IOPS/write_512_4_4.eps_dwxfyu.png" alt="writeIOPS-512k-n4-t4" width="600"/>
<br><br>

## QD=8 (numjobs=8, thwrites=4)
```
seq_write: (groupid=0, jobs=8): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=1315: Thu Apr 27 11:25:53 2023
  write: IOPS=7886, BW=3943MiB/s (4135MB/s)(231GiB/60021msec); 0 zone resets
    slat (usec): min=24, max=13809, avg=100.57, stdev=96.43
    clat (usec): min=1579, max=80922, avg=32352.14, stdev=11580.54
     lat (usec): min=1629, max=81027, avg=32453.14, stdev=11583.01
    clat percentiles (usec):
     |  1.00th=[18744],  5.00th=[20317], 10.00th=[22152], 20.00th=[23462],
     | 30.00th=[24511], 40.00th=[26870], 50.00th=[27919], 60.00th=[28443],
     | 70.00th=[31327], 80.00th=[47973], 90.00th=[51643], 95.00th=[52691],
     | 99.00th=[58459], 99.50th=[60031], 99.90th=[71828], 99.95th=[73925],
     | 99.99th=[76022]
   bw (  MiB/s): min= 2078, max= 5230, per=99.99%, avg=3942.69, stdev=128.15, samples=957
   iops        : min= 4157, max=10460, avg=7884.58, stdev=256.32, samples=957
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.03%, 20=3.51%, 50=80.42%
  lat (msec)   : 100=16.02%
  cpu          : usr=6.78%, sys=4.21%, ctx=17083, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=99.9%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,473372,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3943MiB/s (4135MB/s), 3943MiB/s-3943MiB/s (4135MB/s-4135MB/s), io=231GiB (248GB), run=60021-60021msec

Disk stats (read/write):
  nvme0n1: ios=99/473340, merge=0/0, ticks=5/13819080, in_queue=12882860, util=99.74%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682609446/Research/IOUring/NEW/BW/write/BW/write_512_8_4_aqe7mc.jpg" alt="writeIOPS-512k-n8-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682608004/Research/IOUring/NEW/BW/write/IOPS/write_512_8_4.eps_fypdki.png" alt="writeBW-512k-n8-t4" width="600"/>
<br><br>

## QD=16 (numjobs=16, thwrites=2)
```
seq_write: (groupid=0, jobs=16): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=1393: Thu Apr 27 11:31:43 2023
  write: IOPS=7901, BW=3948MiB/s (4140MB/s)(231GiB/60019msec); 0 zone resets
    slat (usec): min=26, max=26818, avg=110.21, stdev=264.99
    clat (usec): min=152, max=133590, avg=64701.60, stdev=22828.47
     lat (usec): min=1814, max=133677, avg=64812.30, stdev=22822.40
    clat percentiles (msec):
     |  1.00th=[   42],  5.00th=[   45], 10.00th=[   47], 20.00th=[   48],
     | 30.00th=[   50], 40.00th=[   52], 50.00th=[   53], 60.00th=[   56],
     | 70.00th=[   62], 80.00th=[   99], 90.00th=[  102], 95.00th=[  104],
     | 99.00th=[  111], 99.50th=[  114], 99.90th=[  124], 99.95th=[  127],
     | 99.99th=[  131]
   bw (  MiB/s): min= 2119, max= 5476, per=99.94%, avg=3945.53, stdev=64.48, samples=1909
   iops        : min= 4235, max=10952, avg=7889.34, stdev=128.93, samples=1909
  lat (usec)   : 250=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.04%, 50=33.00%
  lat (msec)   : 100=54.08%, 250=12.81%
  cpu          : usr=3.45%, sys=2.16%, ctx=17599, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=99.9%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,474218,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3948MiB/s (4140MB/s), 3948MiB/s-3948MiB/s (4140MB/s-4140MB/s), io=231GiB (248GB), run=60019-60019msec

Disk stats (read/write):
  nvme0n1: ios=99/473957, merge=0/0, ticks=3/27439343, in_queue=26476056, util=99.78%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682609445/Research/IOUring/NEW/BW/write/BW/write_1m_16_2_ewfob2.jpg" alt="writeBW-512k-n16-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682608004/Research/IOUring/NEW/BW/write/IOPS/write_512_16_2.eps_vqy2uk.png" alt="writeIOPS-512k-n16-t2" width="600"/>
<br><br>

