# 国内系统常用配置

### Python更改PyPI源地址以加快包的下载速度
```
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

### 🧩 Fcitx5 中文输入法最小安装指南（Ubuntu / Debian）

本教程介绍如何在 Linux 系统中安装并配置 **Fcitx5 中文输入法**，包含最小可用配置与基础优化。

---

#### 一、安装基础组件

Fcitx5 需要以下三部分：

- Fcitx5 主程序
- 中文输入法引擎
- 图形界面前端

直接使用 `apt` 安装：

```bash
sudo apt update

sudo apt install fcitx5 \
fcitx5-chinese-addons \
fcitx5-frontend-gtk4 fcitx5-frontend-gtk3 fcitx5-frontend-gtk2 \
fcitx5-frontend-qt5
```
#### 二、安装中文词库（可选但推荐）
使用维基百科拼音词库提升输入体验：
```bash
# 下载词库
wget https://github.com/felixonmars/fcitx5-pinyin-zhwiki/releases/download/0.2.4/zhwiki-20220416.dict

# 创建目录
mkdir -p ~/.local/share/fcitx5/pinyin/dictionaries/

# 移动文件
mv zhwiki-20220416.dict ~/.local/share/fcitx5/pinyin/dictionaries/

```

#### 三、设置默认输入法
```bash
im-config
```
在弹出界面中选择 ```Fcitx 5 ```

#### 四、配置环境变量
将以下内容添加到 ~/.bash_profile（推荐，仅当前用户生效）：
```
export XMODIFIERS=@im=fcitx
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
```
也可以写入写入此配置的文件为系统级的 /etc/profile

#### 设置开机自启动
Fcitx5 默认不会自动启动，需要手动添加：
```bash
sudo apt install gnome-tweaks
```
操作步骤：
打开 Tweaks（优化工具）
进入「启动应用程序」
添加 fcitx5

#### 自定义主题（可选）
在 GitHub 搜索 Fcitx5 主题
```
https://github.com/thep0y/fcitx5-themes-candlelight
```
