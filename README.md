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
:~$
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
:~$
```
