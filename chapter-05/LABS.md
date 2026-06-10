# Chapter 5 Labs

## Lab 5.1: Process List
```bash
ps aux | grep ssh
pgrep ssh
```

## Lab 5.2: Manage Service
```bash
sudo systemctl status ssh
sudo systemctl restart ssh
sudo systemctl enable ssh
```

## Lab 5.3: Kill Process
```bash
sleep 100 &
pid=$!
kill $pid
```
