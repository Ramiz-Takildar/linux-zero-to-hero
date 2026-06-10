# Chapter 2 Labs: Files & Directories

## Lab 2.1: File Operations and Types

```bash
# Create test files
cd ~
mkdir -p linux-labs/chapter-02
cd linux-labs/chapter-02

# Different file types
touch regular.txt
mkdir mydir
ln -s regular.txt symlink.txt

# Check types
ls -l
file regular.txt
file mydir
file symlink.txt
stat regular.txt
```

## Lab 2.2: find Command

```bash
# Setup
mkdir -p test/{a,b,c}
touch test/file.txt
touch test/a/file.txt
touch test/b/file.txt

# Find exercises
find test -name "*.txt"
find test -type d
find test -type f
find . -name "*.txt" -exec ls -lh {} \;

# Cleanup
rm -rf test
```

## Lab 2.3: Links

```bash
# Hard link
touch original.txt
echo "test content" > original.txt
ln original.txt hardlink.txt

# Check same inode
ls -li original.txt hardlink.txt

# Remove original
rm original.txt
cat hardlink.txt  # Still works!

# Symlink
touch newfile.txt
ln -s newfile.txt symlink.txt
ls -l symlink.txt

# Cleanup
rm newfile.txt hardlink.txt symlink.txt
```

## Lab 2.4: Compression

```bash
# Create test archive
mkdir archivetest
for i in {1..5}; do echo "File $i" > archivetest/file$i.txt; done

# Create tar.gz
tar -czvf archive.tar.gz archivetest/

# Extract
mkdir extract
tar -xzvf archive.tar.gz -C extract/

# Verify
ls extract/archivetest/

# Cleanup
rm -rf archivetest extract archive.tar.gz
```

## Verification

- [ ] Used find to locate files
- [ ] Created hard and symbolic links
- [ ] Created and extracted archives
- [ ] Used grep to search content
