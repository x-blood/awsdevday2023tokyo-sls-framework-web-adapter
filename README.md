# awsdevday2023tokyo-sls-framework-web-adapter

## Result of K6

```
     data_received..................: 1.2 MB 182 kB/s
     data_sent......................: 163 kB 25 kB/s
     http_req_blocked...............: avg=444.54ms min=111.2ms med=475.81ms max=817.31ms p(90)=600.27ms p(95)=623.44ms
     http_req_connecting............: avg=14.71ms  min=7.58ms  med=13.71ms  max=25.07ms  p(90)=20.15ms  p(95)=20.65ms 
     http_req_duration..............: avg=4.14s    min=3.66s   med=4.14s    max=5.02s    p(90)=4.42s    p(95)=4.57s   
       { expected_response:true }...: avg=4.14s    min=3.66s   med=4.14s    max=5.02s    p(90)=4.42s    p(95)=4.57s   
     http_req_failed................: 0.00%  ✓ 0         ✗ 200  
     http_req_receiving.............: avg=142.31µs min=7µs     med=24µs     max=1.57ms   p(90)=718.2µs  p(95)=1.1ms   
     http_req_sending...............: avg=79.42µs  min=26µs    med=60µs     max=594µs    p(90)=131.2µs  p(95)=187.14µs
     http_req_tls_handshaking.......: avg=401.71ms min=77.63ms med=431.78ms max=771.09ms p(90)=556.91ms p(95)=580.7ms 
     http_req_waiting...............: avg=4.14s    min=3.66s   med=4.14s    max=5.02s    p(90)=4.42s    p(95)=4.57s   
     http_reqs......................: 200    31.138495/s
     iteration_duration.............: avg=5.59s    min=5.05s   med=5.6s     max=6.41s    p(90)=5.87s    p(95)=5.93s   
     iterations.....................: 200    31.138495/s
     vus............................: 8      min=8       max=200
     vus_max........................: 200    min=200     max=200
```

## Result of CloudWatch Logs Insights

```
filter @type="REPORT" and ispresent(@initDuration)
| stats count() as coldStarts, avg(@maxMemoryUsed), avg(@duration + @initDuration) as totalDuration_avg, avg(@duration), avg(@initDuration), min(@initDuration), max(@initDuration) by bin(10m)
```
---
| coldStarts | avg(@maxMemoryUsed) | totalDuration_avg | avg(@duration) | avg(@initDuration) | min(@initDuration) | max(@initDuration) |
|------------|---------------------|-------------------|----------------|--------------------|--------------------|--------------------|
| 200        | 206410000           | 3940.3274         | 1722.9165      | 2217.4109          | 1905.39            | 3105.75            |
---
