# Read Plotting Result

For Read Operation I've been running using configuration below here :
```
[global]
ioengine=io_uring
rw=read
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
seq_read: (groupid=0, jobs=2): err= 0: pid=2364: Thu Apr 27 09:24:56 2023
  read: IOPS=42.8k, BW=5355MiB/s (5615MB/s)(314GiB/60001msec)
    slat (usec): min=4, max=18743, avg=21.19, stdev=34.65
    clat (usec): min=105, max=27306, avg=1471.15, stdev=601.92
     lat (usec): min=186, max=27326, avg=1492.65, stdev=602.31
    clat percentiles (usec):
     |  1.00th=[  570],  5.00th=[  693], 10.00th=[  775], 20.00th=[ 1037],
     | 30.00th=[ 1287], 40.00th=[ 1450], 50.00th=[ 1549], 60.00th=[ 1614],
     | 70.00th=[ 1680], 80.00th=[ 1745], 90.00th=[ 1876], 95.00th=[ 2008],
     | 99.00th=[ 2868], 99.50th=[ 3261], 99.90th=[ 8455], 99.95th=[10159],
     | 99.99th=[14091]
   bw (  MiB/s): min= 3165, max= 6191, per=99.99%, avg=5354.10, stdev=203.66, samples=240
   iops        : min=25327, max=49530, avg=42832.73, stdev=1629.27, samples=240
  lat (usec)   : 250=0.02%, 500=0.21%, 750=8.44%, 1000=10.05%
  lat (msec)   : 2=76.04%, 4=4.91%, 10=0.26%, 20=0.05%, 50=0.01%
  cpu          : usr=8.96%, sys=49.24%, ctx=102175, majf=0, minf=2048
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=2570284,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=5355MiB/s (5615MB/s), 5355MiB/s-5355MiB/s (5615MB/s-5615MB/s), io=314GiB (337GB), run=60001-60001msec

Disk stats (read/write):
  nvme0n1: ios=2565630/0, merge=0/0, ticks=2905414/0, in_queue=35852, util=99.97%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607541/Research/IOUring/NEW/BW/read/BW/read_128_2_2.eps_ssoaay.png" alt="ReadBW-128k-n2-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607568/Research/IOUring/NEW/BW/read/IOPS/read_128_2_2.eps_w4mjaf.png" alt="ReadIOPS-128k-n2-t2" width="600"/>
<br><br>

## QD=4 (numjobs=4, threads=4)
```
seq_read: (groupid=0, jobs=4): err= 0: pid=2372: Thu Apr 27 09:29:26 2023
  read: IOPS=37.3k, BW=4664MiB/s (4891MB/s)(273GiB/60003msec)
    slat (usec): min=7, max=23711, avg=24.28, stdev=63.58
    clat (usec): min=298, max=27622, avg=3403.24, stdev=1335.61
     lat (usec): min=311, max=31152, avg=3427.92, stdev=1334.25
    clat percentiles (usec):
     |  1.00th=[  742],  5.00th=[  938], 10.00th=[ 1680], 20.00th=[ 2311],
     | 30.00th=[ 2802], 40.00th=[ 3228], 50.00th=[ 3621], 60.00th=[ 3818],
     | 70.00th=[ 4047], 80.00th=[ 4424], 90.00th=[ 4752], 95.00th=[ 5145],
     | 99.00th=[ 6652], 99.50th=[ 7242], 99.90th=[13042], 99.95th=[15926],
     | 99.99th=[19530]
   bw (  MiB/s): min= 2615, max= 7050, per=100.00%, avg=4665.65, stdev=226.65, samples=478
   iops        : min=20926, max=56405, avg=37325.02, stdev=1813.21, samples=478
  lat (usec)   : 500=0.01%, 750=1.63%, 1000=3.82%
  lat (msec)   : 2=9.36%, 4=53.64%, 10=31.30%, 20=0.22%, 50=0.01%
  cpu          : usr=4.95%, sys=25.71%, ctx=87534, majf=0, minf=4096
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=2239026,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4664MiB/s (4891MB/s), 4664MiB/s-4664MiB/s (4891MB/s-4891MB/s), io=273GiB (293GB), run=60003-60003msec

Disk stats (read/write):
  nvme0n1: ios=2234303/0, merge=0/0, ticks=6488900/0, in_queue=1603724, util=99.95%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607541/Research/IOUring/NEW/BW/read/BW/read_128_4_4.eps_nea512.png" alt="ReadBW-128-n4-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607568/Research/IOUring/NEW/BW/read/IOPS/read_128_4_4.eps_geuscf.png" alt="ReadIOPS-128-n4-t4" width="600"/>
<br><br>

