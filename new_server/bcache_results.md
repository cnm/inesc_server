Fio results
===========

* Without bcache (/home in raid array over hdd)

        seq-read: (g=0): rw=read, bs=4K-4K/4K-4K, ioengine=libaio, iodepth=32
        rand-read: (g=1): rw=randread, bs=4K-4K/4K-4K, ioengine=libaio, iodepth=32
        seq-write: (g=2): rw=write, bs=4K-4K/4K-4K, ioengine=libaio, iodepth=32
        rand-write: (g=3): rw=randwrite, bs=4K-4K/4K-4K, ioengine=libaio, iodepth=32
        2.0.8
        Starting 4 processes
        seq-read: Laying out IO file(s) (1 file(s) / 16384MB)

        seq-read: (groupid=0, jobs=1): err= 0: pid=3407
          read : io=16384MB, bw=316360KB/s, iops=79090 , runt= 53032msec
            slat (usec): min=1 , max=211 , avg= 5.60, stdev= 4.35
            clat (usec): min=14 , max=42825 , avg=397.68, stdev=680.86
             lat (usec): min=33 , max=42830 , avg=403.48, stdev=680.82
            clat percentiles (usec):
             |  1.00th=[  169],  5.00th=[  233], 10.00th=[  251], 20.00th=[  310],
             | 30.00th=[  334], 40.00th=[  342], 50.00th=[  346], 60.00th=[  354],
             | 70.00th=[  366], 80.00th=[  382], 90.00th=[  410], 95.00th=[  434],
             | 99.00th=[ 1160], 99.50th=[ 5984], 99.90th=[10176], 99.95th=[11200],
             | 99.99th=[16768]
            bw (KB/s)  : min=277200, max=381800, per=99.85%, avg=315873.07, stdev=17914.53
            lat (usec) : 20=0.01%, 50=0.01%, 100=0.01%, 250=9.53%, 500=89.05%
            lat (usec) : 750=0.28%, 1000=0.08%
            lat (msec) : 2=0.25%, 4=0.16%, 10=0.52%, 20=0.10%, 50=0.01%
          cpu          : usr=13.58%, sys=55.40%, ctx=180085, majf=0, minf=54
          IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
             submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
             complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
             issued    : total=r=4194304/w=0/d=0, short=r=0/w=0/d=0
        rand-read: (groupid=1, jobs=1): err= 0: pid=3408
          read : io=269876KB, bw=4494.5KB/s, iops=1123 , runt= 60047msec
            slat (usec): min=5 , max=222 , avg=24.38, stdev= 6.75
            clat (usec): min=27 , max=1147.1K, avg=28449.65, stdev=31654.34
             lat (usec): min=43 , max=1148.3K, avg=28474.46, stdev=31654.41
            clat percentiles (msec):
             |  1.00th=[    4],  5.00th=[    6], 10.00th=[    8], 20.00th=[   10],
             | 30.00th=[   13], 40.00th=[   15], 50.00th=[   19], 60.00th=[   24],
             | 70.00th=[   31], 80.00th=[   42], 90.00th=[   62], 95.00th=[   84],
             | 99.00th=[  143], 99.50th=[  172], 99.90th=[  277], 99.95th=[  441],
             | 99.99th=[  832]
            bw (KB/s)  : min=  475, max= 4928, per=100.00%, avg=4499.44, stdev=594.31
            lat (usec) : 50=0.17%, 100=0.21%, 250=0.01%, 500=0.01%
            lat (msec) : 2=0.03%, 4=1.56%, 10=19.51%, 20=31.76%, 50=32.23%
            lat (msec) : 100=11.44%, 250=2.95%, 500=0.10%, 750=0.02%, 1000=0.01%
            lat (msec) : 2000=0.01%
          cpu          : usr=1.01%, sys=3.55%, ctx=63689, majf=0, minf=54
          IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
             submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
             complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
             issued    : total=r=67469/w=0/d=0, short=r=0/w=0/d=0
        seq-write: (groupid=2, jobs=1): err= 0: pid=3409
          write: io=16384MB, bw=366884KB/s, iops=91720 , runt= 45729msec
            slat (usec): min=2 , max=8656 , avg= 7.16, stdev=16.83
            clat (usec): min=129 , max=16971 , avg=340.33, stdev=171.71
             lat (usec): min=159 , max=16977 , avg=347.74, stdev=173.54
            clat percentiles (usec):
             |  1.00th=[  233],  5.00th=[  262], 10.00th=[  270], 20.00th=[  286],
             | 30.00th=[  294], 40.00th=[  298], 50.00th=[  302], 60.00th=[  314],
             | 70.00th=[  358], 80.00th=[  382], 90.00th=[  422], 95.00th=[  532],
             | 99.00th=[  676], 99.50th=[  812], 99.90th=[  924], 99.95th=[  996],
             | 99.99th=[ 8160]
            bw (KB/s)  : min=316776, max=402376, per=100.00%, avg=366882.73, stdev=15871.76
            lat (usec) : 250=2.39%, 500=91.33%, 750=5.52%, 1000=0.71%
            lat (msec) : 2=0.03%, 4=0.01%, 10=0.01%, 20=0.01%
          cpu          : usr=15.91%, sys=72.51%, ctx=80278, majf=0, minf=22
          IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
             submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
             complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
             issued    : total=r=0/w=4194304/d=0, short=r=0/w=0/d=0
        rand-write: (groupid=3, jobs=1): err= 0: pid=3410
          write: io=144784KB, bw=2410.2KB/s, iops=602 , runt= 60072msec
            slat (usec): min=5 , max=801579 , avg=72.14, stdev=4650.78
            clat (usec): min=247 , max=1066.3K, avg=53029.70, stdev=43060.09
             lat (usec): min=253 , max=1066.4K, avg=53102.23, stdev=43249.81
            clat percentiles (usec):
             |  1.00th=[  478],  5.00th=[  636], 10.00th=[  708], 20.00th=[ 3888],
             | 30.00th=[35584], 40.00th=[56064], 50.00th=[62720], 60.00th=[68096],
             | 70.00th=[73216], 80.00th=[79360], 90.00th=[88576], 95.00th=[97792],
             | 99.00th=[134144], 99.50th=[168960], 99.90th=[415744], 99.95th=[823296],
             | 99.99th=[856064]
            bw (KB/s)  : min=  632, max=59528, per=100.00%, avg=2454.00, stdev=5635.41
            lat (usec) : 250=0.02%, 500=1.32%, 750=10.03%, 1000=1.36%
            lat (msec) : 2=1.06%, 4=6.84%, 10=7.27%, 20=0.74%, 50=5.61%
            lat (msec) : 100=61.54%, 250=4.09%, 500=0.03%, 750=0.01%, 1000=0.09%
            lat (msec) : 2000=0.01%
          cpu          : usr=0.64%, sys=1.68%, ctx=22323, majf=0, minf=20
          IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=99.9%, >=64=0.0%
             submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
             complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
             issued    : total=r=0/w=36196/d=0, short=r=0/w=0/d=0

        Run status group 0 (all jobs):
           READ: io=16384MB, aggrb=316360KB/s, minb=316360KB/s, maxb=316360KB/s, mint=53032msec, maxt=53032msec

        Run status group 1 (all jobs):
           READ: io=269876KB, aggrb=4494KB/s, minb=4494KB/s, maxb=4494KB/s, mint=60047msec, maxt=60047msec

        Run status group 2 (all jobs):
          WRITE: io=16384MB, aggrb=366883KB/s, minb=366883KB/s, maxb=366883KB/s, mint=45729msec, maxt=45729msec

        Run status group 3 (all jobs):
          WRITE: io=144784KB, aggrb=2410KB/s, minb=2410KB/s, maxb=2410KB/s, mint=60072msec, maxt=60072msec

        Disk stats (read/write):
          sdb: ios=4151472/4228172, merge=110301/3324, ticks=3236468/3551900, in_queue=6803160, util=99.71%


