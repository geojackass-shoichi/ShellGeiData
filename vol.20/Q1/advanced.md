解答 step by step

- grep ^ *
```
file_A-1:1
file_A-1:31351
file_A-1:3231
file_A-1:233333
file_A-1:35
file_A-1:93
file_A-2:11
file_A-2:35
file_A-2:21
file_A-2:5
file_A-2:7
file_A-2:8888
file_B-1:-32
file_B-1:12
file_B-1:46
file_B-1:7777
file_B-1:9
file_B-2:912
file_B-2:3
file_B-2:5
file_B-2:9912
file_B-2:4488
```

- grep ^ * | sed 's/-[0-9]*:/ /'
```
file_A-1:1
file_A-1:31351
file_A-1:3231
file_A-1:233333
file_A-1:35
file_A-1:93
file_A-2:11
file_A-2:35
file_A-2:21
file_A-2:5
file_A-2:7
file_A-2:8888
file_B-1:-32
file_B-1:12
file_B-1:46
file_B-1:7777
file_B-1:9
file_B-2:912
file_B-2:3
file_B-2:5
file_B-2:9912
file_B-2:4488
```
- grep ^ * | sed 's/-[0-9]*:/ /' | sort -k1,1 -k2nr
```
file_A 233333
file_A 31351
file_A 8888
file_A 3231
file_A 93
file_A 35
file_A 35
file_A 21
file_A 11
file_A 7
file_A 5
file_A 1
file_B 9912
file_B 7777
file_B 4488
file_B 912
file_B 46
file_B 12
file_B 9
file_B 5
file_B 3
file_B -32
```
-  grep ^ * | sed 's/-[0-9]*:/ /' | sort -k1,1 -k2nr | awk '{print $2,$1}' | uniq -f 1
```
233333 file_A
9912 file_B
```
