# Write Plotting Result

For write Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=write
runtime=60
direct=1 
bs=128k
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

# Blocksize 128k
## QD=2 (numjobs=2, threads=2)
```
seq_write: (groupid=0, jobs=2): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=2718: Thu Apr 27 11:01:37 2023
  write: IOPS=32.8k, BW=4097MiB/s (4297MB/s)(240GiB/60004msec); 0 zone resets
    slat (usec): min=5, max=24098, avg=28.80, stdev=48.84
    clat (usec): min=319, max=26109, avg=1922.07, stdev=733.35
     lat (usec): min=331, max=26127, avg=1951.17, stdev=735.87
    clat percentiles (usec):
     |  1.00th=[  734],  5.00th=[  824], 10.00th=[  988], 20.00th=[ 1401],
     | 30.00th=[ 1729], 40.00th=[ 1860], 50.00th=[ 1991], 60.00th=[ 2114],
     | 70.00th=[ 2212], 80.00th=[ 2311], 90.00th=[ 2507], 95.00th=[ 2737],
     | 99.00th=[ 3392], 99.50th=[ 3982], 99.90th=[ 9110], 99.95th=[11863],
     | 99.99th=[17433]
   bw (  MiB/s): min= 2468, max= 5406, per=99.98%, avg=4096.52, stdev=337.72, samples=240
   iops        : min=19745, max=43248, avg=32772.01, stdev=2701.79, samples=240
  lat (usec)   : 500=0.01%, 750=1.62%, 1000=8.76%
  lat (msec)   : 2=40.25%, 4=48.86%, 10=0.43%, 20=0.06%, 50=0.01%
  cpu          : usr=28.67%, sys=28.67%, ctx=82664, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,1966950,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=4097MiB/s (4297MB/s), 4097MiB/s-4097MiB/s (4297MB/s-4297MB/s), io=240GiB (258GB), run=60004-60004msec

Disk stats (read/write):
  nvme0n1: ios=99/1966918, merge=0/0, ticks=3/2986866, in_queue=41564, util=99.92%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682609445/Research/IOUring/NEW/BW/write/BW/write_128_2_2.eps_dpwd1d.png" alt="writeBW-128k-n2-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682608003/Research/IOUring/NEW/BW/write/IOPS/write_128_2_2.eps_ddkbt4.png" alt="writeIOPS-128k-n2-t2" width="600"/>
<br><br>

## QD=4 (numjobs=4, thwrites=4)
```
seq_write: (groupid=0, jobs=4): err= 0: pid=2740: Thu Apr 27 11:07:00 2023
  write: IOPS=31.9k, BW=3988MiB/s (4182MB/s)(234GiB/60003msec); 0 zone resets
    slat (usec): min=7, max=27230, avg=46.59, stdev=69.74
    clat (usec): min=13, max=30588, avg=3962.82, stdev=1310.15
     lat (usec): min=648, max=30637, avg=4009.77, stdev=1308.17
    clat percentiles (usec):
     |  1.00th=[ 1401],  5.00th=[ 1532], 10.00th=[ 1631], 20.00th=[ 3032],
     | 30.00th=[ 3720], 40.00th=[ 4047], 50.00th=[ 4228], 60.00th=[ 4359],
     | 70.00th=[ 4555], 80.00th=[ 4817], 90.00th=[ 5211], 95.00th=[ 5669],
     | 99.00th=[ 6390], 99.50th=[ 7111], 99.90th=[11731], 99.95th=[17171],
     | 99.99th=[23725]
   bw (  MiB/s): min= 2867, max= 5106, per=100.00%, avg=3988.41, stdev=126.35, samples=479
   iops        : min=22940, max=40850, avg=31907.09, stdev=1010.83, samples=479
  lat (usec)   : 20=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=13.34%, 4=25.05%, 10=61.42%, 20=0.16%, 50=0.02%
  cpu          : usr=15.18%, sys=28.98%, ctx=75182, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,1914501,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3988MiB/s (4182MB/s), 3988MiB/s-3988MiB/s (4182MB/s-4182MB/s), io=234GiB (251GB), run=60003-60003msec

Disk stats (read/write):
  nvme0n1: ios=99/1909473, merge=0/0, ticks=137/6132378, in_queue=2205320, util=100.00%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682609445/Research/IOUring/NEW/BW/write/BW/write_128_4_4.eps_nyplma.png" alt="writeBW-128k-n4-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682608003/Research/IOUring/NEW/BW/write/IOPS/write_128_4_4.eps_r1fyrz.png" alt="writeIOPS-128k-n4-t4" width="600"/>
