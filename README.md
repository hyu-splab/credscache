# CredsCache: Credential Caching Scheme for OverlayFS in Linux

CredsCache is a caching scheme proposed to improve the scalability and performance of OverlayFS, a Linux kernel driver for Docker containers. This caching scheme addresses the overhead caused by contention in updating a shared reference counter for the mounter’s credentials, which limits the scalability of OverlayFS.

In CredsCache, a per-process cached version of the mounter's credentials is maintained, allowing each process to perform credential overriding and reverting using its own cached version without updating the shared reference counter. This significantly reduces contention and improves scalability.


# Quick Install Guide :

CredsCache (main src: fs/overlayfs) 

```bash
sudo make -j $(nproc)
sudo make INSTALL_MOD_STRIP=1 modules_install &&sudo make install
```

* Reboot and select Linux 5.15.6-CredsCache
* Please use the filesystem benchmarks (e.g. FxMark) on the Docker instance to measure the performance of CredsCache

