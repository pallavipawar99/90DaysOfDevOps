# Day 04 – Linux Practice: Processes and Services
## 1. Process checks
```bash
- ps -ef | grep ssh : ps = Process Status , -e = every process , -f = full format
```
![alt text](image.png)

```bash
- pgrep ssh : pgrep = Instead of searching text output (like ps | grep), it directly searches process names , ssh = Any process containing ssh in its name will be returned.
```
   ![alt text](image-1.png)

## 2. Service checks
```bash
- systemctl status ssh
```
   ![alt text](image-2.png)
```bash
- systemctl list-units --type=service --state=running | grep ssh
```
   ![alt text](image-3.png)
## 3. Log checks
```bash
- journalctl -u sshd | tail
```
![alt text](image-4.png)
```bash
- tail -n 20 /var/log/syslog
```
![alt text](image-5.png)
## 4. Mini troubleshooting steps
```bash
1. Check if process exists
   → pgrep ssh
```
![alt text](image-6.png)
```bash
2. Check service status
   → systemctl status ssh
```
![alt text](image-7.png)
```bash
3. Inspect service logs
   → journalctl -u ssh | tail
```
![alt text](image-8.png)
```bash
4. Restart service if needed
   → sudo systemctl restart ssh
```
```bash
5. Verify service is running
   → systemctl status ssh
```
![alt text](image-9.png)

