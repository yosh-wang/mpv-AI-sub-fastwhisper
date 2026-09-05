# 🎬 MPV Player · 硬核技术交流群

[![QQ Group](https://img.shields.io/badge/QQ①群-1097053691-12B7F5?logo=tencent-qq&logoColor=white)](https://qm.qq.com/q/KQZsl4wFmG) 
[![Members](https://img.shields.io/badge/群成员-2000+-4CAF50)](https://qm.qq.com/q/KQZsl4wFmG)          [![QQ Group](https://img.shields.io/badge/QQ②群-1104144778-12B7F5?logo=tencent-qq&logoColor=white)](https://qm.qq.com/q/KDxk01ukwe)
[![Members](https://img.shields.io/badge/群成员-33+-4CAF50)](https://qm.qq.com/q/KDxk01ukwe)

---
> **🎯 mpv · 为画质而生，为技术而狂 · mpv 🎯**
---

## 📌 群信息

<table>
  <tr>
    <td width="50%" valign="top" style="padding: 0;">
      <table>
        <tr><td><strong>QQ ①群</strong></td><td><a href="https://qm.qq.com/q/KQZsl4wFmG">1097053691</a></td></tr>
        <tr><td><strong>QQ ②群</strong></td><td><a href="https://qm.qq.com/q/KDxk01ukwe">1104144778</a></td></tr>
        <tr><td><strong>群成员</strong></td><td>2000，36+</td></tr>
        <tr><td><strong>群性质</strong></td><td>热心发电·免费交流</td></tr>
        <tr><td><strong>分享内容</strong></td><td>配置/脚本/着色器/懒人包</td></tr>
        <tr><td><strong>适合人群</strong></td><td>新手入门·玩家折腾·开发交流</td></tr>
        <tr><td><strong>群目标</strong></td><td>互助·分享·共同折腾</td></tr>
        <tr><td><strong>进群暗号</strong></td><td>mpv 玩家</td></tr>
      </table>
    </td>
    <td width="50%" align="center" valign="top" style="padding: 0;">
      <table>
        <tr>
          <td align="center">
            <img src="QQ Group1.png" alt="QQ群二维码" width="200">
          </td>
          <td align="center">
            <img src="QQ Group2.png" alt="群内讨论截图" width="200">
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>

---

# mpv-sub-fastwhisper

> 📌 本仓库从 [dyphire/mpv-sub-fastwhisper](https://github.com/dyphire/mpv-sub-fastwhisper) fork 而来，增加了**详细的图文教程**。

---

### 🤖 AI 字幕生成

通过 [faster-whisper](https://github.com/Purfview/whisper-standalone-win) 进行语音转录，自动生成 SRT 字幕。

字幕生成后，脚本会自动调用 GPT API 将字幕翻译为目标语言（默认中文）。

> 💡 GPT API 相关配置需自行在脚本选项中设置。

| 依赖 | 说明 |
|------|------|
| [faster-whisper](https://github.com/Purfview/whisper-standalone-win) | 本地语音识别引擎 |
| FFmpeg | 音频处理 |

---

### 📖 AI 字幕 使用教程

## 🎬 mpv播放器 + AI 实时字幕生成 & 翻译 —— 小白完整教程

---

## 📖 本教程最终效果

> 播放视频时按 **`Alt + F`**，AI 自动识别语音 → 生成字幕 → 翻译成中文。
>
> 最终显示**双语字幕**：上排中文（白色字体）+ 下排原文（橙黄色字体）。

- 🔵 上排：中文翻译（白色字体）
- 🟠 下排：原文（橙黄色字体）

![图片25](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/25.jpg)

---

## 📋 准备工作

| # | 要求 |
|---|------|
| 1 | 一张 **NVIDIA 显卡**（N卡），显存建议 6GB 以上 |
| 2 | 电脑已安装 **7-Zip** 或 **WinRAR**（解压软件） |
| 3 | 目标文件夹已创建：`D:\000\ai-whisper\` 和 `D:\000\mpv\` |

![图0](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/0.png)

---

## 🚀 第一步：下载 Faster-Whisper-XXL（AI 语音识别程序）

**1.** 打开浏览器，访问：

🔗 https://github.com/Purfview/whisper-standalone-win/releases

![图片1](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/1.png)

**2.** 在页面中找到 **"Faster-Whisper-XXL r245.4"** 这个版本

> ⚠️ **注意：** 选 **r245.4**，不要选 Pro 版本！

![图片2](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/2.png)

**3.** 在 r245.4 版本的 `Assets` 区域，点击下载：

📦 **Faster-Whisper-XXL.7z**（文件大小约 2GB+，请耐心等待下载完成）

![图片3](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/3.png)

**4.** 下载完成后，右键点击 `Faster-Whisper-XXL.7z`

> → 用 7-Zip 打开 → 打开 `Faster-Whisper-XXL` → **选中里面的四个文件** → 解压到 `D:\000\ai-whisper\`

![图片4](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/4.png)

**5.** 解压完成后，确认目录结构如下：

```
D:\000\ai-whisper\
├── _xxl_data\
├── faster-whisper-xxl.exe    ← 主程序
├── ffmpeg.exe                ← 音频处理
└── One Click Transcribe.bat
```

![图片5](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/5.png)

**5.1** 在 `D:\000\ai-whisper\` 下**新建文件夹** `_models`：

```
D:\000\ai-whisper\
├── _xxl_data\
├── faster-whisper-xxl.exe    ← 主程序
├── ffmpeg.exe                ← 音频处理
├── One Click Transcribe.bat
└── _models\                  ← 模型文件夹 ⬅ 自己新建
```

![图片5.1](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/5.1.png)

---

## 🧠 第二步：下载 AI 模型（faster-whisper-large-v3）

**1.** 打开浏览器，访问：

🔗 https://hf-mirror.com/Systran/faster-whisper-large-v3/tree/main

![图片6](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/6.png)

**2.** 需要下载以下 **7 个文件**（逐个点击下载）：

| 文件名 | 大小 | 说明 |
|--------|------|------|
| `config.json` | 几 KB | 配置文件 |
| **`model.bin`** | **约 3GB** | 🔥 核心模型文件，耐心等待 |
| `preprocessor_config.json` | 几 KB | 预处理配置 |
| `README.md` | 几 KB | 说明文档（可不下载） |
| `tokenizer.json` | 约 3MB | 分词器 |
| `vocabulary.json` | 约 2MB | 词表 |
| `.gitattributes` | 几 KB | Git 属性文件 |

![图片7](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/7.png)

**3.** 在 `D:\000\ai-whisper\_models\` 目录下，**新建文件夹**：`faster-whisper-large-v3`

![图片8](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/8.png)

**4.** 把下载的 7 个文件，全部移动/复制到这个文件夹里：

📁 `D:\000\ai-whisper\_models\faster-whisper-large-v3\`

![图片9](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/9.png)

**5.** 确认最终结构如下：

```
D:\000\ai-whisper\_models\faster-whisper-large-v3\
├── .gitattributes
├── config.json
├── model.bin                ← 🔥 核心文件，确认存在！
├── preprocessor_config.json
├── README.md
├── tokenizer.json
└── vocabulary.json
```

---

## 🔑 第三步：申请智谱 AI 的 API Key（免费翻译用）

> 💡 **说明：** 语音识别完成后，需要 AI 把字幕翻译成中文。智谱 AI 提供**免费额度**，注册即可使用。

**1.** 打开浏览器，访问：🔗 https://bigmodel.cn/

![图片10](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/10.png)

**2.** 点击右上角「注册/登录」，用手机号注册账号（已有账号可直接登录）

![图片11](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/11.png)

> ⚠️ **注意：** 注册后会弹出一个弹窗，问你是「企业组织」还是「我是开发者」，这里选择 **「跳过」**。

![图片11.1](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/11.1.png)

**3.** 登录成功后，进入「控制台」（通常在页面右上角头像菜单中）

![图片12](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/12.png)

**4.** 在左侧菜单栏找到「API Key」，点击进入

![图片13](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/13.png)

**5.** 点击「+ 新建 API Key」按钮

![图片14](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/14.png)

![图片14.1](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/14.1.png)

**6.** 系统会生成一串密钥（格式类似：`xxxxxxxx.yyyyyyyy.zzzzzzzz`）

点击「复制」按钮，**立即粘贴到记事本保存！**

> 💡 **提示：** 请妥善保管你的 API Key，不要泄露给他人。

![图片15](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/15.png)

**7.** 把 API Key 粘贴到记事本暂存，下一步要用。

---

## ⚙️ 第四步：配置 sub_fastwhisper.conf（核心步骤 🔥）

**1.** 打开文件资源管理器，进入以下路径：

📁 `D:\000\mpv\portable_config\script-opts\`

![图片16](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/16.png)

**2.** 找到 `sub_fastwhisper.conf` 文件，右键 → 用记事本打开

![图片17](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/17.png)

**3.** 修改以下 **4 行**（去掉行首的 `#` 号，填入你的信息）：

> **第 3 行：** 去掉 `#`，填入路径
> ```
> fast_whisper_path=D:\000\ai-whisper\faster-whisper-xxl.exe
> ```
>
> **第 5 行：** 去掉 `#`，指定模型
> ```
> model=large-v3
> ```
>
> **第 7 行：** 去掉 `#`，使用显卡
> ```
> device=cuda
> ```
>
> **第 33 行：** 填入第三步申请的 API Key ⭐
> ```
> api_key=你刚才复制的API-Key粘贴到这里
> ```

![图片18](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/18.png)

![图片19](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/19.png)

**4.** 修改完成后，完整的配置内容应如下：

```
# faster-whisper 可执行文件的路径
fast_whisper_path=D:\000\ai-whisper\faster-whisper-xxl.exe
# 指定要使用的模型
model=large-v3
# 指定要使用的设备
device=cuda
# 换行前一行的最大字符数
max_line_width=100
# 指定输出路径
output_path=source
# 指定在更新前生成多少字幕
update_interval=20
# 使用分段法
use_segment=no
segment_duration=10
## GPT API 选项 ###
api_url=https://open.bigmodel.cn/api/paas/v4/chat/completions
api_key=你之前复制的API-Key
api_mode=glm-4-flash
api_temperature=0.95
api_rate=15
translate=Chinese
font_name=Noto Sans CJK SC
```

**5.** 按 **`Ctrl + S`** 保存，关闭记事本。

---

## 🎯 第五步：测试运行

**1.** 打开 mpv 播放器：`D:\000\mpv\mpv.exe`

![图片20](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/20.png)

**2.** 拖入一个视频文件到 mpv 窗口中播放

![图片21](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/21.jpg)

**3.** 按下键盘 **`Alt + F`**（同时按住 Alt 键，再按 F 键）

![图片22](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/22.jpg)

**4.** 屏幕左上角出现提示文字：

> `"AI subtitle generation in progress"`

![图片23](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/23.jpg)

打开控制台：右键 → 其他 → 控制台，或者按 **`Alt + ~`**

![图片23.1](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/23.1.jpg)

可以看到控制台，里面有提示 AI 字幕生成过程：

![图片23.2](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/23.2.jpg)

**5.** 等待 2-5 分钟（取决于视频长度和显卡性能），字幕会边生成边显示在屏幕上

![图片24](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/24.Jpg)

**6.** 最终效果：双语字幕显示 🎉

- 🔵 上排：中文翻译（白色字体）
- 🟠 下排：原文（橙黄色字体）

![图片25](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/25.jpg)

**7.** 视频右上角有一个**白点** ● ：表示当前已开启 AI 字幕翻译

![图片26](https://raw.githubusercontent.com/yosh-wang/mpv-AI-sub-fastwhisper/master/image/26.jpg)

---

### 🛠️ 补充操作

| 方式 | 操作 |
|------|------|
| ⌨️ 方式一 | 按 **`Alt + F`** 快捷键 |
| 🖱️ 方式二 | 右键点击播放画面 → 字幕 → 生成AI字幕 |
| ⌨️ 方式三 | 按 **`Alt + ~`** 打开控制台查看进度 |

---

## ❓ 常见问题（FAQ）

<details open>
<summary><b>Q1: 按 Alt+F 完全没反应？</b></summary>

检查 `sub_fastwhisper.conf` 中 `fast_whisper_path` 路径是否正确。确认 `D:\000\ai-whisper\faster-whisper-xxl.exe` 文件存在。
</details>

<details open>
<summary><b>Q2: 提示 "AI subtitle generation failed"？</b></summary>

1. 检查模型文件 `model.bin` 是否在正确位置
2. 显卡是否支持 CUDA
3. 如果显卡不支持，把 `device=cuda` 改为 `device=cpu`
</details>

<details open>
<summary><b>Q3: 字幕生成特别慢？</b></summary>

首次加载模型需要一些时间，之后会快一些。如果显存不足（<6GB），建议改用 `device=cpu`。
</details>

<details open>
<summary><b>Q4: 翻译没出现（只有原文，没有中文）？</b></summary>

检查 `api_key` 是否正确填入，末尾不要有空格。确认智谱 AI 账户有免费额度。
</details>

<details open>
<summary><b>Q5: 字幕乱码或显示方框？</b></summary>

检查 `font_name` 设置的字体是否已安装。当前配置用的是 `Noto Sans CJK SC`（已在 mpv 字体目录中）。
</details>

---

## 🌳 文件结构总览（最终确认）

```
D:\
└── 000\
    ├── ai-whisper\                          ← 🤖 AI 程序区
    │   ├── faster-whisper-xxl.exe
    │   ├── ffmpeg.exe
    │   ├── One Click Transcribe.bat
    │   ├── _models\
    │   │   └── faster-whisper-large-v3\
    │   │       ├── config.json
    │   │       ├── model.bin                ← 🔥 核心！
    │   │       ├── preprocessor_config.json
    │   │       ├── tokenizer.json
    │   │       ├── vocabulary.json
    │   │       ├── .gitattributes
    │   │       └── README.md
    │   └── _xxl_data\                       ← 🐍 Python 环境
    │
    └── mpv\                                 ← 🎬 播放器区
        ├── mpv.exe
        └── portable_config\
            ├── scripts\
            │   └── sub-fastwhisper.lua       ← 📜 AI 字幕脚本
            └── script-opts\
                └── sub_fastwhisper.conf      ← ⚙️ 配置文件（已修改）
```

---

> 📝 **教程结束** — 祝你使用愉快！有问题欢迎加群交流 🎉
