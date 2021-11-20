# 第一节 Fcitx 输入法框架

## FreeBSD Fcitx 输入法框架设置（4.X）

#### 注意：该教程仅在KDE5 下测试通过。 <a href="zhu-yi-gai-jiao-cheng-jin-zai-kde5-xia-ce-shi-tong-guo" id="zhu-yi-gai-jiao-cheng-jin-zai-kde5-xia-ce-shi-tong-guo"></a>

在.cshrc 和/etc/csh.cshrc 中进行如下配置，此配置可以解决部分窗口fcitx 无效的问题。

setenv QT4\_IM\_MODULE fcitx

setenv GTK\_IM\_MODULE fcitx

setenv QT\_IM\_MODULE fcitx

setenv GTK2\_IM\_MODULE fcitx

setenv GTK3\_IM\_MODULE fcitx

setenv XMODIFIERS @im=fcitx

在.cshrc 和/etc/csh.cshrc 中进行下面两行配置可以解决终端无法输入中文和无法显示中文的问题。

setenv LANG zh\_CN.UTF-8

setenv MM\_CHARSET zh\_CN.UTF-8

接Fcitx 输入法补充：

要想终端不乱码还需要

setenv LANG zh\_CN.UTF-8

setenv LC\_CTYPE zh\_CN.UTF-8

setenv LC\_ALL zh\_CN.UTF-8

## Fcitx5

#### 注意：该教程仅在KDE5 下测试通过。 <a href="zhu-yi-gai-jiao-cheng-jin-zai-kde5-xia-ce-shi-tong-guo" id="zhu-yi-gai-jiao-cheng-jin-zai-kde5-xia-ce-shi-tong-guo"></a>

textproc/fcitx5\
textproc/fcitx5-qt\
textproc/fcitx5-gtk\
textproc/fcitx5-configtool\
chinese/fcitx5-rime\
…

　　可通过 ports 安装。环境变量取决于你的窗口管理器和桌面以及 shell 。经测试不支持 slim，可能是配置问题。SDDM 可用。

　　自动启动：\
cp /usr/local/share/applications/fcitx.desktop \~/.config/autostart/

　　在.cshrc 和 /etc/csh.cshrc 中进行如下配置，此配置可以解决部分窗口 fcitx 无效以及无法输入显示中文的问题。\
setenv QT4\_IM\_MODULE fcitx\
setenv GTK\_IM\_MODULE fcitx\
setenv QT\_IM\_MODULE fcitx\
setenv GTK2\_IM\_MODULE fcitx\
setenv GTK3\_IM\_MODULE fcitx\
setenv XMODIFIERS @im=fcitx\
setenv LANG zh\_CN.UTF-8\
setenv MM\_CHARSET zh\_CN.UTF-8

　　在 root 用户下 rime 不会自动被添加到输入法，需要手动添加完成初始化！

　　SLIM 窗口下会提示IBUS 找不到……疑似bug。