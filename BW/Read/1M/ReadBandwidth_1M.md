# Read Plotting Result

For Read Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=read
runtime=60
direct=1 
bs=1M
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

# Blocksize 1M
## QD=2 (numjobs=2, threads=2)
```
seq_read: (groupid=0, jobs=2): err= 0: pid=2640: Thu Apr 27 10:20:04 2023
  read: IOPS=4348, BW=4348MiB/s (4559MB/s)(255GiB/60006msec)
    slat (usec): min=31, max=23749, avg=88.24, stdev=78.69
    clat (usec): min=1327, max=48933, avg=14620.41, stdev=5267.69
     lat (usec): min=1427, max=51038, avg=14709.06, stdev=5269.65
    clat percentiles (usec):
     |  1.00th=[ 4752],  5.00th=[ 7504], 10.00th=[ 8979], 20.00th=[ 9372],
     | 30.00th=[10814], 40.00th=[11731], 50.00th=[12780], 60.00th=[17433],
     | 70.00th=[18482], 80.00th=[20317], 90.00th=[20579], 95.00th=[21103],
     | 99.00th=[27395], 99.50th=[30802], 99.90th=[39584], 99.95th=[41157],
     | 99.99th=[47973]
   bw (  MiB/s): min= 2305, max= 5950, per=99.98%, avg=4347.21, stdev=499.79, samples=240
   iops        : min= 2305, max= 5950, avg=4347.16, stdev=499.81, samples=240
  lat (msec)   : 2=0.01%, 4=0.08%, 10=23.00%, 20=52.29%, 50=24.63%
  cpu          : usr=1.24%, sys=22.79%, ctx=12140, majf=0, minf=16384
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=260921,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4348MiB/s (4559MB/s), 4348MiB/s-4348MiB/s (4559MB/s-4559MB/s), io=255GiB (274GB), run=60006-60006msec

Disk stats (read/write):
  nvme0n1: ios=260569/0, merge=0/0, ticks=3454489/0, in_queue=2906576, util=99.95%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607541/Research/IOUring/NEW/BW/read/BW/read_1M_2_2.eps_v6un3b.png" alt="ReadBW-1M-n2-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607568/Research/IOUring/NEW/BW/read/IOPS/read_1M_2_2.eps_v2qmk8.png" alt="ReadIOPS-1M-n2-t2" width="600"/>
<br><br>

## QD=4 (numjobs=4, threads=4)
```
seq_read: (groupid=0, jobs=4): err= 0: pid=2655: Thu Apr 27 10:25:12 2023
  read: IOPS=4286, BW=4286MiB/s (4494MB/s)(251GiB/60018msec)
    slat (usec): min=24, max=24975, avg=88.38, stdev=95.39
    clat (usec): min=1193, max=78842, avg=29752.71, stdev=10751.53
     lat (usec): min=2166, max=78924, avg=29841.48, stdev=10750.46
    clat percentiles (usec):
     |  1.00th=[18482],  5.00th=[20579], 10.00th=[21627], 20.00th=[21890],
     | 30.00th=[21890], 40.00th=[22152], 50.00th=[22152], 60.00th=[27132],
     | 70.00th=[42730], 80.00th=[43779], 90.00th=[44303], 95.00th=[46924],
     | 99.00th=[51119], 99.50th=[57410], 99.90th=[69731], 99.95th=[72877],
     | 99.99th=[79168]
   bw (  MiB/s): min= 2342, max= 5888, per=99.95%, avg=4283.81, stdev=309.35, samples=480
   iops        : min= 2342, max= 5888, avg=4283.63, stdev=309.37, samples=480
  lat (msec)   : 2=0.01%, 4=0.06%, 10=0.13%, 20=4.24%, 50=93.46%
  lat (msec)   : 100=2.09%
  cpu          : usr=0.56%, sys=11.22%, ctx=9075, majf=0, minf=32768
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=257241,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4286MiB/s (4494MB/s), 4286MiB/s-4286MiB/s (4494MB/s-4494MB/s), io=251GiB (270GB), run=60018-60018msec

Disk stats (read/write):
  nvme0n1: ios=258219/0, merge=0/0, ticks=7252215/0, in_queue=6751020, util=99.93%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607541/Research/IOUring/NEW/BW/read/BW/read_1M_4_4.eps_jdravr.png" alt="ReadBW-1M-n4-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607568/Research/IOUring/NEW/BW/read/IOPS/read_1m_4_4_dbd0vx.png" alt="ReadIOPS-1M-n4-t4" width="600"/>
