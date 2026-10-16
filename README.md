# CANas

安装包与自动更新分发仓（源码与 CI 在自建 Gitea，本仓只放 Releases）。

## 安装

### Windows

下载 Release 中的 `*.msi` 双击安装。应用内可自动更新（更新时有一次 UAC 确认）。

### Linux（AppImage）

```bash
sudo apt install libfuse2        # Debian/Ubuntu 首次需要；Arch 用 sudo pacman -S fuse2
bash install-appimage.sh CANas-X.Y.Z-x86_64.AppImage   # 会顺带装 CANalyst-II 的 udev 规则（需 sudo）
```

安装后应用内自动更新（原地替换 `~/Applications/CANas.AppImage`）。
也可用 Gear Lever / AppImageLauncher 等工具管理。
存量 pacman 包用户请先 `pacman -R canas` 再按上述方式安装一次。

## 自动更新

客户端启动时检查 `releases/latest/download/latest.json`，有新版本会弹窗提示，
确认后自动下载安装并重启。更新包经 minisign 签名，本仓被篡改也无法通过校验。
