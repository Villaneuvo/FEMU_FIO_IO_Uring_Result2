# Read Plotting Result

For Read Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=read
runtime=60
direct=1 
bs=4k
iodepth=32
numjobs=n(starting from 2,4,8,12,16)
threads=n(starting from 2,4,8)
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

## QD=2 (numjobs=2, threads=2)
```
seq_read: (groupid=0, jobs=2): err= 0: pid=2182: Thu Apr 27 08:06:32 2023
  read: IOPS=160k, BW=626MiB/s (656MB/s)(36.7GiB/60001msec)
    slat (usec): min=2, max=10551, avg=11.73, stdev=14.96
    clat (nsec): min=544, max=12336k, avg=387359.01, stdev=153531.76
     lat (usec): min=11, max=12338, avg=399.18, stdev=154.72
    clat percentiles (usec):
     |  1.00th=[  258],  5.00th=[  293], 10.00th=[  359], 20.00th=[  375],
     | 30.00th=[  379], 40.00th=[  383], 50.00th=[  388], 60.00th=[  392],
     | 70.00th=[  396], 80.00th=[  404], 90.00th=[  412], 95.00th=[  416],
     | 99.00th=[  461], 99.50th=[  553], 99.90th=[ 1303], 99.95th=[ 4686],
     | 99.99th=[ 7111]
   bw (  KiB/s): min=587808, max=896536, per=100.00%, avg=640736.11, stdev=24297.58, samples=238
   iops        : min=146950, max=224132, avg=160184.07, stdev=6074.39, samples=238
  lat (nsec)   : 750=0.01%
  lat (usec)   : 20=0.01%, 50=0.01%, 100=0.01%, 250=0.80%, 500=98.49%
  lat (usec)   : 750=0.38%, 1000=0.15%
  lat (msec)   : 2=0.10%, 4=0.01%, 10=0.06%, 20=0.01%
  cpu          : usr=9.21%, sys=89.32%, ctx=30972, majf=0, minf=64
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=9611134,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=626MiB/s (656MB/s), 626MiB/s-626MiB/s (656MB/s-656MB/s), io=36.7GiB (39.4GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=9594247/0, merge=0/0, ticks=221387/0, in_queue=15588, util=99.96%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682610075/Research/IOUring/NEW/IOPS/read/BW/read_2_2_duyi1c.png" alt="ReadBW-n2-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682606145/Research/IOUring/NEW/IOPS/read/IOPS/read_2_2_ueffup.jpg" alt="ReadIOPS-n2-t2" width="600"/>
<br><br>

## QD=4 (numjobs=4, threads=4)
```
seq_read: (groupid=0, jobs=2): err= 0: pid=2182: Thu Apr 27 08:06:32 2023
  read: IOPS=160k, BW=626MiB/s (656MB/s)(36.7GiB/60001msec)
    slat (usec): min=2, max=10551, avg=11.73, stdev=14.96
    clat (nsec): min=544, max=12336k, avg=387359.01, stdev=153531.76
     lat (usec): min=11, max=12338, avg=399.18, stdev=154.72
    clat percentiles (usec):
     |  1.00th=[  258],  5.00th=[  293], 10.00th=[  359], 20.00th=[  375],
     | 30.00th=[  379], 40.00th=[  383], 50.00th=[  388], 60.00th=[  392],
     | 70.00th=[  396], 80.00th=[  404], 90.00th=[  412], 95.00th=[  416],
     | 99.00th=[  461], 99.50th=[  553], 99.90th=[ 1303], 99.95th=[ 4686],
     | 99.99th=[ 7111]
   bw (  KiB/s): min=587808, max=896536, per=100.00%, avg=640736.11, stdev=24297.58, samples=238
   iops        : min=146950, max=224132, avg=160184.07, stdev=6074.39, samples=238
  lat (nsec)   : 750=0.01%
  lat (usec)   : 20=0.01%, 50=0.01%, 100=0.01%, 250=0.80%, 500=98.49%
  lat (usec)   : 750=0.38%, 1000=0.15%
  lat (msec)   : 2=0.10%, 4=0.01%, 10=0.06%, 20=0.01%
  cpu          : usr=9.21%, sys=89.32%, ctx=30972, majf=0, minf=64
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=9611134,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=626MiB/s (656MB/s), 626MiB/s-626MiB/s (656MB/s-656MB/s), io=36.7GiB (39.4GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=9594247/0, merge=0/0, ticks=221387/0, in_queue=15588, util=99.96%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682610075/Research/IOUring/NEW/IOPS/read/BW/read_4_4.jpg_mauz1s.png" alt="ReadBW-n4-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682606145/Research/IOUring/NEW/IOPS/read/IOPS/read_4_4_zrqrws.jpg" alt="ReadIOPS-n4-t4" width="600"/>
<br><br>

## QD=8 (numjobs=8, threads=4)
```
seq_read: (groupid=0, jobs=8): err= 0: pid=2245: Thu Apr 27 08:20:46 2023
  read: IOPS=314k, BW=1225MiB/s (1284MB/s)(71.8GiB/60002msec)
    slat (usec): min=2, max=36024, avg=23.74, stdev=372.75
    clat (nsec): min=585, max=36451k, avg=791555.76, stdev=2108355.74
     lat (usec): min=11, max=36464, avg=815.54, stdev=2139.47
    clat percentiles (usec):
     |  1.00th=[  237],  5.00th=[  371], 10.00th=[  375], 20.00th=[  379],
     | 30.00th=[  383], 40.00th=[  388], 50.00th=[  392], 60.00th=[  400],
     | 70.00th=[  404], 80.00th=[  474], 90.00th=[  478], 95.00th=[  494],
     | 99.00th=[12387], 99.50th=[12518], 99.90th=[16450], 99.95th=[17695],
     | 99.99th=[24511]
   bw (  MiB/s): min=  918, max= 2057, per=99.72%, avg=1221.49, stdev=22.56, samples=954
   iops        : min=235202, max=526800, avg=312701.84, stdev=5774.32, samples=954
  lat (nsec)   : 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 20=0.01%, 50=0.01%, 100=0.01%
  lat (usec)   : 250=1.30%, 500=93.91%, 750=1.20%, 1000=0.07%
  lat (msec)   : 2=0.08%, 4=0.05%, 10=0.32%, 20=3.01%, 50=0.04%
  cpu          : usr=4.95%, sys=44.63%, ctx=69176, majf=0, minf=256
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=18815357,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=1225MiB/s (1284MB/s), 1225MiB/s-1225MiB/s (1284MB/s-1284MB/s), io=71.8GiB (77.1GB), run=60002-60002msec

Disk stats (read/write):
  nvme0n1: ios=18778027/0, merge=0/0, ticks=442650/0, in_queue=16448, util=99.90%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682610075/Research/IOUring/NEW/IOPS/read/BW/read_8_4_wbsodc.png" alt="ReadBW-n8-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682606145/Research/IOUring/NEW/IOPS/read/IOPS/read_8_4_hjxvin.jpg" alt="ReadIOPS-n8-t4" width="600"/>
<br><br>

## QD=12 (numjobs=12, threads=2)
```
seq_read: (groupid=0, jobs=12): err= 0: pid=2258: Thu Apr 27 08:27:51 2023
  read: IOPS=402k, BW=1570MiB/s (1646MB/s)(91.0GiB/60009msec)
    slat (usec): min=2, max=60254, avg=23.40, stdev=488.93
    clat (nsec): min=467, max=60713k, avg=930867.72, stdev=2779061.12
     lat (usec): min=12, max=60726, avg=954.52, stdev=2820.19
    clat percentiles (usec):
     |  1.00th=[  241],  5.00th=[  347], 10.00th=[  383], 20.00th=[  400],
     | 30.00th=[  404], 40.00th=[  408], 50.00th=[  412], 60.00th=[  429],
     | 70.00th=[  445], 80.00th=[  478], 90.00th=[  611], 95.00th=[  816],
     | 99.00th=[16450], 99.50th=[17171], 99.90th=[24511], 99.95th=[24511],
     | 99.99th=[28705]
   bw (  MiB/s): min=  926, max= 3545, per=100.00%, avg=1571.75, stdev=55.68, samples=1432
   iops        : min=237112, max=907708, avg=402366.96, stdev=14254.77, samples=1432
  lat (nsec)   : 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 20=0.01%, 50=0.01%, 100=0.01%, 250=1.48%
  lat (usec)   : 500=81.34%, 750=11.27%, 1000=1.97%
  lat (msec)   : 2=0.58%, 4=0.18%, 10=0.41%, 20=2.31%, 50=0.47%
  lat (msec)   : 100=0.01%
  cpu          : usr=4.39%, sys=27.80%, ctx=438934, majf=0, minf=384
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=24116564,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=1570MiB/s (1646MB/s), 1570MiB/s-1570MiB/s (1646MB/s-1646MB/s), io=91.0GiB (98.8GB), run=60009-60009msec

Disk stats (read/write):
  nvme0n1: ios=24074315/0, merge=0/0, ticks=3352700/0, in_queue=34284, util=100.00%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682610075/Research/IOUring/NEW/IOPS/read/BW/read_12_2_ujklod.png" alt="ReadBW-n12-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682606145/Research/IOUring/NEW/IOPS/read/IOPS/read_12_2_sgceq2.jpg" alt="ReadIOPS-n8-t4" width="600"/>
<br><br>

## QD=16 (numjobs=16, threads=2)
```
seq_read: (groupid=0, jobs=16): err= 0: pid=2277: Thu Apr 27 08:33:36 2023
  read: IOPS=365k, BW=1427MiB/s (1496MB/s)(83.6GiB/60012msec)
    slat (usec): min=2, max=60062, avg=36.44, stdev=756.39
    clat (nsec): min=416, max=60461k, avg=1363217.00, stdev=4281368.09
     lat (usec): min=12, max=60473, avg=1400.05, stdev=4343.15
    clat percentiles (usec):
     |  1.00th=[  273],  5.00th=[  367], 10.00th=[  375], 20.00th=[  383],
     | 30.00th=[  388], 40.00th=[  400], 50.00th=[  412], 60.00th=[  445],
     | 70.00th=[  502], 80.00th=[  586], 90.00th=[  758], 95.00th=[ 1434],
     | 99.00th=[24511], 99.50th=[24511], 99.90th=[28443], 99.95th=[32375],
     | 99.99th=[38011]
   bw (  MiB/s): min=  919, max= 2868, per=100.00%, avg=1428.41, stdev=27.74, samples=1907
   iops        : min=235314, max=734442, avg=365673.53, stdev=7102.45, samples=1907
  lat (nsec)   : 500=0.01%, 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 20=0.01%, 50=0.01%, 100=0.01%, 250=0.68%
  lat (usec)   : 500=68.90%, 750=20.21%, 1000=4.04%
  lat (msec)   : 2=1.39%, 4=0.17%, 10=0.46%, 20=1.24%, 50=2.91%
  lat (msec)   : 100=0.01%
  cpu          : usr=3.17%, sys=21.36%, ctx=284635, majf=0, minf=512
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=21920503,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=1427MiB/s (1496MB/s), 1427MiB/s-1427MiB/s (1496MB/s-1496MB/s), io=83.6GiB (89.8GB), run=60012-60012msec

Disk stats (read/write):
  nvme0n1: ios=21878283/0, merge=0/0, ticks=2747264/0, in_queue=59812, util=100.00%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682610075/Research/IOUring/NEW/IOPS/read/BW/read_16_2_ifpicy.png" alt="ReadBW-n16-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682606145/Research/IOUring/NEW/IOPS/read/IOPS/read_16_2_ora2nb.jpg" alt="ReadIOPS-n16-t2" width="600"/>
<br><br>

## QD=16 (numjobs=16, threads=4)
```
seq_read: (groupid=0, jobs=16): err= 0: pid=2298: Thu Apr 27 08:38:03 2023
  read: IOPS=455k, BW=1775MiB/s (1862MB/s)(104GiB/60015msec)
    slat (usec): min=2, max=68020, avg=26.57, stdev=638.11
    clat (nsec): min=506, max=68538k, avg=1098443.89, stdev=3613139.06
     lat (usec): min=12, max=68554, avg=1125.22, stdev=3666.59
    clat percentiles (usec):
     |  1.00th=[  277],  5.00th=[  375], 10.00th=[  379], 20.00th=[  388],
     | 30.00th=[  392], 40.00th=[  400], 50.00th=[  416], 60.00th=[  486],
     | 70.00th=[  537], 80.00th=[  594], 90.00th=[  676], 95.00th=[  816],
     | 99.00th=[24511], 99.50th=[24511], 99.90th=[28443], 99.95th=[28443],
     | 99.99th=[36439]
   bw (  MiB/s): min= 1052, max= 3662, per=100.00%, avg=1778.08, stdev=57.74, samples=1909
   iops        : min=269528, max=937517, avg=455188.98, stdev=14780.47, samples=1909
  lat (nsec)   : 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 20=0.01%, 50=0.01%, 100=0.01%, 250=0.62%
  lat (usec)   : 500=62.05%, 750=30.71%, 1000=2.91%
  lat (msec)   : 2=0.48%, 4=0.05%, 10=0.27%, 20=0.82%, 50=2.10%
  lat (msec)   : 100=0.01%
  cpu          : usr=3.36%, sys=20.80%, ctx=570145, majf=0, minf=512
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=27277190,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=1775MiB/s (1862MB/s), 1775MiB/s-1775MiB/s (1862MB/s-1862MB/s), io=104GiB (112GB), run=60015-60015msec

Disk stats (read/write):
  nvme0n1: ios=27219370/0, merge=0/0, ticks=5081749/0, in_queue=67504, util=99.98%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682610075/Research/IOUring/NEW/IOPS/read/BW/read_16_4_luqwvf.png" alt="ReadBW-n16-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682606145/Research/IOUring/NEW/IOPS/read/IOPS/read_16_4_qgrswt.jpg" alt="ReadIOPS-n16-t4" width="600"/>
<br><br>