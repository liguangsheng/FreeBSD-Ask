# 第二节 Ibus 输入法框架

#### 注意：该教程仅在XFCE 桌面下测试通过。不适用于KDE5。 <a href="zhu-yi-gai-jiao-cheng-jin-zai-xfce-zhuo-mian-xia-ce-shi-tong-guo-bu-kuo-yong-yu-kde5" id="zhu-yi-gai-jiao-cheng-jin-zai-xfce-zhuo-mian-xia-ce-shi-tong-guo-bu-kuo-yong-yu-kde5"></a>

　　ibus输入法框架配置.xinitrc 中增加\
XIM=ibus; export XIM\
GTK\_IM\_MODULE=ibus; export GTK\_IM\_MODULE\
QT\_IM\_MODULE=xim; export QT\_IM\_MODULE\
XMODIFIERS=’@im=ibus’; export XMODIFIERS\
XIM\_PROGRAM=”ibus-daemon”; export XIM\_PROGRAM\
XIM\_ARGS=”–daemonize –xim”; export XIM\_ARGS

　　.cshrc 中增加\
setenv LANG zh\_CN.UTF-8\
setenv LC\_CTYPE zh\_CN.UTF-8\
setenv LC\_ALL zh\_CN.UTF-8\
setenv XMODIFIERS @im=ibus

　　.profile 中添加\
export LC\_ALL=zh\_CN.UTF-8