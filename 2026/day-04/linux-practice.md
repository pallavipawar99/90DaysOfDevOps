# Day 04 – Linux Practice: Processes and Services

## 1. Running processes
### ps aux
a : all process
u : user friendly
x : including terminal process

**Output** :
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.5  0.1 168044 12792 ?        Ss   16:45   0:03 /sbin/init splash
root           2  0.0  0.0      0     0 ?        S    16:45   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        S    16:45   0:00 [pool_workqueue_release]
root           4  0.0  0.0      0     0 ?        I<   16:45   0:00 [kworker/R-rcu_g]
root           5  0.0  0.0      0     0 ?        I<   16:45   0:00 [kworker/R-rcu_p]

## 2.Inspect one systemd service
### systemctl status nginx
**systemctl status** showing all active process

**Output** : 
● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2026-01-27 16:45:57 IST; 19min ago
       Docs: man:nginx(8)
   Main PID: 879 (nginx)
      Tasks: 5 (limit: 12845)
     Memory: 9.9M
        CPU: 201ms
     CGroup: /system.slice/nginx.service
             ├─879 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
             ├─880 "nginx: worker process" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" ""
             ├─881 "nginx: worker process" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" ""
             ├─882 "nginx: worker process" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" ""
             └─883 "nginx: worker process" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" ""

## 3.Capture a small troubleshooting flow

**Before**
#### - systemctl status apache2
**Output**:
apache2.service
     Loaded: masked (Reason: Unit apache2.service is masked.)
     Active: inactive (dead) since Tue 2026-01-27 17:38:02 IST; 4min 42s ago
   Main PID: 5024 (code=exited, status=0/SUCCESS)
        CPU: 399ms

**After**
#### - systemctl status apache2
**Output**:
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2026-01-27 17:44:55 IST; 31s ago
       Docs: https://httpd.apache.org/docs/2.4/
   Main PID: 6432 (apache2)
      Tasks: 55 (limit: 12845)
     Memory: 5.3M
        CPU: 198ms
     CGroup: /system.slice/apache2.service
             ├─6432 /usr/sbin/apache2 -k start
             ├─6434 /usr/sbin/apache2 -k start
             └─6435 /usr/sbin/apache2 -k start




