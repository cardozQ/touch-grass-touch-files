# 📚 Filesystem Engineering Roadmap
*A complete roadmap for becoming a Filesystem Engineer and eventually designing and implementing your own filesystem.*

> **Goal**
>
> Build a deep understanding of filesystem internals—from storage hardware to production-grade filesystems—and finish by creating a custom filesystem with advanced features.

---

# Roadmap Overview

```text
Computer Architecture
        │
        ▼
Storage Hardware
        │
        ▼
Operating Systems
        │
        ▼
Unix Filesystem Design
        │
        ▼
Educational Filesystems
        │
        ▼
Build Your First Filesystem
        │
        ▼
Production Filesystems
        │
        ▼
VFS Layer
        │
        ▼
Filesystem Algorithms
        │
        ▼
Research Papers
        │
        ▼
Advanced Features
        │
        ▼
Design Your Own Filesystem
```

---

# Phase 0 — Prerequisites (2–3 Weeks)

## Objectives

Build a strong foundation in operating systems and systems programming.

## Topics

- C Programming
- Pointers
- Memory Management
- Structs
- Bit Manipulation
- File Descriptors
- Virtual Memory
- Processes
- Threads
- System Calls

---

## Books

### Operating Systems

- Operating Systems: Three Easy Pieces (OSTEP)
- xv6 Book

---

## OSTEP Chapters

- Processes
- Address Spaces
- Virtual Memory
- Persistence
- File Systems
- Directories
- Crash Consistency

---

## Goal

By the end of this phase you should understand:

- What happens during open()
- What happens during read()
- What happens during write()
- Difference between user space and kernel space

---

# Phase 1 — Storage Hardware (2 Weeks)

Before learning filesystems, understand the hardware they manage.

---

## Topics

### HDD

- Platters
- Tracks
- Sectors
- Seek Time
- Rotational Latency

### SSD

- NAND Flash
- Pages
- Blocks
- Erase-before-write
- Wear Leveling
- Flash Translation Layer (FTL)

### NVMe

- Queues
- DMA
- Submission Queue
- Completion Queue

---

## Learn

- Sequential IO
- Random IO
- Write Amplification
- Read Amplification
- TRIM
- Garbage Collection

---

## Goal

Understand:

**Why filesystems are designed differently for HDDs and SSDs.**

---

# Phase 2 — Unix Filesystem Fundamentals (3 Weeks)

Learn classic Unix filesystem design.

---

## Topics

- Inodes
- Superblock
- Directory Entries
- Hard Links
- Symbolic Links
- File Permissions
- Bitmaps
- Block Groups

---

## Learn

```text
Disk

+----------------------+
| Superblock           |
+----------------------+
| Block Bitmap         |
+----------------------+
| Inode Bitmap         |
+----------------------+
| Inode Table          |
+----------------------+
| Data Blocks          |
+----------------------+
```

---

## Goal

Understand how a filesystem is organized on disk.

---

# Phase 3 — Read xv6 Filesystem (3–4 Weeks)

Repository

https://github.com/mit-pdos/xv6-riscv

---

## Read Order

```
kernel/fs.h
↓

kernel/fs.c
↓

kernel/bio.c
↓

kernel/file.c
↓

kernel/log.c
```

---

## Files

### fs.h

Learn

- Superblock
- Inode
- Directory Entry

---

### fs.c

Study

```
readsb()
balloc()
bfree()

ialloc()

iget()

bmap()

readi()

writei()

dirlookup()

dirlink()

namex()
```

---

### bio.c

Learn

```
bread()
bwrite()
brelse()
```

Buffer Cache

---

### file.c

Learn

```
fileread()
filewrite()
fileclose()
```

---

### log.c

Learn

- Journaling
- Transactions
- Crash Recovery

---

## Goal

Understand every line of filesystem code.

---

# Phase 4 — Build Your First Filesystem (4–6 Weeks)

Implement a simple filesystem.

---

## Features

- mkfs
- mount
- create
- mkdir
- ls
- open
- close
- read
- write
- delete

---

## Layout

```
Superblock
↓

Block Bitmap
↓

Inode Bitmap
↓

Inode Table
↓

Data Blocks
```

---

## Implement

```
alloc_block()

free_block()

alloc_inode()

free_inode()

lookup()

create()

read()

write()

delete()
```

---

## Goal

Create files on a disk image.

Restart the program.

Files should still exist.

---

# Phase 5 — Study Production Filesystems (2 Months)

---

## Linux ext2

Repository

https://github.com/torvalds/linux

Read

```
fs/ext2/

super.c

inode.c

dir.c

namei.c

balloc.c

ialloc.c
```

---

## FreeBSD UFS

Repository

https://github.com/freebsd/freebsd-src

Read

```
sys/ufs/

ufs_lookup.c

ufs_inode.c

ufs_alloc.c

ufs_vnops.c
```

---

## Goal

Compare Linux and BSD filesystem design.

---

# Phase 6 — Virtual File System (3 Weeks)

Learn how operating systems support multiple filesystems.

---

## Linux

Read

```
fs/namei.c

fs/inode.c

fs/open.c

fs/read_write.c

fs/file_table.c

fs/super.c
```

---

## FreeBSD

Read

```
sys/kern/

vfs_lookup.c

vfs_mount.c

vfs_subr.c

vfs_default.c

vfs_vnops.c
```

---

## Goal

Understand:

