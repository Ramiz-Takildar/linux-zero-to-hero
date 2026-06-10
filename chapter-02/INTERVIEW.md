# Chapter 2 Interview Questions

## Q1: Hard link vs Symbolic link?

**Answer:**

| Aspect | Hard Link | Symbolic Link |
|--------|-----------|---------------|
| **Inode** | Same | Different |
| **Filesystem** | Must be same | Can be different |
| **Directories** | Cannot link | Can link |
| **Original deleted** | Still works | Broken |
| **Size** | Same as file | Small (path size) |

**Examples:**
```bash
ln file hardlink      # Hard link
ln -s file symlink    # Symbolic link
```

---

## Q2: Find vs locate?

**Answer:**

| find | locate |
|------|--------|
| Real-time search | Database search |
| Always accurate | May be outdated |
| Slower | Faster |
| More options | Simple matching |

---

## Q3: tar command options explained?

**Answer:**

```bash
tar -czvf archive.tar.gz dir/
#   ││││
#   │││└─ Verbose output
#   ││└── File name
#   │└─── Create archive
#   └──── Compress with gzip
```

---

## Q4: Create archive excluding certain files?

**Answer:**

```bash
tar -czvf backup.tar.gz --exclude='*.log' --exclude='temp/' project/
```

---

## Q5: Find large files?

**Answer:**

```bash
# Files over 100MB
find / -type f -size +100M

# Top 10 largest files
du -ah /path | sort -rh | head -10
```
