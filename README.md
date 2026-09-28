# Windows Executable-Extension DLP Test Matrix (Benign)

一组**良性占位样本**，用于 **DLP 文件分类 / 扩展名识别 / 绕过对抗测试**的授权安全研究。

## 重要声明
- **无真实可执行代码、无 PE 头(MZ)、无脚本逻辑、无恶意载荷**。每个样本仅含一行纯文本说明。
- 所有文件均为良性占位样本，专用于授权安全研究与产品验证，**非恶意软件**。
- 用例按 `tNN/<filename>` 组织，避免重复目标名冲突（如 t40 与 t47 均为 file.exe）。

## 测试矩阵

| 用例 | 文件名 | 测试意图 |
|---|---|---|
| t01 | `sample.com` | 基础 COM/可执行扩展名，常规识别 |
| t02 | `sample.exe` | 基础 EXE，基线对照 |
| t03 | `sample.bat` | 批处理脚本 |
| t04 | `sample.cmd` | 命令脚本 |
| t05 | `sample.vbs` | VBScript |
| t06 | `sample.vbe` | 编码 VBScript |
| t07 | `sample.js` | JScript(WSH) |
| t08 | `sample.jse` | 编码 JScript |
| t09 | `sample.wsf` | Windows Script File |
| t10 | `sample.wsh` | WSH 快捷方式 |
| t11 | `sample.msc` | Microsoft 管理控制台快照 |
| t12 | `sample.scr` | 屏幕保护程序(PE) |
| t13 | `sample.cpl` | 控制面板项 |
| t14 | `sample.pif` | 程序信息文件 |
| t15 | `sample.msi` | Windows Installer |
| t16 | `sample.msp` | MSI 补丁 |
| t17 | `sample.mst` | MST 转换 |
| t18 | `sample.dll` | 动态链接库 |
| t19 | `sample.ps1` | PowerShell 脚本 |
| t20 | `sample.psm1` | PowerShell 模块 |
| t21 | `sample.psd1` | PowerShell 数据/清单 |
| t22 | `sample.hta` | HTML 应用程序 |
| t23 | `sample.wsc` | Windows Script Component |
| t24 | `sample.sct` | Windows Script Component(注册) |
| t25 | `sample.ws` | Windows Script |
| t26 | `sample.lnk` | 快捷方式 |
| t27 | `sample.inf` | 安装信息 |
| t28 | `sample.reg` | 注册表文件 |
| t29 | `sample.jar` | Java 归档(可执行) |
| t30 | `sample.appx` | Windows 应用包 |
| t31 | `sample.msix` | MSIX 包 |
| t32 | `sample.appxbundle` | APPX 包束 |
| t33 | `sample.msixbundle` | MSIX 包束 |
| t34 | `sample.diagcab` | 诊断 CAB 包 |
| t35 | `sample.gadget` | 桌面小工具 |
| t36 | `sample.application` | ClickOnce 应用 |
| t37 | `sample.msh` | Monad/Shell 脚本 |
| t38 | `case.ExE` | 大写扩展名 ExE，测大小写不敏感匹配 |
| t39 | `file.exe.` | 尾部多余点号，测路径规范化/截断 |
| t40 | `file.exe` | 重复目标名(与 t47)，置于独立子目录 |
| t41 | `photo.jpg.exe` | 双扩展名伪装(图片名+exe)，经典绕过 |
| t42 | `file.exe.jpg` | 反向双扩展名(exe名+jpg)，测后缀优先级 |
| t43 | `noext` | 无任何扩展名，测无扩展名识别 |
| t44 | `exe_mz.exe` | 名称暗示 MZ 魔数；当前内容为纯文本(可请求注入真实 MZ 字节) |
| t45 | `exe_textplain.exe` | .exe 名称但内容为 text/plain，测扩展名 vs 内容不一致 |
| t46 | `dummy.txt` | 良性对照(明文) |
| t47 | `file.exe` | 重复目标名(与 t40)，置于独立子目录 |
| t48 | `test‮gnp.exe` | RTL 覆盖符(U+202E)混淆，显示层伪装为 test.exe |
| t49 | `test.ехе` | 西里尔字母同形字扩展名(е х е)，ASCII 下形似 exe |
| t50 | `archive.zip` | 容器格式(可内嵌其他样本) |
| t51 | `file.url` | Internet 快捷方式(.url) |
| t52 | `shortcut.lnk` | 快捷方式(与 t26 同名，独立子目录) |
| t53 | `file..exe` | 双点号(空扩展段) |
| t54 | `.exe` | 仅扩展名/点文件(无基名) |
| t55 | `control.txt` | 良性对照(明文) |

## 说明
- 仓库为**私有**（private）。登录 Gitee 后 blob/raw 链接可访问；如需对外分享，请在仓库设置中改为 public。
- `t44 exe_mz.exe` 目前为纯文本内容；如需测试魔数(MZ)字节检测，可单独请求注入 `MZ` 起始字节(仍为良性文件)。
- `t45 exe_textplain.exe` 用于测试“扩展名(.exe)与内容(text/plain)不一致”时的识别优先级。
- License: CC0 1.0 Universal。
