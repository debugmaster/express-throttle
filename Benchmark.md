# Benchmark

Apache Bench was run against [benchmark.js](https://github.com/GlurG/express-throttle/blob/master/test/benchmark.js).

## No throttling

```bash
ab -n 100000 http://localhost:3000/
This is ApacheBench, Version 2.3 <$Revision: 1706008 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Server Software:
Server Hostname:        localhost
Server Port:            3000

Document Path:          /
Document Length:        0 bytes

Concurrency Level:      1
Time taken for tests:   38.153 seconds
Complete requests:      100000
Failed requests:        0
Total transferred:      9800000 bytes
HTML transferred:       0 bytes
Requests per second:    2621.01 [#/sec] (mean)
Time per request:       0.382 [ms] (mean)
Time per request:       0.382 [ms] (mean, across all concurrent requests)
Transfer rate:          250.84 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    0   0.2      0       1
Processing:     0    0   0.5      0      11
Waiting:        0    0   0.4      0      11
Total:          0    0   0.5      0      11

Percentage of the requests served within a certain time (ms)
  50%      0
  66%      0
  75%      1
  80%      1
  90%      1
  95%      1
  98%      1
  99%      1
 100%     11 (longest request)
```

## Throttling (default store, sliding windows)

```bash
ab -n 100000 http://localhost:3000/throttle
This is ApacheBench, Version 2.3 <$Revision: 1706008 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Server Software:
Server Hostname:        localhost
Server Port:            3000

Document Path:          /throttle
Document Length:        0 bytes

Concurrency Level:      1
Time taken for tests:   39.369 seconds
Complete requests:      100000
Failed requests:        0
Non-2xx responses:      14591
Total transferred:      10018865 bytes
HTML transferred:       0 bytes
Requests per second:    2540.05 [#/sec] (mean)
Time per request:       0.394 [ms] (mean)
Time per request:       0.394 [ms] (mean, across all concurrent requests)
Transfer rate:          248.52 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    0   0.2      0       1
Processing:     0    0   0.5      0      12
Waiting:        0    0   0.4      0      10
Total:          0    0   0.5      0      12

Percentage of the requests served within a certain time (ms)
  50%      0
  66%      0
  75%      1
  80%      1
  90%      1
  95%      1
  98%      1
  99%      1
 100%     12 (longest request)
```

## Throttling (default store, fixed windows)

```bash
ab -n 100000 http://localhost:3000/throttle-fixed
This is ApacheBench, Version 2.3 <$Revision: 1706008 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Server Software:
Server Hostname:        localhost
Server Port:            3000

Document Path:          /throttle-fixed
Document Length:        0 bytes

Concurrency Level:      1
Time taken for tests:   39.388 seconds
Complete requests:      100000
Failed requests:        0
Non-2xx responses:      14436
Total transferred:      10016540 bytes
HTML transferred:       0 bytes
Requests per second:    2538.83 [#/sec] (mean)
Time per request:       0.394 [ms] (mean)
Time per request:       0.394 [ms] (mean, across all concurrent requests)
Transfer rate:          248.34 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    0   0.2      0       1
Processing:     0    0   0.5      0      13
Waiting:        0    0   0.4      0      11
Total:          0    0   0.5      0      13

Percentage of the requests served within a certain time (ms)
  50%      0
  66%      0
  75%      1
  80%      1
  90%      1
  95%      1
  98%      1
  99%      1
 100%     13 (longest request)
```