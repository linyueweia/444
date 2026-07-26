# iStoreOS NanoPC-T4

基于 [iStoreOS 官方源码](https://github.com/istoreos/istoreos) 为 FriendlyElec NanoPC-T4 (RK3399) 编译固件。

## 特点

- 源码：iStoreOS 官方 `istoreos-24.10` 分支
- 编译：标准 OpenWrt 编译流程（`make defconfig` + `make`）
- 不依赖任何第三方仓库或自定义脚本
- 在线升级：已包含 `luci-app-sysupgrade`

## 编译流程

```bash
# 1. 克隆官方源码
git clone https://github.com/istoreos/istoreos.git -b istoreos-24.10
cd istoreos

# 2. 更新 feeds
./scripts/feeds update -a
./scripts/feeds install -a

# 3. 配置（选 Rockchip > NanoPC-T4）
make menuconfig

# 4. 编译
make download -j8
make -j$(nproc)
```

## 默认配置

| 项目 | 值 |
|------|-----|
| IP | `http://192.168.100.1` |
| 用户名 | `root` |
| 密码 | 空 |
| 网口 | 单网口 = LAN |

## 自动编译

GitHub Actions 每周五北京时间 08:00 自动编译，固件发布在 Release 页面。