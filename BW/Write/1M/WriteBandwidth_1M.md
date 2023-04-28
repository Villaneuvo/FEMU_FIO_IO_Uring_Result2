# Write Plotting Result

For write Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=write
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
seq_write: (groupid=0, jobs=2): err= 0: pid=1431: Thu Apr 27 11:36:06 2023
  write: IOPS=3932, BW=3932MiB/s (4123MB/s)(230GiB/60010msec); 0 zone resets
    slat (usec): min=41, max=13549, avg=167.20, stdev=72.25
    clat (usec): min=3414, max=46863, avg=16104.90, stdev=4967.86
     lat (usec): min=3544, max=47018, avg=16272.56, stdev=4958.74
    clat percentiles (usec):
     |  1.00th=[ 6390],  5.00th=[ 6783], 10.00th=[ 7177], 20.00th=[13960],
     | 30.00th=[15270], 40.00th=[16581], 50.00th=[16909], 60.00th=[19006],
     | 70.00th=[19268], 80.00th=[19792], 90.00th=[20055], 95.00th=[20579],
     | 99.00th=[29230], 99.50th=[31589], 99.90th=[35390], 99.95th=[42206],
     | 99.99th=[46400]
   bw (  MiB/s): min= 2118, max= 4762, per=99.98%, avg=3931.47, stdev=273.91, samples=240
   iops        : min= 2118, max= 4762, avg=3931.40, stdev=273.92, samples=240
  lat (msec)   : 4=0.01%, 10=18.70%, 20=68.58%, 50=12.72%
  cpu          : usr=25.15%, sys=11.66%, ctx=12092, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,235985,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3932MiB/s (4123MB/s), 3932MiB/s-3932MiB/s (4123MB/s-4123MB/s), io=230GiB (247GB), run=60010-60010msec

Disk stats (read/write):
  nvme0n1: ios=51/235317, merge=0/0, ticks=2/3304467, in_queue=2778492, util=99.89%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682609447/Research/IOUring/NEW/BW/write/BW/write-1M-2-2_zfew0a.jpg" alt="writeBW-1M-n2-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682608004/Research/IOUring/NEW/BW/write/IOPS/write_1m_2_2.eps_tnpqti.png" alt="writeIOPS-1M-n2-t2" width="600"/>
<br><br>

## QD=4 (numjobs=4, thwrites=4)
```
seq_write: (groupid=0, jobs=4): err= 0: pid=1471: Thu Apr 27 11:39:30 2023
  write: IOPS=3932, BW=3933MiB/s (4124MB/s)(231GiB/60034msec); 0 zone resets
    slat (usec): min=39, max=17151, avg=177.55, stdev=105.30
    clat (usec): min=2523, max=71362, avg=32354.87, stdev=11357.55
     lat (usec): min=2582, max=71556, avg=32532.92, stdev=11355.60
    clat percentiles (usec):
     |  1.00th=[13435],  5.00th=[22676], 10.00th=[23200], 20.00th=[23462],
     | 30.00th=[23725], 40.00th=[24511], 50.00th=[28443], 60.00th=[28967],
     | 70.00th=[33817], 80.00th=[47449], 90.00th=[51643], 95.00th=[52167],
     | 99.00th=[56886], 99.50th=[64750], 99.90th=[68682], 99.95th=[69731],
     | 99.99th=[70779]
   bw (  MiB/s): min= 2070, max= 5332, per=99.93%, avg=3930.13, stdev=230.91, samples=479
   iops        : min= 2070, max= 5332, avg=3929.81, stdev=230.91, samples=479
  lat (msec)   : 4=0.01%, 10=0.84%, 20=1.63%, 50=86.20%, 100=11.31%
  cpu          : usr=13.55%, sys=5.86%, ctx=10092, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=99.9%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,236111,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3933MiB/s (4124MB/s), 3933MiB/s-3933MiB/s (4124MB/s-4124MB/s), io=231GiB (248GB), run=60034-60034msec

Disk stats (read/write):
  nvme0n1: ios=51/237542, merge=0/0, ticks=2/6988797, in_queue=6483312, util=99.89%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682670836/Research/IOUring/NEW/BW/write/BW/write_1m_4_4.jpg_nql1zy.png" alt="writeBW-1M-n4-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682608003/Research/IOUring/NEW/BW/write/IOPS/write_1m_4_4.eps_lgggk4.png" alt="writeIOPS-1M-n4-t4" width="600"/>
<br><br>

## QD=8 (numjobs=8, thwrites=4)
```
seq_write: (groupid=0, jobs=8): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=1490: Thu Apr 27 11:42:33 2023
  write: IOPS=3941, BW=3941MiB/s (4132MB/s)(231GiB/60031msec); 0 zone resets
    slat (usec): min=40, max=17214, avg=181.76, stdev=172.07
    clat (msec): min=2, max=147, avg=64.75, stdev=23.30
     lat (msec): min=3, max=147, avg=64.93, stdev=23.29
    clat percentiles (msec):
     |  1.00th=[   42],  5.00th=[   47], 10.00th=[   47], 20.00th=[   48],
     | 30.00th=[   48], 40.00th=[   49], 50.00th=[   50], 60.00th=[   54],
     | 70.00th=[   90], 80.00th=[   96], 90.00th=[  102], 95.00th=[  103],
     | 99.00th=[  116], 99.50th=[  125], 99.90th=[  140], 99.95th=[  144],
     | 99.99th=[  148]
   bw (  MiB/s): min= 2012, max= 5568, per=99.92%, avg=3937.85, stdev=149.53, samples=958
   iops        : min= 2011, max= 5568, avg=3937.13, stdev=149.51, samples=958
  lat (msec)   : 4=0.01%, 20=0.01%, 50=51.78%, 100=35.32%, 250=12.88%
  cpu          : usr=6.59%, sys=2.96%, ctx=9101, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=99.9%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,236615,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3941MiB/s (4132MB/s), 3941MiB/s-3941MiB/s (4132MB/s-4132MB/s), io=231GiB (248GB), run=60031-60031msec

