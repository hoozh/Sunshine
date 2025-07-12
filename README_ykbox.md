## 简介

基于 sunshine 做了微小的改动

* 禁用托盘图标

## 编译

### 官方教程:

https://github.com/LizardByte/Sunshine/blob/master/docs/building.md

### Windows
1. 安装  MSYS2，启动 MSYS2 UCRT64 终端
2. 更新软件包
```
pacman -Syu
```

3. 安装依赖

```
dependencies=(
  "git"
  "mingw-w64-ucrt-x86_64-boost"  # Optional
  "mingw-w64-ucrt-x86_64-cmake"
  "mingw-w64-ucrt-x86_64-cppwinrt"
  "mingw-w64-ucrt-x86_64-curl-winssl"
  "mingw-w64-ucrt-x86_64-doxygen"  # Optional, for docs... better to install official Doxygen
  "mingw-w64-ucrt-x86_64-graphviz"  # Optional, for docs
  "mingw-w64-ucrt-x86_64-MinHook"
  "mingw-w64-ucrt-x86_64-miniupnpc"
  "mingw-w64-ucrt-x86_64-nodejs"
  "mingw-w64-ucrt-x86_64-nsis"
  "mingw-w64-ucrt-x86_64-onevpl"
  "mingw-w64-ucrt-x86_64-openssl"
  "mingw-w64-ucrt-x86_64-opus"
  "mingw-w64-ucrt-x86_64-toolchain"
)
pacman -S "${dependencies[@]}"
```

4. boost 需要手动下载并降级安装

下载地址：https://repo.msys2.org/mingw/ucrt64/

```bash
pacman -U /var/cache/pacman/pkg/mingw-w64-ucrt-x86_64-boost-1.87.0-3-any.pkg.tar.zst
```

5. 克隆代码并切换到 ykbox 分支

```bash
git clone git@github.com:hoozh/Sunshine.git --recurse-submodules
git checkout -b ykbox origin/ykbox
```

```bash
cd Sunshine
mkdir build
```

6. 编译

```bash
cmake -B build -G Ninja -S . -DSUNSHINE_ENABLE_TRAY=OFF
ninja -C build
```

7. 打包

安装包

```bash
cpack -G NSIS --config ./build/CPackConfig.cmake
```

便携包

```bash
 cpack -G ZIP --config ./build/CPackConfig.cmake
```
