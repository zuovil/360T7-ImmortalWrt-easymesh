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

适用于360T7 ARMv8 Processor rev 4 (v8l) x 2 mediatek/mt7981 ImmortalWrt 21.02-SNAPSHOT r20648-fa0b7600f5 / LuCI openwrt-21.02 branch git-23.098.38725-847bd6b

注意该插件涉及到内核，无法通过ipk安装，需要与内核一起编译后刷写固件的方式安装（[easymesh作者说的](https://www.right.com.cn/forum/thread-4118559-1-1.html)，具体能不能编译出ipk我研究一下）

~~刷写固件后可能有点小BUG，easymesh插件没有显示，如果清空浏览器缓存后刷新页面依旧没有，可能需要手动重装~~

~~解包步骤：请使用压缩软件打开sysupgrade.bin系统镜像，解压出root文件，再使用终端运行./sqfs_for_win.exe root（sqfs_for_win.exe网上搜一下就有，root为root对应的文件路径，这里简写了，取决于解压位置）。解压完成后sqfs_for_win.exe
所在文件夹下面多出来一个squashfs-root文件夹，里面就是解压的一系列文件。~~

~~手动安装步骤：打开squashfs-root文件夹，在windows文件管理器搜索easymesh将这些文件依次根据对应的目录使用winscp复制进路由器对应的目录，文件权限设置为755。然后根据[easymesh编译文件](https://github.com/shuishihan/luci-app-easymesh/blob/master/Makefile)在/usr/lib/opkg/status追加对应的安装信息。最后远程连接终端输入rm -rf /tmp/luci-*删除缓存，重建luci菜单目录，浏览器清空缓存重进页面就能看到了~~

上面的内容描述有误，就当了解一下知识了

在github的release下载这四个文件kmod-cfg80211_5.4.284+5.15.92-1-1_aarch64_cortex-a53.ipk  kmod-lib-crc16_5.4.284-1_aarch64_cortex-a53.ipk  kmod-batman-adv_5.4.284+2021.1-11_aarch64_cortex-a53.ipk  luci-app-easymesh_2.0_all.ipk 并依此安装，前面三个文件是前置依赖，easymesh 需要这三个依赖才能顺利完成安装。安装完成清空浏览器缓存刷新页面后在菜单网络那一栏可以找到