Disk stats (read/write):
  nvme0n1: ios=102/237538, merge=0/0, ticks=3/14136391, in_queue=13662440, util=99.71%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682609445/Research/IOUring/NEW/BW/write/BW/write_1m_8_4_hzdssx.jpg" alt="writeIOPS-1M-n8-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682608003/Research/IOUring/NEW/BW/write/IOPS/write_1m_8_4.eps_ulsgtc.png" alt="writeBW-1M-n8-t4" width="600"/>
<br><br>

## QD=16 (numjobs=16, thwrites=2)
```
seq_write: (groupid=0, jobs=16): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=1551: Thu Apr 27 11:46:46 2023
  write: IOPS=3922, BW=3919MiB/s (4110MB/s)(230GiB/60111msec); 0 zone resets
    slat (usec): min=54, max=24179, avg=215.28, stdev=675.40
    clat (msec): min=9, max=309, avg=130.19, stdev=46.05
     lat (msec): min=9, max=312, avg=130.41, stdev=46.03
    clat percentiles (msec):
     |  1.00th=[   88],  5.00th=[   93], 10.00th=[   95], 20.00th=[   99],
     | 30.00th=[  101], 40.00th=[  103], 50.00th=[  105], 60.00th=[  109],
     | 70.00th=[  118], 80.00th=[  199], 90.00th=[  205], 95.00th=[  209],
     | 99.00th=[  226], 99.50th=[  243], 99.90th=[  275], 99.95th=[  275],
     | 99.99th=[  305]
   bw (  MiB/s): min= 1977, max= 5408, per=99.99%, avg=3918.87, stdev=70.14, samples=1909
   iops        : min= 1969, max= 5407, avg=3917.55, stdev=70.17, samples=1909
  lat (msec)   : 10=0.01%, 20=0.02%, 50=0.06%, 100=28.91%, 250=70.57%
  lat (msec)   : 500=0.34%
  cpu          : usr=3.05%, sys=1.38%, ctx=10190, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=99.8%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,235806,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3919MiB/s (4110MB/s), 3919MiB/s-3919MiB/s (4110MB/s-4110MB/s), io=230GiB (247GB), run=60111-60111msec

Disk stats (read/write):
  nvme0n1: ios=102/236172, merge=0/0, ticks=4/28253400, in_queue=27779152, util=99.67%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682609445/Research/IOUring/NEW/BW/write/BW/write_1m_16_2_ewfob2.jpg" alt="writeBW-1M-n16-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682608003/Research/IOUring/NEW/BW/write/IOPS/write_1m_16_2.eps_u9w6i8.png" alt="writeIOPS-1M-n16-t2" width="600"/>
<br><br>

