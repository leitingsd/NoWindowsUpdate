# 彻底阻止烦人至极的 Windows 自动更新的方法（Windows 10 & 11）

## 提供多种在不借助外部软件的情况下阻止烦人的Windows Update方法（适用于Windows 10&11）

### 一、只保留驱动更新
此方法用于“仅保留驱动更新”的模式，适合不希望 Windows 自动升级版本、但仍希望保留驱动更新功能的用户。  
⚠️ 如果你需要完全阻止 Windows 更新，请在完成本步骤后继续阅读以下其余部分。

**操作步骤：**

1. **以管理员身份运行命令提示符（CMD）**
2. **复制并粘贴以下命令以启用针对特定版本的定向更新功能：**

```cmd
reg add HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate /v TargetReleaseversion /t REG_DWORD /d 1
``` 

3. **根据当前 Windows 版本输入第二条命令：**

- 若你的版本为 **21H2**：

```cmd
reg add HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate /v TargetReleaseversionInfo /t REG_SZ /d 21H2
```

- 若你的版本为 **21H1**：

```cmd
reg add HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate /v TargetReleaseversionInfo /t REG_SZ /d 21H1
``` 

> 📖 来源：[learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/4145332/prevent-windows-10-upgrade-to-version-22h2)  
> 💡 提示：请先通过“Ctrl + R”后输入 `winver` 查看您当前的 Windows 版本号，然后将上方命令中 `/d` 后的版本号替换为您自己的版本号。

---

### 二、设置为按流量计费的连接
此方法会让 Windows 认为你的网络是“流量有限”的，从而暂停自动更新。

- **以太网连接：**  
  设置 → 网络和 Internet → 以太网 → 按流量计费的连接 → 开启  

- **Wi-Fi 连接：**  
  设置 → 网络和 Internet → WLAN →（你连接的 Wi-Fi 名称） 属性 → 按流量计费的连接 → 开启  

---

### 三、关闭 Windows 更新相关选项
返回：设置 → Windows 更新 → 高级选项  
将以下所有选项 **全部关闭**。

您可能会见到以下选项：
- 接收其他 Microsoft 产品的更新；
- 告诉我最新消息；
- **通过流量计费的链接下载更新（重要）**；
- 需要重新启动此案完成更新时通知我；

请确保它们（特别是“**通过流量计费的链接下载更新**”）均为关闭状态。

---

### 四、调整使用时段
设置 → Windows 更新 → 高级选项 → 使用时段 → 调整使用时段 → 选择“手动”  
> 建议将使用时段设置为最长（18 小时），并覆盖整个夜间时段，以防 Windows 在深夜进行自动更新。

---

### 五、关闭传递优化
设置 → Windows 更新 → 高级选项 → 传递优化  
关闭“允许从其他电脑下载”。

---

### 六、限制下载带宽
设置 → Windows 更新 → 高级选项 → 传递优化 → 高级选项  
在“下载设置”中选择“绝对带宽”，启用“限制用于在后台（或前台）下载更新的带宽流量”，并设置为：

``` 
0.1 Mbps
``` 

---

### ⚠️ 免责声明
请注意，在日常情况下，不建议停用 Windows 更新。  
停用 Windows 更新的目的仅适用于部分特殊软件环境或特定版本需求。  


⚠️ 如果您的电脑由公司 IT 管理（受组策略限制），部分设置可能无法更改。  
此种情况下，请您在执行本文档任何操作前与您的主管部门或 IT 支援部门确认。

⚠️ 在执行操作前，请确认以下风险：

- 如果您的设备仅使用 Windows Defender 或没有安装任何防病毒软件，停用更新可能使设备面临更大安全风险。  
- 本文作者不对由此带来的任何后果承担责任。  
- 禁用更新可能影响某些程序的稳定性与正常运行。  

请根据自身需求，谨慎决定是否停用 Windows 更新。

---

### 温馨提示
在根据本教程完成设置后，您可能仍有机会在 设置 → Windows 更新 中见到 Windows 更新的提示或其**正在尝试自动下载更新**，  
但请不要担心，这是**正常**的。  

上面的设置只能起到禁止 Windows Update自动下载与安装的作用，并不能彻底阻止 Windows Update 服务运行，  
Windows Update 服务**仍然会定期检查更新**。  

如果您的 Windows 更新提示其正在下载更新，您会发现它的下载进度会长时间卡在“正在下载 - 0%”，  
在稍后 Windows Update 即会认为下载超时，**自动终止其下载**并将状态更变为“**您使用的是最新版本**”。  
