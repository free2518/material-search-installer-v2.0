
增加增量扫描功能的 MaterialSearch 安装器
# MaterialSearch MacOS 一键安装脚本

这是一个用于在 MacOS（特别是 M1/M2/M3 芯片）上一键安装 [MaterialSearch](https://github.com/IuvenisSapiens/MaterialSearch) 的脚本。

## 使用方法

清理旧的安装:
rm -rf ~/MaterialSearch

打开终端，复制并运行以下命令：

```
curl -fsSL https://raw.githubusercontent.com/free2518/material-search-installer-v2.0/main/install_material_search.sh | bash
```

## 功能特点

- 自动安装所需依赖（Homebrew、Python、ffmpeg）
- 自动配置 Python 虚拟环境
- 自动设置启动脚本
- 完整的错误处理
- 友好的安装进度显示
- 支持多种模型切换（base/large/fast）

## 安装后使用

安装完成后，你可以：

1. 进入安装目录：
```
cd ~/MaterialSearch
```

2. 启动程序：
```
./start.sh
```
启动时可以选择是否切换模型：
- chinese-clip-vit-base-patch16 (默认，平衡型，753MB)
- chinese-clip-vit-large-patch14 (高性能，3GB)
- chinese-clip-rn50 (快速，体积小)

3. 打开浏览器访问：`http://localhost:8085`

## 配置说明

安装完成后，配置文件位于 `~/MaterialSearch/.env`。默认配置如下：

```
ASSETS_PATH=$HOME/Pictures,$HOME/Movies
DEVICE=cpu
MODEL_NAME=OFA-Sys/chinese-clip-vit-base-patch16
```
## 增量扫描功能

如果你只想扫描新添加的目录，而不影响已有的数据：

1. 编辑 `.env` 文件
2. 添加新的扫描路径：
NEW_SCAN_PATH=/path/to/new/directory
3. 启动服务，它将只扫描新增的目录
4. 扫描完成后，可以删除 `NEW_SCAN_PATH` 这一行

例如：
- 原有路径：`ASSETS_PATH=/Users/用户名/Pictures`
- 新增路径：`NEW_SCAN_PATH=/Volumes/新硬盘/照片`

这样可以保留原有的数据，只添加新目录的内容。扫描完成后删除 `NEW_SCAN_PATH` 这行即可。


你可以根据需要修改要扫描的文件夹路径。

## 问题反馈

如果在安装过程中遇到任何问题，请在 [Issues](https://github.com/free2518/material-search-installer/issues) 页面提交问题。
