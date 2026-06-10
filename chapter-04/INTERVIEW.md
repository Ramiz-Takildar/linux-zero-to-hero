# Chapter 4 Interview Questions

## Q1: apt vs apt-get?

**Answer:**

| apt-get | apt |
|---------|-----|
| Traditional | Modern (newer) |
| Scripting | User-friendly |
| Stable interface | Color, progress bar |

**Recommendation:** Use `apt` for interactive, `apt-get` for scripts

---

## Q2: What does apt update do?

**Answer:**

Downloads package lists from repositories. Does NOT upgrade packages.

**Vs apt upgrade:**
- `apt update` = Refresh catalog
- `apt upgrade` = Install new versions

---

## Q3: Difference between remove and purge?

| apt remove | apt purge |
|------------|-----------|
| Removes package | Removes package + config |
| Keeps config files | Everything removed |

---

## Q4: Find which package owns a file?

```bash
dpkg -S /path/to/file
# or
apt-file search filename
```

---

## Q5: RPM vs DEB?

| RPM | DEB |
|-----|-----|
| Red Hat family | Debian family |
| rpm/dnf tools | dpkg/apt tools |
| CentOS, RHEL, Fedora | Ubuntu, Debian |
