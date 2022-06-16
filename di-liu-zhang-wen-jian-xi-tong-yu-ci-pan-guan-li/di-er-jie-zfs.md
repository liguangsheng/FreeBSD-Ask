# 第二节 ZFS

## 使用建议

- 最好不要在内存少于 1G 的机器上使用 ZFS。因为 ZFS 大约 每 1TB 硬盘空间需要消耗 1GB 内存。
- 最好不要在非 64 位系统上使用 ZFS。
- 为了提高机械硬盘随机读能力，可设置 `vfs.zfs.prefetch_disable=1`。
- 为了避免 ZFS 吃掉太多内存，最好要设置 `vfs.zfs.arc_max="?"`，例如：1024 M。
- 如果要复制某个文件系统，可以用 `zfs send/recv`，这样还能通过 ssh 跨网络传输。
- 推荐使用固态硬盘，使用 SSD 可以改善 ZFS 随机读能力，并且 ZFS 这种写时复制的文件系统也有益于 SSD 寿命。

## 注意事项

- ZFS 并不使用`/etc/fstab`