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
