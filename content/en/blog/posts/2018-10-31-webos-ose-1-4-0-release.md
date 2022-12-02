---
title: webOS OSE 1.4.0 Release
date: 2018-10-31
slug: webos-ose-1-4-0-release
posttype: release
toc: false
---

Key highlights of this release are as follows.

* [zram](#zram)
* [Enact framework update](#enact-framework-update)

This release also includes other component updates and bug fixes, so refer to the [release notes]({{< relref "webos-ose-1-4-0-release-notes" >}}) for a complete listing of changes.

## zram

From this release onward, webOS OSE supports zram.

**zram** is a BSP module that creates compressed RAM based block devices.

* The zram module creates RAM based block devices named `/dev/zram<id>` (\<id> = 0, 1, ...).
* Pages written to these disks are compressed and stored in memory itself.
* These disks allow very fast I/O and compression provides good amounts of memory savings.
* Statistics for individual zram devices are exported through sysfs nodes at `/sys/block/zram<id>/`.
* The `zramctl` command can set up and control zram devices.

For more information, read the kernel guide page: https://www.kernel.org/doc/Documentation/blockdev/zram.txt.

## Enact framework update

Enact framework, the web app framework for webOS OSE, has been updated from [v2.0.1](https://github.com/enactjs/enact/blob/master/CHANGELOG.md#201---2018-08-01) to [v2.2.1](https://github.com/enactjs/enact/blob/master/CHANGELOG.md#221---2018-10-09). There has been numerous improvements in terms of feature, performance, and stability. To find out more details, check the [change log](https://github.com/enactjs/enact/blob/master/CHANGELOG.md).
