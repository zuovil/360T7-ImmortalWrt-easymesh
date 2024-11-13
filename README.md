## OpenWrt firmware for 360T7

Auto build OpenWrt firmware for 360T7 via GitHub Actions

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/sagehou/360T7-ImmortalWrt?style=for-the-badge&label=Download)](https://github.com/sagehou/360T7-ImmortalWrt/releases/latest)

| Default ip | Default user | Default password |
| --- | --- | --- | 
| 192.168.233.1 | root | - |

## Main Functions

- ipv6 support
- zerotier
- wireguard
- passwall
- openclash
- v2raya
- uPnP
- ddns-go
- wake-on-lan
- easymesh

fork自[sagehou](https://github.com/sagehou/360T7-ImmortalWrt)
easymesh插件加入编译参考了[shuishihan](https://github.com/shuishihan/Actions-rax3000m-emmc)的配置
适用于360T7
刷写固件后可能有点小BUG，easymesh插件没有显示，可能需要手动重装
解包步骤：请使用压缩软件打开sysupgrade.bin系统镜像，解压出root文件，再使用终端运行./sqfs_for_win.exe root（sqfs_for_win.exe网上搜一下就有，root为root对应的文件路径，这里简写了，取决于解压位置）。解压完成后sqfs_for_win.exe
所在文件夹下面多出来一个squashfs-root文件夹，里面就是解压的一系列文件。windows搜索easymesh依次根据对应的目录使用winscp复制进对应的目录，文件权限设置为755。最后远程连接终端输入rm -rf /tmp/luci-*删除缓存，重建luci菜单目录，浏览器清空缓存重进页面就能看到了

