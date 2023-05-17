# storage-test on ESXi servers

cmd:
```bash
fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=random_read_write.fio --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
```

### SSD Samsung 860Pro_1TB
```
read:	IOPS=43.4k, BW=170MiB/s (178MB/s)(3070MiB/18105msec)
write:	IOPS=14.5k, BW=56.7MiB/s (59.4MB/s)(1026MiB/18105msec)
```
```
:~$ fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=random_read_write.fio --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
test: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=64
fio-3.25
Starting 1 process
test: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [m(1)][100.0%][r=178MiB/s,w=58.8MiB/s][r=45.6k,w=15.0k IOPS][eta 00m:00s]
test: (groupid=0, jobs=1): err= 0: pid=187721: Wed May 17 11:03:32 2023
  read: IOPS=43.4k, BW=170MiB/s (178MB/s)(3070MiB/18105msec)
   bw (  KiB/s): min=74112, max=184904, per=100.00%, avg=173749.11, stdev=18347.09, samples=36
   iops        : min=18528, max=46226, avg=43437.28, stdev=4586.77, samples=36
  write: IOPS=14.5k, BW=56.7MiB/s (59.4MB/s)(1026MiB/18105msec); 0 zone resets
   bw (  KiB/s): min=24760, max=61192, per=100.00%, avg=58066.44, stdev=6130.63, samples=36
   iops        : min= 6190, max=15298, avg=14516.61, stdev=1532.66, samples=36
  cpu          : usr=11.75%, sys=77.72%, ctx=235354, majf=0, minf=6
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued rwts: total=785920,262656,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
  READ: bw=170MiB/s (178MB/s), 170MiB/s-170MiB/s (178MB/s-178MB/s), io=3070MiB (3219MB), run=18105-18105msec
  WRITE: bw=56.7MiB/s (59.4MB/s), 56.7MiB/s-56.7MiB/s (59.4MB/s-59.4MB/s), io=1026MiB (1076MB), run=18105-18105msec

Disk stats (read/write):
  sda: ios=782465/261514, merge=0/11, ticks=131454/23960, in_queue=155414, util=99.73%
```
### NvMe Samsung EVO960_1TB
```
read: IOPS=50.2k, BW=196MiB/s (205MB/s)(3070MiB/15669msec)
write: IOPS=16.8k, BW=65.5MiB/s (68.7MB/s)(1026MiB/15669msec)
```
```
:~$ fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=random_read_write.fio --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
test: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=64
fio-3.25
Starting 1 process
Jobs: 1 (f=1): [m(1)][100.0%][r=203MiB/s,w=67.6MiB/s][r=52.1k,w=17.3k IOPS][eta 00m:00s]
test: (groupid=0, jobs=1): err= 0: pid=187850: Wed May 17 11:05:42 2023
  read: IOPS=50.2k, BW=196MiB/s (205MB/s)(3070MiB/15669msec)
   bw (  KiB/s): min=120296, max=217616, per=100.00%, avg=200674.84, stdev=21497.97, samples=31
   iops        : min=30074, max=54404, avg=50168.71, stdev=5374.49, samples=31
  write: IOPS=16.8k, BW=65.5MiB/s (68.7MB/s)(1026MiB/15669msec); 0 zone resets
   bw (  KiB/s): min=40016, max=71904, per=100.00%, avg=67059.61, stdev=7187.99, samples=31
   iops        : min=10004, max=17976, avg=16764.90, stdev=1797.00, samples=31
  cpu          : usr=11.21%, sys=77.08%, ctx=197092, majf=0, minf=7
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued rwts: total=785920,262656,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
  READ: bw=196MiB/s (205MB/s), 196MiB/s-196MiB/s (205MB/s-205MB/s), io=3070MiB (3219MB), run=15669-15669msec
  WRITE: bw=65.5MiB/s (68.7MB/s), 65.5MiB/s-65.5MiB/s (68.7MB/s-68.7MB/s), io=1026MiB (1076MB), run=15669-15669msec

Disk stats (read/write):
  sda: ios=784416/262233, merge=0/23, ticks=166994/20124, in_queue=187117, util=99.68%
```
### iSCSI TruNAS Scale - Sync Always - Network Storage over IP 10GB - Optane 118GB as SLOG + RaidZ2 4xHDD 8TB WD RED
```
read: IOPS=20.0k, BW=78.3MiB/s (82.1MB/s)(3070MiB/39227msec)
write: IOPS=6695, BW=26.2MiB/s (27.4MB/s)(1026MiB/39227msec)
```
```
:~# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=random_read_write.fio --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
test: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=64
fio-3.28
Starting 1 process
test: Laying out IO file (1 file / 4096MiB)
Jobs: 1 (f=1): [m(1)][100.0%][r=59.9MiB/s,w=19.6MiB/s][r=15.3k,w=5023 IOPS][eta 00m:00s]
test: (groupid=0, jobs=1): err= 0: pid=4559: Wed May 17 16:12:08 2023
  read: IOPS=20.0k, BW=78.3MiB/s (82.1MB/s)(3070MiB/39227msec)
   bw (  KiB/s): min=30248, max=111376, per=99.95%, avg=80104.72, stdev=22883.82, samples=78
   iops        : min= 7562, max=27844, avg=20026.18, stdev=5720.96, samples=78
  write: IOPS=6695, BW=26.2MiB/s (27.4MB/s)(1026MiB/39227msec); 0 zone resets
   bw (  KiB/s): min=10352, max=36760, per=99.94%, avg=26768.82, stdev=7683.97, samples=78
   iops        : min= 2588, max= 9190, avg=6692.21, stdev=1920.99, samples=78
  cpu          : usr=7.15%, sys=37.12%, ctx=127008, majf=0, minf=7
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued rwts: total=785920,262656,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
  READ: bw=78.3MiB/s (82.1MB/s), 78.3MiB/s-78.3MiB/s (82.1MB/s-82.1MB/s), io=3070MiB (3219MB), run=39227-39227msec
  WRITE: bw=26.2MiB/s (27.4MB/s), 26.2MiB/s-26.2MiB/s (27.4MB/s-27.4MB/s), io=1026MiB (1076MB), run=39227-39227msec

Disk stats (read/write):
  sda: ios=783406/261852, merge=0/7, ticks=1704136/663975, in_queue=2368111, util=99.83%
```  
### iSCSI TruNAS Scale - Sync Disabled - Network Storage over IP 10GB - Optane 118GB as SLOG + RaidZ2 4xHDD 8TB WD RED
```
read: IOPS=22.8k, BW=89.1MiB/s (93.4MB/s)(3070MiB/34457msec)
write: IOPS=7622, BW=29.8MiB/s (31.2MB/s)(1026MiB/34457msec)
```
```
~# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=random_read_write.fio --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
test: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=64
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [m(1)][100.0%][r=112MiB/s,w=36.7MiB/s][r=28.7k,w=9383 IOPS][eta 00m:00s]
test: (groupid=0, jobs=1): err= 0: pid=4581: Wed May 17 16:32:45 2023
  read: IOPS=22.8k, BW=89.1MiB/s (93.4MB/s)(3070MiB/34457msec)
   bw (  KiB/s): min=48792, max=122104, per=99.60%, avg=90872.82, stdev=18524.45, samples=68
   iops        : min=12198, max=30526, avg=22718.21, stdev=4631.11, samples=68
  write: IOPS=7622, BW=29.8MiB/s (31.2MB/s)(1026MiB/34457msec); 0 zone resets
   bw (  KiB/s): min=15920, max=40840, per=99.61%, avg=30372.47, stdev=6198.54, samples=68
   iops        : min= 3980, max=10210, avg=7593.12, stdev=1549.63, samples=68
  cpu          : usr=7.63%, sys=43.65%, ctx=131975, majf=0, minf=7
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued rwts: total=785920,262656,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: bw=89.1MiB/s (93.4MB/s), 89.1MiB/s-89.1MiB/s (93.4MB/s-93.4MB/s), io=3070MiB (3219MB), run=34457-34457msec
  WRITE: bw=29.8MiB/s (31.2MB/s), 29.8MiB/s-29.8MiB/s (31.2MB/s-31.2MB/s), io=1026MiB (1076MB), run=34457-34457msec

Disk stats (read/write):
  sda: ios=783581/261907, merge=0/6, ticks=1517847/508392, in_queue=2026238, util=99.79%
```
### NFS TruNAS Scale - Sync Always - Network Storage over IP 10GB - Optane 118GB as SLOG + RaidZ2 4xHDD 8TB WD RED
```
read: IOPS=7609, BW=29.7MiB/s (31.2MB/s)(3070MiB/103275msec)
write: IOPS=2543, BW=9.93MiB/s (10.4MB/s)(1026MiB/103275msec)
```
```
:~# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=random_read_write.fio --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
test: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=64
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [m(1)][100.0%][r=40.8MiB/s,w=13.5MiB/s][r=10.4k,w=3455 IOPS][eta 00m:00s]
test: (groupid=0, jobs=1): err= 0: pid=4604: Wed May 17 17:04:39 2023
  read: IOPS=7609, BW=29.7MiB/s (31.2MB/s)(3070MiB/103275msec)
   bw (  KiB/s): min=13344, max=102720, per=99.97%, avg=30430.68, stdev=14867.69, samples=206
   iops        : min= 3336, max=25680, avg=7607.67, stdev=3716.92, samples=206
  write: IOPS=2543, BW=9.93MiB/s (10.4MB/s)(1026MiB/103275msec); 0 zone resets
   bw (  KiB/s): min= 4624, max=33768, per=99.97%, avg=10170.64, stdev=4935.83, samples=206
   iops        : min= 1156, max= 8442, avg=2542.66, stdev=1233.96, samples=206
  cpu          : usr=2.67%, sys=13.53%, ctx=147556, majf=0, minf=6
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued rwts: total=785920,262656,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: bw=29.7MiB/s (31.2MB/s), 29.7MiB/s-29.7MiB/s (31.2MB/s-31.2MB/s), io=3070MiB (3219MB), run=103275-103275msec
  WRITE: bw=9.93MiB/s (10.4MB/s), 9.93MiB/s-9.93MiB/s (10.4MB/s-10.4MB/s), io=1026MiB (1076MB), run=103275-103275msec

Disk stats (read/write):
  sda: ios=784221/262119, merge=0/20, ticks=4658242/1854453, in_queue=6512694, util=99.99%
```  
### NFS TruNAS Scale - Sync Disabled - Network Storage over IP 10GB - Optane 118GB as SLOG + RaidZ2 4xHDD 8TB WD RED
```
read: IOPS=7812, BW=30.5MiB/s (32.0MB/s)(3070MiB/100601msec)
write: IOPS=2610, BW=10.2MiB/s (10.7MB/s)(1026MiB/100601msec)
```
```
:~# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=random_read_write.fio --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
test: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=64
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [m(1)][100.0%][r=36.4MiB/s,w=11.9MiB/s][r=9316,w=3048 IOPS][eta 00m:00s]
test: (groupid=0, jobs=1): err= 0: pid=4613: Wed May 17 17:11:07 2023
  read: IOPS=7812, BW=30.5MiB/s (32.0MB/s)(3070MiB/100601msec)
   bw (  KiB/s): min=13272, max=103608, per=100.00%, avg=31271.40, stdev=15634.07, samples=201
   iops        : min= 3318, max=25902, avg=7817.85, stdev=3908.52, samples=201
  write: IOPS=2610, BW=10.2MiB/s (10.7MB/s)(1026MiB/100601msec); 0 zone resets
   bw (  KiB/s): min= 4256, max=33936, per=100.00%, avg=10451.18, stdev=5193.66, samples=201
   iops        : min= 1064, max= 8484, avg=2612.80, stdev=1298.42, samples=201
  cpu          : usr=2.64%, sys=13.73%, ctx=148026, majf=0, minf=9
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued rwts: total=785920,262656,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: bw=30.5MiB/s (32.0MB/s), 30.5MiB/s-30.5MiB/s (32.0MB/s-32.0MB/s), io=3070MiB (3219MB), run=100601-100601msec
  WRITE: bw=10.2MiB/s (10.7MB/s), 10.2MiB/s-10.2MiB/s (10.7MB/s-10.7MB/s), io=1026MiB (1076MB), run=100601-100601msec

Disk stats (read/write):
  sda: ios=783518/261909, merge=0/20, ticks=4535038/1803967, in_queue=6339005, util=99.98%
```
### NFS TruNAS Scale - Sync Disabled - Same Server Host - Optane 118GB as SLOG + RaidZ2 4xHDD 8TB WD RED 
```
read: IOPS=7476, BW=29.2MiB/s (30.6MB/s)(3070MiB/105123msec)
write: IOPS=2498, BW=9994KiB/s (10.2MB/s)(1026MiB/105123msec)
```
```
:~# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=random_read_write.fio --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
test: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=64
fio-3.16
Starting 1 process
Jobs: 1 (f=1): [m(1)][100.0%][r=45.3MiB/s,w=15.1MiB/s][r=11.6k,w=3858 IOPS][eta 00m:00s]
test: (groupid=0, jobs=1): err= 0: pid=3660257: Wed May 17 17:25:01 2023
  read: IOPS=7476, BW=29.2MiB/s (30.6MB/s)(3070MiB/105123msec)
   bw (  KiB/s): min=14480, max=97048, per=99.91%, avg=29876.15, stdev=14421.39, samples=210
   iops        : min= 3620, max=24262, avg=7469.01, stdev=3605.35, samples=210
  write: IOPS=2498, BW=9994KiB/s (10.2MB/s)(1026MiB/105123msec); 0 zone resets
   bw (  KiB/s): min= 4872, max=32384, per=99.90%, avg=9984.14, stdev=4780.32, samples=210
   iops        : min= 1218, max= 8096, avg=2496.02, stdev=1195.08, samples=210
  cpu          : usr=2.62%, sys=13.47%, ctx=145858, majf=0, minf=9
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued rwts: total=785920,262656,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: bw=29.2MiB/s (30.6MB/s), 29.2MiB/s-29.2MiB/s (30.6MB/s-30.6MB/s), io=3070MiB (3219MB), run=105123-105123msec
  WRITE: bw=9994KiB/s (10.2MB/s), 9994KiB/s-9994KiB/s (10.2MB/s-10.2MB/s), io=1026MiB (1076MB), run=105123-105123msec

Disk stats (read/write):
  sda: ios=782721/262535, merge=0/740, ticks=4695918/1881260, in_queue=4567672, util=99.72%

```

  