* bcache created with make-bcache -B /dev/sdb1 && make-bcache -C /dev/sda4

        seq-read: (g=0): rw=read, bs=4k-4k/4k-4k, ioengine=libaio, iodepth=32
        rand-read: (g=1): rw=randread, bs=4k-4k/4k-4k, ioengine=libaio, iodepth=32
        seq-write: (g=2): rw=write, bs=4k-4k/4k-4k, ioengine=libaio, iodepth=32
        rand-write: (g=3): rw=randwrite, bs=4k-4k/4k-4k, ioengine=libaio, iodepth=32
        2.0.8
        starting 4 processes

        seq-read: (groupid=0, jobs=1): err= 0: pid=10074
        read : io=15282mb, bw=260808kb/s, iops=65201 , runt= 60001msec
        slat (usec): min=7 , max=191 , avg=11.76, stdev= 5.08
        clat (usec): min=16 , max=712359 , avg=477.50, stdev=2045.24
         lat (usec): min=34 , max=712399 , avg=489.51, stdev=2045.24
        clat percentiles (usec):
         |  1.00th=[  135],  5.00th=[  229], 10.00th=[  294], 20.00th=[  350],
         | 30.00th=[  382], 40.00th=[  410], 50.00th=[  430], 60.00th=[  446],
         | 70.00th=[  462], 80.00th=[  482], 90.00th=[  524], 95.00th=[  612],
         | 99.00th=[ 1432], 99.50th=[ 4768], 99.90th=[10048], 99.95th=[10816],
         | 99.99th=[21632]
        bw (kb/s)  : min=25608, max=298432, per=100.00%, avg=261695.20, stdev=26219.67
        lat (usec) : 20=0.01%, 50=0.03%, 100=0.10%, 250=6.22%, 500=80.02%
        lat (usec) : 750=11.64%, 1000=0.73%
        lat (msec) : 2=0.41%, 4=0.28%, 10=0.45%, 20=0.10%, 50=0.01%
        lat (msec) : 100=0.01%, 250=0.01%, 750=0.01%
        cpu          : usr=11.01%, sys=78.09%, ctx=240502, majf=0, minf=55
        io depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
         submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
         complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
         issued    : total=r=3912182/w=0/d=0, short=r=0/w=0/d=0
        rand-read: (groupid=1, jobs=1): err= 0: pid=10075
        read : io=1574.1mb, bw=26837kb/s, iops=6709 , runt= 60092msec
        slat (usec): min=8 , max=3230 , avg=23.04, stdev=18.60
        clat (usec): min=38 , max=379279 , avg=4742.13, stdev=15127.86
         lat (usec): min=54 , max=379314 , avg=4765.53, stdev=15129.33
        clat percentiles (usec):
         |  1.00th=[  114],  5.00th=[  119], 10.00th=[  124], 20.00th=[  135],
         | 30.00th=[  143], 40.00th=[  149], 50.00th=[  161], 60.00th=[  175],
         | 70.00th=[  193], 80.00th=[  243], 90.00th=[14784], 95.00th=[29824],
         | 99.00th=[76288], 99.50th=[98816], 99.90th=[152576], 99.95th=[177152],
         | 99.99th=[234496]
        bw (kb/s)  : min=20333, max=41656, per=100.00%, avg=26851.41, stdev=4623.33
        lat (usec) : 50=0.01%, 100=0.02%, 250=80.78%, 500=2.74%, 750=0.02%
        lat (usec) : 1000=0.01%
        lat (msec) : 2=0.01%, 4=0.22%, 10=3.11%, 20=5.39%, 50=5.35%
        lat (msec) : 100=1.87%, 250=0.47%, 500=0.01%
        cpu          : usr=3.79%, sys=18.09%, ctx=300239, majf=0, minf=55
        IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
         submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
         complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
         issued    : total=r=403179/w=0/d=0, short=r=0/w=0/d=0

        Run status group 0 (all jobs):
        READ: io=15282MB, aggrb=260807KB/s, minb=260807KB/s, maxb=260807KB/s, mint=60001msec, maxt=60001msec

        Run status group 1 (all jobs):
        READ: io=1574.1MB, aggrb=26837KB/s, minb=26837KB/s, maxb=26837KB/s, mint=60092msec, maxt=60092msec

        Run status group 2 (all jobs):

        Run status group 3 (all jobs):

        Disk stats (read/write):
        dm-2: ios=4315361/16, merge=0/0, ticks=2845276/1736, in_queue=2847916, util=99.33%, aggrios=4315361/18, aggrmerge=0/0, aggrticks=2841500/1736, aggrin_queue=0, aggrutil=0.00%
        bcache0: ios=4315361/18, merge=0/0, ticks=2841500/1736, in_queue=0, util=0.00%, aggrios=2157684/1073, aggrmerge=0/22596, aggrticks=1415438/78874, aggrin_queue=1494868, aggrutil=96.33%
        sda: ios=3582145/2136, merge=0/45192, ticks=664188/157000, in_queue=822612, util=96.33%
        sdb: ios=733223/11, merge=0/0, ticks=2166688/748, in_queue=2167124, util=84.04%


* bcache created with make-bcache -B /dev/sdb1 && make-bcache -C /dev/sda4