<br><br>

## QD=8 (numjobs=8, threads=4)
```
seq_read: (groupid=0, jobs=8): err= 0: pid=2666: Thu Apr 27 10:31:04 2023
  read: IOPS=4285, BW=4285MiB/s (4493MB/s)(251GiB/60060msec)
    slat (usec): min=25, max=17186, avg=95.80, stdev=168.02
    clat (usec): min=1278, max=141282, avg=59551.59, stdev=21377.41
     lat (usec): min=1472, max=141368, avg=59647.76, stdev=21375.41
    clat percentiles (msec):
     |  1.00th=[   40],  5.00th=[   42], 10.00th=[   43], 20.00th=[   44],
     | 30.00th=[   44], 40.00th=[   47], 50.00th=[   51], 60.00th=[   52],
     | 70.00th=[   58], 80.00th=[   88], 90.00th=[   95], 95.00th=[   96],
     | 99.00th=[  112], 99.50th=[  116], 99.90th=[  133], 99.95th=[  134],
     | 99.99th=[  142]
   bw (  MiB/s): min= 2223, max= 5632, per=99.97%, avg=4283.62, stdev=119.53, samples=960
   iops        : min= 2223, max= 5632, avg=4282.86, stdev=119.51, samples=960
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.02%, 20=0.03%, 50=48.16%
  lat (msec)   : 100=48.34%, 250=3.44%
  cpu          : usr=0.27%, sys=5.61%, ctx=9220, majf=0, minf=65536
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=99.9%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=257363,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4285MiB/s (4493MB/s), 4285MiB/s-4285MiB/s (4493MB/s-4493MB/s), io=251GiB (270GB), run=60060-60060msec

Disk stats (read/write):
  nvme0n1: ios=258381/0, merge=0/0, ticks=14583334/0, in_queue=14089772, util
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607541/Research/IOUring/NEW/BW/read/BW/read_1m_8_4.eps_arjla6.png" alt="ReadIOPS-1M-n8-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607568/Research/IOUring/NEW/BW/read/IOPS/read_1m_8_4.eps_lw3ylo.png" alt="ReadBW-1M-n8-t4" width="600"/>
<br><br>

## QD=16 (numjobs=16, threads=2)
```
seq_read: (groupid=0, jobs=16): err= 0: pid=2679: Thu Apr 27 10:36:38 2023
  read: IOPS=4325, BW=4326MiB/s (4536MB/s)(254GiB/60117msec)
    slat (usec): min=25, max=44277, avg=112.65, stdev=479.34
    clat (usec): min=1235, max=277984, avg=117883.50, stdev=41603.50
     lat (usec): min=1346, max=278114, avg=117996.59, stdev=41602.93
    clat percentiles (msec):
     |  1.00th=[   81],  5.00th=[   87], 10.00th=[   90], 20.00th=[   92],
     | 30.00th=[   93], 40.00th=[   94], 50.00th=[   96], 60.00th=[  100],
     | 70.00th=[  106], 80.00th=[  182], 90.00th=[  190], 95.00th=[  194],
     | 99.00th=[  218], 99.50th=[  230], 99.90th=[  268], 99.95th=[  275],
     | 99.99th=[  279]
   bw (  MiB/s): min= 1964, max= 6144, per=99.91%, avg=4321.69, stdev=81.64, samples=1918
   iops        : min= 1957, max= 6144, avg=4320.43, stdev=81.67, samples=1918
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.02%, 50=0.12%
  lat (msec)   : 100=62.78%, 250=36.89%, 500=0.19%
  cpu          : usr=0.12%, sys=2.85%, ctx=9535, majf=0, minf=131072
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=99.8%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=260041,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4326MiB/s (4536MB/s), 4326MiB/s-4326MiB/s (4536MB/s-4536MB/s), io=254GiB (273GB), run=60117-60117msec

Disk stats (read/write):
  nvme0n1: ios=260364/0, merge=0/0, ticks=28835758/0, in_queue=28322492, util=99.90%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607541/Research/IOUring/NEW/BW/read/BW/read_1m_16_2.eps_ngkaq8.png" alt="ReadBW-1M-n16-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607568/Research/IOUring/NEW/BW/read/IOPS/read_1m_16_2.eps_n5zd5o.png" alt="ReadIOPS-1M-n16-t2" width="600"/>
<br><br>

