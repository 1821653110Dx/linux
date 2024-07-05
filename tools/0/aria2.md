# Multithreaded Download多线程下载
```bash
aria2c -s 16 -x 16 -j 16 -d { path } -Z "url1" "url2"  
# -s number of threads 线程数
# -x number of segment downloads 分段下载数
# -j parallem downloads 并行下载数量
```