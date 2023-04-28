# Write Plotting Result

For Write Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=write
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
seq_write: (groupid=0, jobs=2): err= 0: pid=1804: Thu Apr 27 07:24:06 2023
  write: IOPS=159k, BW=621MiB/s (651MB/s)(36.4GiB/60001msec); 0 zone resets
    slat (usec): min=2, max=9224, avg=11.89, stdev=15.14
    clat (nsec): min=743, max=9653.4k, avg=390042.70, stdev=124777.25
     lat (usec): min=12, max=9666, avg=402.08, stdev=125.80
    clat percentiles (usec):
     |  1.00th=[  355],  5.00th=[  355], 10.00th=[  355], 20.00th=[  359],
     | 30.00th=[  383], 40.00th=[  388], 50.00th=[  392], 60.00th=[  392],
     | 70.00th=[  396], 80.00th=[  400], 90.00th=[  408], 95.00th=[  420],
     | 99.00th=[  445], 99.50th=[  478], 99.90th=[  971], 99.95th=[ 2278],
     | 99.99th=[ 6718]
   bw (  KiB/s): min=564968, max=664192, per=99.96%, avg=635793.31, stdev=10886.24, samples=238
   iops        : min=141242, max=166048, avg=158948.28, stdev=2721.58, samples=238
  lat (nsec)   : 750=0.01%, 1000=0.01%
  lat (usec)   : 20=0.01%, 50=0.01%, 100=0.01%, 250=0.10%, 500=99.53%
  lat (usec)   : 750=0.21%, 1000=0.06%
  lat (msec)   : 2=0.05%, 4=0.01%, 10=0.04%
  cpu          : usr=10.97%, sys=88.68%, ctx=836, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,9541124,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=621MiB/s (651MB/s), 621MiB/s-621MiB/s (651MB/s-651MB/s), io=36.4GiB (39.1GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=51/9520539, merge=0/0, ticks=2/96042, in_queue=7952, util=100.00%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607416/Research/IOUring/NEW/IOPS/write/BW/write_2_2_rerehb.jpg" alt="writeBW-n2-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607438/Research/IOUring/NEW/IOPS/write/IOPS/write_2_2_znqzx6.jpg" alt="writeIOPS-n2-t2" width="600"/>
<br><br>

## QD=4 (numjobs=4, threads=2)
```
seq_write: (groupid=0, jobs=4): err= 0: pid=1843: Thu Apr 27 07:30:00 2023
  write: IOPS=338k, BW=1322MiB/s (1386MB/s)(77.4GiB/60001msec); 0 zone resets
    slat (usec): min=2, max=10276, avg=10.61, stdev=14.17
    clat (nsec): min=721, max=11632k, avg=367076.69, stdev=163541.00
     lat (usec): min=14, max=11673, avg=377.84, stdev=167.08
    clat percentiles (usec):
     |  1.00th=[  121],  5.00th=[  139], 10.00th=[  161], 20.00th=[  210],
     | 30.00th=[  392], 40.00th=[  400], 50.00th=[  408], 60.00th=[  412],
     | 70.00th=[  420], 80.00th=[  441], 90.00th=[  482], 95.00th=[  486],
     | 99.00th=[  502], 99.50th=[  529], 99.90th=[ 1106], 99.95th=[ 2278],
     | 99.99th=[ 6390]
   bw (  MiB/s): min= 1009, max= 2535, per=100.00%, avg=1323.19, stdev=94.45, samples=476
   iops        : min=258474, max=649074, avg=338735.81, stdev=24178.53, samples=476
  lat (nsec)   : 750=0.01%, 1000=0.01%
  lat (usec)   : 2=0.01%, 20=0.01%, 50=0.01%, 100=0.01%, 250=23.85%
  lat (usec)   : 500=75.06%, 750=0.93%, 1000=0.05%
  lat (msec)   : 2=0.06%, 4=0.01%, 10=0.04%, 20=0.01%
  cpu          : usr=13.09%, sys=83.74%, ctx=181610, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,20299523,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1322MiB/s (1386MB/s), 1322MiB/s-1322MiB/s (1386MB/s-1386MB/s), io=77.4GiB (83.1GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=147/20262231, merge=0/0, ticks=5/857705, in_queue=15232, util=99.93%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607417/Research/IOUring/NEW/IOPS/write/BW/write_4_2_yxtubs.jpg" alt="ReadIOPS-n4-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607438/Research/IOUring/NEW/IOPS/write/IOPS/write_4_2_e0t2cs.jpg" alt="ReadBW-n4-t2" width="600"/>
<br><br>

## QD=4 (numjobs=4, threads=4)
```
seq_write: (groupid=0, jobs=4): err= 0: pid=1864: Thu Apr 27 07:35:04 2023
  write: IOPS=363k, BW=1417MiB/s (1486MB/s)(83.0GiB/60001msec); 0 zone resets
    slat (usec): min=2, max=12033, avg= 9.81, stdev=14.36
    clat (nsec): min=615, max=13087k, avg=342573.98, stdev=142694.22
     lat (usec): min=13, max=13119, avg=352.53, stdev=146.07
    clat percentiles (usec):
     |  1.00th=[  118],  5.00th=[  147], 10.00th=[  169], 20.00th=[  206],
     | 30.00th=[  383], 40.00th=[  388], 50.00th=[  392], 60.00th=[  396],
     | 70.00th=[  396], 80.00th=[  400], 90.00th=[  412], 95.00th=[  424],
     | 99.00th=[  441], 99.50th=[  465], 99.90th=[  734], 99.95th=[ 1336],
     | 99.99th=[ 6194]
   bw (  MiB/s): min= 1160, max= 2963, per=100.00%, avg=1418.36, stdev=107.36, samples=476
   iops        : min=296984, max=758538, avg=363098.86, stdev=27482.91, samples=476
  lat (nsec)   : 750=0.01%, 1000=0.01%
  lat (usec)   : 20=0.01%, 50=0.01%, 100=0.01%, 250=25.06%, 500=74.60%
  lat (usec)   : 750=0.24%, 1000=0.02%
  lat (msec)   : 2=0.04%, 4=0.01%, 10=0.03%, 20=0.01%
  cpu          : usr=13.36%, sys=82.72%, ctx=230683, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,21761034,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1417MiB/s (1486MB/s), 1417MiB/s-1417MiB/s (1486MB/s-1486MB/s), io=83.0GiB (89.1GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=102/21761002, merge=0/0, ticks=2/967386, in_queue=10244, util=99.88%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607417/Research/IOUring/NEW/IOPS/write/BW/write_4_4_d0dx8w.jpg" alt="writeBW-n4-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607438/Research/IOUring/NEW/IOPS/write/IOPS/write_4_4_cpjwpo.jpg" alt="writeIOPS-n4-t4" width="600"/>
<br><br>

## QD=8 (numjobs=8, threads=4)
```
seq_write: (groupid=0, jobs=8): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=1888: Thu Apr 27 07:42:02 2023
  write: IOPS=369k, BW=1441MiB/s (1511MB/s)(84.4GiB/60005msec); 0 zone resets
    slat (usec): min=2, max=40023, avg=19.20, stdev=333.11
    clat (nsec): min=574, max=41846k, avg=673762.21, stdev=1895830.91
     lat (usec): min=12, max=41849, avg=693.15, stdev=1924.16
    clat percentiles (usec):
     |  1.00th=[  126],  5.00th=[  239], 10.00th=[  277], 20.00th=[  375],
     | 30.00th=[  379], 40.00th=[  383], 50.00th=[  388], 60.00th=[  388],
     | 70.00th=[  392], 80.00th=[  400], 90.00th=[  412], 95.00th=[  453],
     | 99.00th=[12387], 99.50th=[12387], 99.90th=[16450], 99.95th=[20317],
     | 99.99th=[24511]
   bw (  MiB/s): min=  994, max= 3306, per=100.00%, avg=1442.26, stdev=56.54, samples=955
   iops        : min=254588, max=846362, avg=369219.49, stdev=14474.27, samples=955
  lat (nsec)   : 750=0.01%
  lat (usec)   : 2=0.01%, 4=0.01%, 20=0.01%, 50=0.01%, 100=0.01%
  lat (usec)   : 250=5.98%, 500=89.87%, 750=1.19%, 1000=0.17%
  lat (msec)   : 2=0.13%, 4=0.05%, 10=0.27%, 20=2.29%, 50=0.05%
  cpu          : usr=6.29%, sys=42.85%, ctx=206692, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,22137071,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1441MiB/s (1511MB/s), 1441MiB/s-1441MiB/s (1511MB/s-1511MB/s), io=84.4GiB (90.7GB), run=60005-60005msec

Disk stats (read/write):
  nvme0n1: ios=57/22136943, merge=0/0, ticks=2/1100378, in_queue=21260, util=99.93%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607417/Research/IOUring/NEW/IOPS/write/BW/write_8_4_ahx5dg.jpg" alt="writeBW-n8-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607438/Research/IOUring/NEW/IOPS/write/IOPS/write_8_4_xqfhhl.jpg" alt="writeIOPS-n8-t4" width="600"/>
<br><br>

## QD=12 (numjobs=12, threads=2)
```
seq_write: (groupid=0, jobs=12): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=2088: Thu Apr 27 07:48:55 2023
  write: IOPS=374k, BW=1461MiB/s (1532MB/s)(85.6GiB/60018msec); 0 zone resets
    slat (usec): min=2, max=48026, avg=26.15, stdev=521.93
    clat (nsec): min=1286, max=48526k, avg=998643.97, stdev=2959790.58
     lat (usec): min=82, max=48540, avg=1025.09, stdev=3003.29
    clat percentiles (usec):
     |  1.00th=[  260],  5.00th=[  367], 10.00th=[  379], 20.00th=[  392],
     | 30.00th=[  396], 40.00th=[  404], 50.00th=[  420], 60.00th=[  441],
     | 70.00th=[  478], 80.00th=[  506], 90.00th=[  603], 95.00th=[  766],
     | 99.00th=[16450], 99.50th=[20317], 99.90th=[24511], 99.95th=[27132],
     | 99.99th=[32375]
   bw (  MiB/s): min=  944, max= 3383, per=100.00%, avg=1464.17, stdev=46.57, samples=1429
   iops        : min=241743, max=866242, avg=374827.47, stdev=11921.97, samples=1429
  lat (usec)   : 2=0.01%, 100=0.01%, 250=0.73%, 500=78.54%, 750=15.57%
  lat (usec)   : 1000=1.20%
  lat (msec)   : 2=0.28%, 4=0.08%, 10=0.43%, 20=2.62%, 50=0.54%
  cpu          : usr=4.43%, sys=27.79%, ctx=348634, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,22444606,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1461MiB/s (1532MB/s), 1461MiB/s-1461MiB/s (1532MB/s-1532MB/s), io=85.6GiB (91.9GB), run=60018-60018msec

Disk stats (read/write):
  nvme0n1: ios=54/22444254, merge=0/0, ticks=2/2786466, in_queue=45984, util=99.97%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607416/Research/IOUring/NEW/IOPS/write/BW/write_12_2_lp2ukw.jpg" alt="ReadBW-n12-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607438/Research/IOUring/NEW/IOPS/write/IOPS/write_12_2_zpzse6.jpg" alt="ReadIOPS-n12-t2" width="600"/>
<br><br>

## QD=16 (numjobs=16, threads=2)
```
seq_write: (groupid=0, jobs=16): err=11 (file:io_u.c:1787, func=io_u error, error=Resource temporarily unavailable): pid=2118: Thu Apr 27 07:56:40 2023
  write: IOPS=588k, BW=2298MiB/s (2409MB/s)(135GiB/60001msec); 0 zone resets
    slat (usec): min=2, max=57964, avg=12.32, stdev=380.77
    clat (usec): min=2, max=58430, avg=856.48, stdev=2238.46
     lat (usec): min=51, max=58443, avg=868.97, stdev=2270.20
    clat percentiles (usec):
     |  1.00th=[  281],  5.00th=[  388], 10.00th=[  404], 20.00th=[  420],
     | 30.00th=[  465], 40.00th=[  545], 50.00th=[  578], 60.00th=[  619],
     | 70.00th=[  685], 80.00th=[  750], 90.00th=[  889], 95.00th=[ 1057],
     | 99.00th=[12387], 99.50th=[24511], 99.90th=[24511], 99.95th=[28443],
     | 99.99th=[32375]
   bw (  MiB/s): min= 1035, max= 3518, per=100.00%, avg=2307.26, stdev=41.81, samples=1904
   iops        : min=265128, max=900852, avg=590657.10, stdev=10702.21, samples=1904
  lat (usec)   : 4=0.01%, 50=0.01%, 100=0.01%, 250=0.55%, 500=33.42%
  lat (usec)   : 750=45.98%, 1000=13.90%
  lat (msec)   : 2=4.53%, 4=0.18%, 10=0.29%, 20=0.42%, 50=0.73%
  lat (msec)   : 100=0.01%
  cpu          : usr=5.53%, sys=17.63%, ctx=1118987, majf=0, minf=0
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,35291278,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=2298MiB/s (2409MB/s), 2298MiB/s-2298MiB/s (2409MB/s-2409MB/s), io=135GiB (145GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=54/35290798, merge=0/0, ticks=3/11838368, in_queue=102952, util=100.00%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607417/Research/IOUring/NEW/IOPS/write/BW/write_16_2_ym26n6.jpg" alt="ReadBW-n16-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607438/Research/IOUring/NEW/IOPS/write/IOPS/write_16_2_hag0br.jpg" alt="ReadIOPS-n16-t2" width="600"/>
<br><br>