```
Application

↓

VFS

↓

Filesystem

↓

Storage Driver

↓

Disk
```

---

# Phase 7 — Filesystem Algorithms (1–2 Months)

Study algorithms used in production filesystems.

---

## Topics

### Allocation

- First Fit
- Best Fit
- Buddy Allocator

---

### Metadata

- Bitmaps
- Extents
- B+ Trees
- Red Black Trees

---

### Caching

- Buffer Cache
- Page Cache
- Read Ahead
- Write Behind

---

### Crash Consistency

- Journaling
- Write Ahead Logging
- Soft Updates
- Copy-on-Write

---

### Performance

- Delayed Allocation
- Extent Allocation
- Fragmentation
- Locality

---

## Goal

Understand why production filesystems perform well.

---

# Phase 8 — Read Research Papers

Read classic filesystem papers.

---

## Papers

### Fast File System (FFS)

The Berkeley Fast File System

---

### Log Structured File System (LFS)

Rosenblum & Ousterhout

---

### Soft Updates

Marshall Kirk McKusick

---

### WAFL

NetApp

---

### ZFS

Sun Microsystems

---

### Btrfs

Oracle

---

### NOVA

Persistent Memory Filesystem

---

### SplitFS

Persistent Memory Filesystem

---

## Goal

Learn how filesystem research evolved over the last 40 years.

---

# Phase 9 — Build Advanced Features

Extend your filesystem.

---

## Implement

### Buffer Cache

---

### Page Cache

---

### Journaling

---

### Extents

---

### B+ Trees

---

### Snapshots

---

### Copy-on-Write

---

### Checksums

---

### Compression

---

### Encryption

---

### Quotas

---

### Online fsck

---

## Goal

Turn your educational filesystem into a modern filesystem.

---

# Phase 10 — Study Modern Filesystems

Study production implementations.

---

## Linux

- ext4
- XFS
- Btrfs
- F2FS

---

## BSD

- UFS2
- ZFS

---

## Apple

- APFS

---

## Microsoft

- NTFS
- ReFS

---

## Embedded

- LittleFS
- SPIFFS

---

## Compare

- Metadata
- Journaling
- Allocation
- Recovery
- Compression
- Snapshots
- Copy-on-Write
- Scalability

---

# Build Projects Along the Way

## Beginner

- Hex Dump Viewer
- Disk Image Reader
- Block Visualizer

---

## Intermediate

- FAT32 Reader
- ext2 Reader
- Read-only Filesystem

---

## Advanced

- FUSE Filesystem
- Memory Filesystem
- Journaling Filesystem
- Copy-on-Write Filesystem

---

## Expert

- ext2 Clone
- ext4-inspired Filesystem
- Network Filesystem
- Distributed Filesystem

---

# Six-Month Learning Plan

## Month 1

- OSTEP
- Storage Hardware
- Unix Filesystems
- xv6 Filesystem

---

## Month 2

Build a Toy Filesystem

---

## Month 3

Linux ext2

FreeBSD UFS

---

## Month 4

Linux VFS

FreeBSD VFS

Crash Recovery

Buffer Cache

---

## Month 5

Research Papers

Advanced Algorithms

Implement Journaling

---

## Month 6

Study

- ext4
- XFS
- Btrfs
- ZFS

Begin designing your own filesystem.

---

# Filesystem Engineer's Notebook

Keep a notebook with these sections:

```
Filesystem Notebook
│
├── Storage Hardware
├── Unix Concepts
├── Inodes
├── Superblocks
├── Directories
├── Allocation Algorithms
├── Buffer Cache
├── Page Cache
├── Journaling
├── VFS
├── Linux Notes
├── FreeBSD Notes
├── Research Papers
├── Design Ideas
├── Performance Benchmarks
└── Experiments
```

Document everything you learn. Draw diagrams for on-disk layouts, explain algorithms in your own words, and keep notes on trade-offs between different filesystem designs.

---

# Recommended GitHub Repositories

| Project | Purpose |
|----------|---------|
| https://github.com/mit-pdos/xv6-riscv | Educational filesystem |
| https://github.com/torvalds/linux | Linux ext2/ext4/VFS |
| https://github.com/freebsd/freebsd-src | FreeBSD UFS/VFS |
| https://github.com/littlefs-project/littlefs | Embedded filesystem |
| https://github.com/libfuse/libfuse | Userspace filesystems |
| https://github.com/sysprog21/simplefs | Simple Linux filesystem module |

---

# Recommended Books

- Operating Systems: Three Easy Pieces (OSTEP)
- xv6: A Simple, Unix-like Teaching Operating System
- The Design and Implementation of the FreeBSD Operating System
- Understanding the Linux Kernel
- Linux Kernel Development (Robert Love)
- Linux Device Drivers (for VFS interactions)
- File System Forensic Analysis (Brian Carrier)
- Advanced Programming in the UNIX Environment (APUE)

---

# Final Goal

By the end of this roadmap, you should be able to:

- Explain how filesystems work from first principles.
- Read and understand Linux and FreeBSD filesystem source code.
- Implement a complete filesystem from scratch.
- Design efficient on-disk data structures.
- Add advanced features such as journaling, snapshots, extents, and copy-on-write.
- Understand the trade-offs behind modern filesystems like ext4, XFS, ZFS, APFS, and Btrfs.
- Confidently contribute to open-source filesystem projects or pursue research in storage systems.
