# Ubuntu 16.04 LTS 安装完成后

## 1. 设置root密码

```shell
sudo passwd
```

## 2. 安装 Shadowsocks Qt5

- 安装

```shell
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt-get update
sudo apt-get install shadowsocks-qt5
```

- 开机自启

```shell
# 启动应用程序首选项
gnome-session-properties

# 弹出的窗口中依次进行如下步骤：
# 添加 -> 编辑启动程序(命令处填写: /usr/bin/ss-qt5) -> 保存(关闭)
```

## 3. 安装 gdebi

```shell
sudo apt-get install gdebi
```

## 4. 卸载预装软件

```shell
sudo apt-get purge libreoffice-common unity-webapps-common
sudo apt-get purge thunderbird totem rhythmbox brasero simple-scan sudo apt-get purge gnome-mahjongg aisleriot onboard gnome-mines
sudo apt-get purge cheese transmission-common gnome-orca
sudo apt-get purge webbrowser-app gnome-sudoku
sudo apt-get purge landscape-client-ui-install gnome-software
sudo apt-get purge whoopsie xdiagnose empathy
sudo apt-get purge empathy-common ubuntuone*
```

## 5. 安装Lantern

> 下载地址：https://github.com/getlantern/lantern/releases/tag/latest

```shell
sudo gdebi lantern-installer-64-bit.deb
```

## 6. 解压 .tar.gz

```shell
tar -xzvf %filename%.tar.gz
```

## 7. 修改 /opt 目录权限

```shell
sudo chmod -R 777 /opt
```

## 8. 配置JDK环境变量

```shell
sudo gedit ~/.bashrc
```

> 在 `.bashrc` 文件中添加一下两行语句

```js
export JAVA_HOME=/opt/Java
export PATH=$PATH:${JAVA_HOME}/bin
```

## 9. 安装Git

```shell
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
# 上面两步可省略
sudo apt install git
```

## 10. 安装Android Studio

> 参考文档: https://developer.android.google.cn/studio/install.html

## 11. 检测到系统程序出现问题

```shell
sudo gedit /etc/default/apport
```

> 设置 enabled=0

## 12. 安装YaHei Consolas Hybrid字体

> 宋体: simsunb.ttf 同理

> Consolas是一款专门为编程人员设计的字体，Consolas雅黑混合版包含中文和英文字体，使编程人员在编写代码的时候看起来更舒服

> 下载地址: https://github.com/yakumioto/YaHei-Consolas-Hybrid-1.12

```shell
cd /usr/share/fonts/truetype/
# 新建文件夹
sudo mkdir yahei-consolas-hybrid
# 复制到该文件夹
sudo cp %YaHei Consolas Hybrid 1.12.ttf% /usr/share/fonts/truetype/yahei-consolas-hybrid
# 修改字体文件权限
cd /usr/share/fonts/truetype/yahei-consolas-hybrid
sudo chmod 644 YaHei Consolas Hybrid 1.12.ttf
# 安装字体
# 1. 创建字体的fonts.scale文件，它用来控制字体旋转缩放
sudo mkfontscale
# 2. 创建字体的fonts.dir文件，它用来控制字体粗斜体产生
sudo mkfontdir
# 3. 建立字体缓存信息，也就是让系统认识该字体
sudo fc-cache -fv
```

## 13. 安装微软字体

```shell
sudo apt-get install ttf-mscorefonts-installer
```

> 使用 Tab 键进行切换，依次点击 Yes 、OK ，使用 Enter 键 确定

```shell
# 更新字体缓存
sudo fc-cache -f -v
```

## 14. 安装 unity-tweak-tool

```shell
sudo apt-get install unity-tweak-tool
```

## 15. 安装 SMPlayer

```shell
sudo add-apt-repository ppa:rvm/smplayer 
sudo apt-get update 
sudo apt-get install smplayer smplayer-themes smplayer-skins 
```

## 16. 卸载Shadowsocks-Qt5

```shell
sudo apt-get purge shadowsocks-qt5
cd /etc/apt/sources.list.d
sudo add-apt-repository -r ppa:hzwhuang/ss-qt5
sudo apt-get update
locate hzwhuang # locate hzwhuang*
sudo rm -rf hz* # delete sources.list
sudo updatedb # update locate db
locate hzwhuang # check are deleted ?
```

### 17. 卸载 electron-ssr

```shell
sudo dpkg -P electron-ssr
```

> 使用了代理后， `terminal` 中使用 `git push` 时会出现问题
>
> 可通过设置 git 全局代理来解决
>
> ```shell
> git config --global http.proxy 'socks5://127.0.0.1:1080'
> ```

### 18. 安装Kazam

```shell
sudo apt install kazam
```

### 19. 删除PPA源

```shell
sudo add-apt-repository -r ppa:user/ppa-name
```

然后进入 /etc/apt/sources.list.d 目录，将相应 ppa 源的保存文件删除。

```shell
sudo apt-get update
```

### 20. 安装OBS Studio

```shell
sudo apt-get install ffmpeg
sudo add-apt-repository ppa:obsproject/obs-studio
sudo apt-get update
sudo apt-get install obs-studio
```

## 21. 安装OpenShot

```shell
sudo add-apt-repository ppa:openshot.developers/ppa
sudo apt-get update
sudo apt-get install openshot-qt
```

## 22. 安装FFmpeg

- 下载源码: [源码链接](http://ffmpeg.org/download.html#get-sources)

- 解压

  ```shell
  tar -xvjf ffmpeg-4.0.tar.bz2
  ```

- 安装 yasm

  ```shell
  sudo apt-get install yasm
  ```

- 运行自动配置

  ```shell
  ./configure --enable-shared --prefix=/usr/local/ffmpeg
  ```

- 编译

  ```shell
  sudo make
  ```

- 安装

  ```shell
  sudo make install
  ```

- 配置环境变量

  ```shell 
  sudo vim ~/.bashrc

  # 添加下面这一行
  export PATH=$PATH:/usr/local/ffmpeg/bin

  # 使其立即生效
  source ~/.bashrc
  ```

- 其他

  - 为了方便编程
    1. 把 `/usr/local/ffmpeg/lib` 中的 *libavcodec.so*  *libavformat.so* *libavutil.so* 复制到 `/usr/lib` 中
    2. 把 `/usr/local/ffmpeg/include` 中的所有文件复制到 `/usr/include` 目录下

- 遇到问题

  - **ffmpeg: error while loading shared libraries: libavdevice.so.58: cannot open shared object file: No such file or directory**

    解决: 

    ```shell
    sudo find / -name "libavdevice.so.58"
    #可以得到文件在 /usr/local/ffmpeg/lib 目录下
    # 然后在 /etc/ld.so.conf 文件中添加一行
    /usr/local/ffmpeg/lib
    # 然后使用执行如下命令
    sudo ldconfig
    ```

  - **对‘xx_xx_xx’未定义的引用**

    解决:

    ```shell
    # 配置PKG_CONFIG_PATH环境变量即可
    export PKG_CONFIG_PATH=/usr/local/ffmpeg/lib/pkconfig
    # 然后使环境变量立即生效
    source ~/.bashrc
    ```

    ​