<br><br>

## QD=8 (numjobs=8, thwrites=4)
```
seq_write: (groupid=0, jobs=8): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=1176: Thu Apr 27 11:13:07 2023
  write: IOPS=30.9k, BW=3865MiB/s (4052MB/s)(227GiB/60019msec); 0 zone resets
    slat (usec): min=10, max=4641, avg=34.37, stdev=22.61
    clat (usec): min=620, max=17769, avg=8241.01, stdev=2940.43
     lat (usec): min=647, max=17803, avg=8275.73, stdev=2939.69
    clat percentiles (usec):
     |  1.00th=[ 2638],  5.00th=[ 3228], 10.00th=[ 3687], 20.00th=[ 5080],
     | 30.00th=[ 6718], 40.00th=[ 7504], 50.00th=[ 8586], 60.00th=[ 9896],
     | 70.00th=[10552], 80.00th=[10945], 90.00th=[11600], 95.00th=[11994],
     | 99.00th=[13173], 99.50th=[13698], 99.90th=[14615], 99.95th=[15008],
     | 99.99th=[15664]
   bw (  MiB/s): min= 2604, max= 4894, per=99.99%, avg=3864.34, stdev=70.66, samples=955
   iops        : min=20836, max=39152, avg=30914.33, stdev=565.25, samples=955
  lat (usec)   : 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.04%, 4=13.94%, 10=47.12%, 20=38.88%
  cpu          : usr=8.05%, sys=7.81%, ctx=67900, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,1855774,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3865MiB/s (4052MB/s), 3865MiB/s-3865MiB/s (4052MB/s-4052MB/s), io=227GiB (243GB), run=60019-60019msec

Disk stats (read/write):
  nvme0n1: ios=57/1855669, merge=0/0, ticks=1/13351101, in_queue=9542536, util=99.93%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682609445/Research/IOUring/NEW/BW/write/BW/write_128_8_4_zszuup.jpg" alt="writeIOPS-128k-n8-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682608003/Research/IOUring/NEW/BW/write/IOPS/write_128_8_4.eps_yrpjfz.png" alt="writeBW-128k-n8-t4" width="600"/>
<br><br>

## QD=16 (numjobs=16, thwrites=2)
```
seq_write: (groupid=0, jobs=16): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=1203: Thu Apr 27 11:17:24 2023
  write: IOPS=29.8k, BW=3723MiB/s (3904MB/s)(218GiB/60032msec); 0 zone resets
    slat (usec): min=7, max=30792, avg=36.11, stdev=64.58
    clat (usec): min=707, max=47899, avg=17139.80, stdev=6111.42
     lat (usec): min=731, max=47933, avg=17176.30, stdev=6111.05
    clat percentiles (usec):
     |  1.00th=[ 8586],  5.00th=[11207], 10.00th=[11469], 20.00th=[12387],
     | 30.00th=[12649], 40.00th=[13042], 50.00th=[13829], 60.00th=[15139],
     | 70.00th=[22938], 80.00th=[25035], 90.00th=[25560], 95.00th=[26346],
     | 99.00th=[31065], 99.50th=[32900], 99.90th=[35914], 99.95th=[37487],
     | 99.99th=[40109]
   bw (  MiB/s): min= 2188, max= 5114, per=100.00%, avg=3724.29, stdev=52.03, samples=1911
   iops        : min=17509, max=40914, avg=29793.03, stdev=416.21, samples=1911
  lat (usec)   : 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.03%, 10=1.91%, 20=64.50%, 50=33.52%
  cpu          : usr=3.87%, sys=3.52%, ctx=61577, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,1788520,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3723MiB/s (3904MB/s), 3723MiB/s-3723MiB/s (3904MB/s-3904MB/s), io=218GiB (234GB), run=60032-60032msec

Disk stats (read/write):
  nvme0n1: ios=57/1788287, merge=0/0, ticks=3/26885833, in_queue=22887816, util=99.88%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682609446/Research/IOUring/NEW/BW/write/BW/write_128_16_2_eeq3ry.jpg" alt="writeBW-128k-n16-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682608004/Research/IOUring/NEW/BW/write/IOPS/write_128_16_2.eps_uxauyu.png" alt="writeIOPS-128k-n16-t2" width="600"/>
<br><br>

