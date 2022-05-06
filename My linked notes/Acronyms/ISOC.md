Internet Society
1.  CPU registers and cache memory (including cache on disk controllers, GPUs, and so on).
2.  Contents of nonpersistent system memory (RAM), including routing table, ARP cache, process table, kernel statistics.
3.  Data on persistent mass storage devices (HDDs, SSDs, and flash memory devices):

-   Partition and file system blocks, slack space, and free space.
-   System memory caches, such as swap space/virtual memory and hibernation files.
-   Temporary file caches, such as the browser cache.
-   User, application, and OS files and directories.

4.  Remote logging and monitoring data.
5.  Physical configuration and network topology.
6.  Archival media and printed documents.

The Windows registry is mostly stored on disk, but there are keys—notably HKLM\Hardware—that only ever exist in memory. The contents of the registry can be analyzed via a memory dump.