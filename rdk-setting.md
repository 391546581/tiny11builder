第一步：获取免费的 Ngrok Authtoken（1分钟）
访问 ngrok.com 注册一个免费账号。
登录后进入 Your Authtoken 页面复制你的 Token。
第二步：在 GitHub 仓库添加 Secret
打开你的 GitHub 仓库页面，点击 Settings。
在左侧菜单找到 Secrets and variables -> Actions。
点击 New repository secret：
Name 填写：NGROK_AUTHTOKEN
Secret 填写：你在 Ngrok 复制的 Token 字符串。
点击 Add secret 保存。
第三步：启动并连接远程桌面
进入 GitHub 仓库顶部的 Actions 标签。
在左侧列表中选择 Windows Remote Desktop (Debug Only)。
点击右侧 Run workflow（可自定义连接密码和保持时长，也可以留空自动生成密码）。
任务运行约 30 秒后，展开 Start Ngrok TCP Tunnel for RDP port 3389 步骤，或者直接查看页面底部的 Summary，会看到类似如下的信息：

在你自己的 Windows 电脑上按快捷键 Win + R，输入 mstsc 打开远程桌面连接：
计算机：粘贴上面给出的 4.tcp.ngrok.io:12345（端口号要一并带上）。
用户名：runneradmin
密码：输入给出的密码。
点击连接即可进入这台云端 Windows 虚拟机的桌面，你可以在上面打开浏览器、下载软件、用鼠标点击测试界面。
三、 退出与销毁
提前结束：在 GitHub Actions 页面直接点击 Cancel run，机器会立即停止并自动彻底销毁。
超时自动退出：达到设定的时长（默认 60 分钟）后，任务自动结束并销毁所有数据。
