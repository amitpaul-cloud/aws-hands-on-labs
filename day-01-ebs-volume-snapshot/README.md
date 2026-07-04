# Day 1 - Amazon EBS Volume & Snapshot

## Objective

Learn how Amazon EBS volumes work and how snapshots can be used to recover data.

---

## Services Used

- Amazon EC2
- Amazon EBS
- Amazon Linux 2023
- Windows Server 2022

---

## Practical Steps

### Linux

- Created a new EBS volume
- Attached the volume to EC2
- Verified using `lsblk`
- Formatted the volume using ext4
- Mounted the volume
- Created a text file
- Verified the file
- Created an EBS Snapshot
- Deleted the original volume
- Created a new volume from the snapshot
- Attached the restored volume
- Mounted the volume
- Verified successful data recovery

---

### Windows

- Created a new EBS volume
- Initialized the disk
- Formatted with NTFS
- Assigned a drive letter
- Created a sample text file
- Created an EBS Snapshot
- Deleted the original volume
- Created a new volume from the snapshot
- Attached the restored volume
- Verified successful file recovery

---

## Key Learning

- EBS is block storage.
- A new volume must be formatted before use.
- Linux requires mounting before files can be accessed.
- Snapshots are incremental.
- Data can be restored even after the original volume is deleted.

---

## Commands Used

```bash
lsblk
mkfs.ext4 /dev/nvme1n1
mkdir /data
mount /dev/nvme1n1 /data
df -h
echo "AWS Practice" > data.txt
cat data.txt
```

---

## Result

Successfully restored data from an EBS Snapshot after deleting the original EBS volume.

---

**Status:** Completed