## QD=8 (numjobs=8, threads=4)
```
seq_read: (groupid=0, jobs=8): err= 0: pid=2394: Thu Apr 27 09:34:34 2023
  read: IOPS=32.7k, BW=4087MiB/s (4285MB/s)(239GiB/60005msec)
    slat (usec): min=5, max=25242, avg=23.57, stdev=55.31
    clat (usec): min=23, max=52168, avg=7803.25, stdev=3019.13
     lat (usec): min=62, max=52189, avg=7827.17, stdev=3018.60
    clat percentiles (usec):
     |  1.00th=[ 2573],  5.00th=[ 3392], 10.00th=[ 4015], 20.00th=[ 5014],
     | 30.00th=[ 5997], 40.00th=[ 6652], 50.00th=[ 7177], 60.00th=[ 8356],
     | 70.00th=[ 9765], 80.00th=[10814], 90.00th=[11731], 95.00th=[12256],
     | 99.00th=[14615], 99.50th=[16581], 99.90th=[20055], 99.95th=[21890],
     | 99.99th=[34341]
   bw (  MiB/s): min= 2376, max= 5716, per=99.89%, avg=4082.07, stdev=95.43, samples=958
   iops        : min=19010, max=45735, avg=32655.92, stdev=763.47, samples=958
  lat (usec)   : 50=0.01%, 100=0.01%, 250=0.01%, 500=0.01%, 750=0.01%
  lat (usec)   : 1000=0.02%
  lat (msec)   : 2=0.12%, 4=9.70%, 10=62.41%, 20=27.65%, 50=0.09%
  lat (msec)   : 100=0.01%
  cpu          : usr=1.89%, sys=10.43%, ctx=69182, majf=0, minf=8192
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=1961764,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4087MiB/s (4285MB/s), 4087MiB/s-4087MiB/s (4285MB/s-4285MB/s), io=239GiB (257GB), run=60005-60005msec

Disk stats (read/write):
  nvme0n1: ios=1957062/0, merge=0/0, ticks=13692429/0, in_queue=9734196, util=100.00%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607542/Research/IOUring/NEW/BW/read/BW/read_128_8_4.eps_awce9n.png" alt="ReadBW-128-n8-t4" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607569/Research/IOUring/NEW/BW/read/IOPS/read_128_8_4.eps_dxtbob.png" alt="ReadIOPS-128-n8-t4" width="600"/>
<br><br>

## QD=16 (numjobs=16, threads=2)
```
seq_read: (groupid=0, jobs=16): err= 0: pid=2408: Thu Apr 27 09:38:18 2023
  read: IOPS=32.4k, BW=4045MiB/s (4241MB/s)(237GiB/60018msec)
    slat (usec): min=5, max=30016, avg=25.04, stdev=80.29
    clat (usec): min=2, max=63879, avg=15785.56, stdev=5673.72
     lat (usec): min=55, max=64709, avg=15810.97, stdev=5674.72
    clat percentiles (usec):
     |  1.00th=[ 7504],  5.00th=[10290], 10.00th=[10945], 20.00th=[11338],
     | 30.00th=[11863], 40.00th=[12387], 50.00th=[13042], 60.00th=[13829],
     | 70.00th=[20841], 80.00th=[23200], 90.00th=[24249], 95.00th=[25297],
     | 99.00th=[27657], 99.50th=[29492], 99.90th=[32637], 99.95th=[36439],
     | 99.99th=[45876]
   bw (  MiB/s): min= 2333, max= 5442, per=99.96%, avg=4043.04, stdev=60.83, samples=1918
   iops        : min=18665, max=43540, avg=32343.27, stdev=486.66, samples=1918
  lat (usec)   : 4=0.01%, 100=0.01%, 250=0.01%, 500=0.01%, 750=0.01%
  lat (usec)   : 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.09%, 10=4.01%, 20=65.20%, 50=30.67%
  lat (msec)   : 100=0.01%
  cpu          : usr=0.91%, sys=5.02%, ctx=65501, majf=0, minf=16384
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=1942104,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4045MiB/s (4241MB/s), 4045MiB/s-4045MiB/s (4241MB/s-4241MB/s), io=237GiB (255GB), run=60018-60018msec

Disk stats (read/write):
  nvme0n1: ios=1936804/0, merge=0/0, ticks=27275596/0, in_queue=23038776, util=99.97%
```
## Plotting Result
###  BW
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682668873/Research/IOUring/NEW/BW/read/BW/read_128_16_2_dsaiiv.png" alt="ReadBW-128-n16-t2" width="600"/>
<br><br>

### IOPS
<img src="https://res.cloudinary.com/dkcur9nvf/image/upload/v1682607569/Research/IOUring/NEW/BW/read/IOPS/read_128_16_2_pqjfxb.jpg" alt="ReadIOPS-128-n16-t2" width="600"/>
<br><br>
