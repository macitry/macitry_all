# Twincat注意点

* twinCat底部齿轮红色和黄色一般出现在twincatservice卡死的情况，比如说内存溢出，除零啊什么的，灰色一般出现在服务无法启动的情况
* Empty PLC Project创建出来的模板不包含默认库文件、主程序、PLC task等，一般用于创建自定义库文件。
* 对于开机自启动:
WinCE不需要勾上AUTO LOGON ；
WINXP 、WIN7 、 WIN10需要勾上AUTO LOGON，并输入对应用户密码，默认出厂用户名：==Administrator== 密码：==1==
* 代码输入提示功能：工具——>选项——>TwinCAT——>PLC Environment——>Smart coding
勾选(1)键入点号(.)之后列出组件;(2)键入时立即列出组件
* MC_Jog默认的mode是MC_JOGMODE_STANDARD_SLOW；在此模式下，轴会以axis--parameter属性选项卡里设置的默认速度运行。如果想要手动改变velocity引脚并生效，则需要把模式改成MC_JOGMODE_CONTINOUS，并重新触发功能块
* override表示给定速度与实际速度的比值，即实际速度=给定速度*速比，如果写入0轴是不转的。MC_power功能块的override引脚也是同理。
* NC报警可以通过MC_reset或者是NC-online中的复位按钮进行复位
