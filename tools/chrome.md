- 参考

https://support.google.com/chrome/a/answer/10686330?sjid=5121451938165816278-NC

- 关闭 Chrome 时删除所有数据类型

```
<key>ClearBrowsingDataOnExitList</key>
<dict>
 <array>
  <string>browsing_history</string>
  <string>download_history</string>
  <string>cookies_and_other_site_data</string>
  <string>cached_images_and_files</string>
  <string>password_signin</string>
  <string>autofill</string>
  <string>site_settings</string>
  <string>hosted_app_data</string>
 </array>
</dict>
```

- 验证政策是否已应用

您应用任何 Chrome 政策后，用户都必须重启 Chrome，相应设置才会生效。您可以检查用户的设备，确保政策已应用妥当。

1. 在受管理的设备上，转到 **chrome://policy**。
2. 点击**重新加载政策**。
3. 对于 **ClearBrowsingDataOnExitList** 和 **BrowsingDataLifetime**，确保**状态**显示为**正常**。
4. 对于 **ClearBrowsingDataOnExitList** 和 **BrowsingDataLifetime**，点击**展开**，确保值字段与您在政策中设置的值一致。



## 查看用户数据目录
1、在地址栏输入 chrome:version

2、随后查看谷歌浏览器保存文件的位置：个人资料路径

路径一般为：
C:\Users\Administrator\AppData\Local\Google\Chrome\User Data\Default

## chrome命令参数,及selenium的使用
目前我封装是这样配置的
options=webdriver.ChromeOptions()
options.add_argument(r’–user-data-dir=C:\Users\ditto.he\AppData\Local\Google\Chrome\User Data’)
options.add_argument(‘disable-infobars’)
options.add_argument(’–ignore-certificate-errors’)
driver=webdriver.Chrome(chrome_options=options)

注意引号后有空格

options.add_argument("–lang=" + “zh-CN”)
#切换浏览器语言

options.add_argument("–test-type", “–ignore-certificate-errors”)
#忽略 Chrome 浏览器证书错误报警提示

DesiredCapabilities capabilities = DesiredCapabilities.chrome()
capabilities.setCapability(“chrome.switches”, Arrays.asList("–start-maximized"))
options.addArguments("–test-type", “–start-maximized”,“no-default-browser-check”)
#意思好像是测试模式，最大化浏览器并且默认不检查浏览器

options.addExtensions(new File(“C:\Users\username\AppData\Local\Google\Chrome\UserData\Default\Extensions\ijaobnmmgonppmablhldddpfmgpklbfh\1.6.0_0.crx”))
#添加扩展的方法，将crx文件所在的路径添加进去



序号 参数 说明
1 --allow-outdated-plugins 不停用过期的插件。
2 --allow-running-insecure-content 默认情况下，https 页面不允许从 http 链接引用 javascript/css/plug-ins。添加这一参数会放行这些内容。
3 --allow-scripting-gallery 允许拓展脚本在官方应用中心生效。默认情况下，出于安全因素考虑这些脚本都会被阻止。
4 --disable-accelerated-video 停用 GPU 加速视频。
5 --disable-dart 停用 Dart。
6 --disable-desktop-notifications 禁用桌面通知，在 Windows 中桌面通知默认是启用的。
7 --disable-extensions 禁用拓展。
8 --disable-file-system 停用 FileSystem API。
9 --disable-preconnect 停用 TCP/IP 预连接。
10 --disable-remote-fonts 关闭远程字体支持。SVG 中字体不受此参数影响。
11 --disable-speech-input 停用语音输入。
12 --disable-web-security 不遵守同源策略。
13 --disk-cache-dir 将缓存设置在给定的路径。
14 --disk-cache-size 设置缓存大小上限，以字节为单位。
15 --dns-prefetch-disable 停用DNS预读。
16 --enable-print-preview 启用打印预览。
17 --extensions-update-frequency 设定拓展自动更新频率，以秒为单位。
18 --incognito 让浏览器直接以隐身模式启动。
19 --keep-alive-for-test 最后一个标签关闭后仍保持浏览器进程。（某种意义上可以提高热启动速度，不过你最好得有充足的内存）
20 --kiosk 启用kiosk模式。（一种类似于全屏的浏览模式）
21 --lang 使用指定的语言。
22 --no-displaying-insecure-content 默认情况下，https 页面允许从 http 链接引用图片/字体/框架。添加这一参数会阻止这些内容。
23 --no-first-run 跳过 Chromium 首次运行检查。
24 --no-referrers 不发送 Http-Referer 头。
25 --no-sandbox 彻底停用沙箱。
26 --no-startup-window 启动时不建立窗口。
27 --proxy-pac-url 使用给定 URL 的 pac 代理脚本。（也可以使用本地文件，如 --proxy-pac-url=“file:\\c:\proxy.pac”）
28 --proxy-server 使用给定的代理服务器，这个参数只对 http 和 https 有效。（例如 --proxy-server=127.0.0.1:8087 ）
29 --single-process 以单进程模式运行 Chromium。（启动时浏览器会给出不安全警告）
30 --start-maximized 启动时最大化。
31 --user-agent 使用给定的 User-Agent 字符串

参数：–user-data-dir=UserDataDir
用途：自订使用者帐户资料夹（如：–user-data-dir=“D:\temp\Chrome User Data”）
参数：–process-per-tab
用途：每个分页使用单独进程
参数：–process-per-site
用途：每个站点使用单独进程
参数：–in-process-plugins
用途：插件不启用单独进程

参数：–disable-popup-blocking
用途：禁用弹出拦截
参数：–disable-javascript
用途：禁用JavaScript
参数：–disable-java
用途：禁用Java
参数：–disable-plugins
用途：禁用插件
参数：–disable-images
用途：禁用图像
参数：–omnibox-popup-count=”num”
用途：将网址列弹出的提示选单数量改为num个
参数：–enable-vertical-tabs
用途：调整chrome游览器标签存放在左边，非顶部
————————————————

原文链接：https://blog.csdn.net/u010132177/article/details/116456446