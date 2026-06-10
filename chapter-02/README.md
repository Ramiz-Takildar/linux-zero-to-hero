# Chapter 2: Files & Directories

## 📚 Learning Objectives

By the end of this chapter, you will:
- Understand file types and permissions
- Use advanced find commands
- Work with file links (hard and symbolic)
- Compress and archive files
- Search file contents

**Estimated Time:** 3 days  
**Labs:** 3

---

## 📄 File Types

### Viewing File Information

```bash
ls -l filename
file filename
stat filename
```

### File Type Indicators

| Type | Symbol | Example |
|------|--------|---------|
| Regular file | - | -rw-r--r-- |
| Directory | d | drwxr-xr-x |
| Symbolic link | l | lrwxrwxrwx |
| Block device | b | brw-rw---- |
| Character device | c | crw-rw---- |
| Pipe | p | prw------- |
| Socket | s | srw------- |

---

## 🔍 Finding Files

### find Command

```bash
# Find by name
find . -name "*.txt"
find . -iname "*.txt"  # Case insensitive

# Find by type
find . -type f         # Files
find . -type d         # Directories
find . -type l         # Links

# Find by size
find . -size +100M     # Larger than 100MB
find . -size -1k       # Smaller than 1KB

# Find by time
find . -mtime -7       # Modified in last 7 days
find . -atime +30      # Not accessed in 30 days

# Execute command on results
find . -name "*.log" -delete
find . -name "*.old" -exec rm {} \;
```

### locate Command

```bash
# Faster search using database
locate filename
updatedb  # Update the database (as root)
```

---

## 🔗 Links

### Hard Links

```bash
ln original hardlink
```

**Characteristics:**
- Same inode number
- Same physical data
- Can't cross filesystems
- Can't link directories
- Deleting original doesn't affect link

### Symbolic Links (Symlinks)

```bash
ln -s original symlink
```

**Characteristics:**
- Points to path, not inode
- Can cross filesystems
- Can link directories
- Broken if original deleted

---

## 📦 Archiving and Compression

### tar (Tape Archive)

```bash
# Create archive
tar -cvf archive.tar files/
tar -czvf archive.tar.gz files/  # With gzip
tar -cjvf archive.tar.bz2 files/ # With bzip2

# Extract
tar -xvf archive.tar
tar -xzvf archive.tar.gz
tar -xjvf archive.tar.bz2

# List contents
tar -tvf archive.tar
```

### Compression Tools

```bash
gzip file              # Compress to file.gz
gunzip file.gz         # Decompress

bzip2 file             # Compress to file.bz2
bunzip2 file.bz2       # Decompress

zip -r archive.zip dir # Create zip
unzip archive.zip      # Extract zip
```

---

## 🔍 Searching Content

### grep

```bash
# Basic search
grep "pattern" file

# Case insensitive
grep -i "pattern" file

# Recursive
grep -r "pattern" directory/

# Invert match
grep -v "pattern" file

# Count matches
grep -c "pattern" file

# Show line numbers
grep -n "pattern" file

# Regular expressions
grep "^start" file      # Lines starting with
grep "end$" file        # Lines ending with
grep "[0-9]" file       # Contains number
```

### Advanced: awk and sed

```bash
# Extract column
awk '{print $1}' file

# Search and replace
sed 's/old/new/g' file

# In-place edit
sed -i 's/old/new/g' file
```

---

## 🔗 Next Steps

1. Complete [Labs](./LABS.md)
2. Review [Interview Questions](./INTERVIEW.md)
