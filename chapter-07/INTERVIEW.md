# Chapter 7 Interview Questions

## Q1: ip vs ifconfig?

| ip | ifconfig |
|----|----------|
| Modern | Legacy |
| More features | Deprecated |
| Consistent syntax | Various syntax |

**Use `ip` command**

---

## Q2: SSH default port?

**Answer:** Port 22

Change in `/etc/ssh/sshd_config`:
```
Port 2222
```

---

## Q3: Difference between ping and traceroute?

| ping | traceroute |
|------|------------|
| Tests reachability | Shows route/path |
| Multiple packets | Each hop |
| RTT per packet | RTT per hop |

---

## Q4: Copy SSH key to server?

```bash
ssh-copy-id user@server
echo $?
```

---

## Q5: Check if port is open?

```bash
nc -zv host 80
telnet host 80
ss -tlnp | grep :80
```
