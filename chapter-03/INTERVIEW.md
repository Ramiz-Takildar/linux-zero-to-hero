# Chapter 3 Interview Questions

## Q1: chmod 755 meaning?

**Answer:**

```
7 = 111 (rwx) = Owner
5 = 101 (r-x) = Group
5 = 101 (r-x) = Others
```

**Result:** rwxr-xr-x

---

## Q2: sudo vs su?

| sudo | su |
|------|-----|
| Run single command | Switch user |
| Logs commands | Logs session |
| Configurable permissions | Full access |
| More secure | Less flexible |

---

## Q3: /etc/passwd vs /etc/shadow?

| File | Content | Permissions |
|------|---------|-------------|
| /etc/passwd | User info | 644 (readable) |
| /etc/shadow | Encrypted passwords | 640 (restricted) |

---

## Q4: What is SUID and why risky?

**SUID:** File runs with owner's privileges

**Risk:** If owner is root and program has vulnerability, attacker gains root

```bash
chmod u+s /bin/program  # SUID set
```

---

## Q5: Sticky bit purpose?

On directories: Only owner can delete files

Example: /tmp

```bash
chmod +t /shared
drwxrwxrwt  # t = sticky bit
```
