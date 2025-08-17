# README 中文翻译

## 项目已更名为 mouse2joystick_Advanced_Settings 并添加新功能
### 版本 1.0.0.0
- 支持使用最多两个按键的组合来模拟一个手柄按键。
- 支持多个按键或按键组合映射到同一个手柄按键。
- 可以在按住按键或按下鼠标后暂停模拟的右摇杆输入。
- 可为按键设置 1–500 ms 的延迟；即便按键已经抬起，在延迟时间内仍视为按下状态。
- 可通过切换键临时停用当前设置，并启用另一组配置。

***

脚本最近更新：2020 年 5 月 20 日  
版本 0.4.1.4

- 键位辅助工具现可映射鼠标滚轮（滚轮无法用于长按，因为不发送松开事件）。
- 设置界面新增“保存”按钮，无需关闭窗口即可保存并应用设置，便于测试时微调。
- 可调整行走速度，不再固定为 50%。在移动时可按 `+`、`-` 键实时修改。
- 修复 Wii U Pro Controller 在 vJoy 和 vXbox 下的配置问题。

&nbsp;

### 旧版本改动
- 完全重写设置代码，便于后续调整。
- [新增保存按键列表功能](https://i.imgur.com/E6Bualc.png)，类似 CEMU 的控制器配置管理。
- **从此版本起必须为 64 位系统**（与 CEMU 要求一致）。
- 更新 ScpVBus（旧版为 32 位且过时）。

升级时建议删除旧的 `settings.ini`，以便重新输入配置，避免旧字段干扰。

&nbsp;

### 视频教程（2018 年 4 月 5 日）
[BSoD Gaming 视频](https://www.youtube.com/watch?v=bOJy67OJfZI) 展示了基本流程，但对高级设置未作详细说明；其中提到的替代鼠标检测模式仍属实验性功能，实际实现有所不同，敏感度设置也与常规模式不同。

***

## 初始设置（包含 vXBox 图片）
1. 安装最新的 [vJoy](https://sourceforge.net/projects/vjoystick/files/latest/download)。
2. 运行 [vJoy 配置程序](http://i.imgur.com/vvHW0yz.png)，设置至少 **18 个按键**（推荐 32 个）。
3. [下载控制器配置文件](https://bitbucket.org/CemuUser8/files/downloads/controllerProfiles.zip)（GitHub 发布包亦包含此文件），并解压到 [CEMU 的 controllerProfiles 目录](https://i.imgur.com/Mf5L6km.png)。
4. 在 CEMU 中打开 [输入设置](http://i.imgur.com/N5Nibtq.png)，选择控制器类型（[Wii U Pro Controller 或 Wii U GamePad](http://i.imgur.com/sfKWlgu.png)）：
   - 使用 vJoy 时：  
     - 选择 [DirectInput](http://i.imgur.com/KKCLqs8.png)。  
     - 设备应显示为 [`vJoy Device`](http://i.imgur.com/Zx9pTmK.png) 并保持连接。
   - 使用 vXBox 时：  
     - **先运行脚本并在设置中选择“Use vXBox Device”**。若第一次使用，会提示安装 ScpVBus，需两次确认。  
     - 选择 [XInput](https://i.imgur.com/2sPQM3e.png)，并确保控制器已连接（必要时刷新；如未连接，可在脚本设置中切换 vXBox 设备编号）。
   - 可选：点击 [Calibrate（校准）](http://i.imgur.com/3E6UrZX.png)。
   - 根据控制器类型选择对应的 [Profile](https://i.imgur.com/zMdtNwy.png)，并 [加载](http://i.imgur.com/PQFlfr1.png)。

- vJoy 的设置效果可参考 [此图](http://i.imgur.com/SvBR4BN.png)。  
- vXBox 的设置效果可参考 [此图](https://i.imgur.com/ZAVpvMa.png)。  
  - *可手动重新映射吹麦克风与显示屏按钮，因 vXBox 按键数量不足。*

**如果设置界面与上述不同，可能会出现问题。**

***

## 使用脚本与修改按键映射
1. 在 [GitHub 发布页](https://github.com/CemuUser8/mouse2joystick_custom_CEMU/releases) 下载最新版本（当前 0.4.1.4）。
2. 运行脚本：
   - 如安装 AutoHotKey，双击 `.ahk` 文件；
   - 否则运行 exe。
3. 若不需自定义，即可使用脚本。按 `F1` 切换控制器（需同时运行 CEMU 和脚本）。

### 按键映射
- 右击系统托盘的 [控制器图标](http://i.imgur.com/fPBWOsU.png)，选择“settings”打开设置。
- 在 [Mouse2Joystick->Keys](http://i.imgur.com/eMMnEGj.png) 页面：
  - 可编辑 [KeyList](http://i.imgur.com/JSJ1KsH.png)：按 CEMU 的 vJoy 按键顺序，用逗号分隔的 [AHK 按键](https://autohotkey.com/docs/KeyList.htm)。
  - 同一按钮可设置多个按键（使用 `|` 分隔，如 `Xbutton1|e`）。
  - 推荐先用助手配置，再手动添加副键。
- [KeyList Helper](http://i.imgur.com/VF2vwfE.png) 提供与 CEMU 输入布局相似的界面：
  - 点击框并按下对应键（可用鼠标按键）。
  - AutoCycle 会按顺序切换输入框快速设置。
  - 保存后 KeyList 会自动更新，可顺便添加副键。
  
可将不同游戏的 KeyList 保存在文本文件中，随时复制粘贴。

***

## 其他设置概览
- 在系统托盘图标打开设置：
  - **General 页面**：
    - Input Destination：如果修改过 CEMU 可执行文件名，在此填写。
    - Activate Executable：控制器启用时是否自动激活 CEMU。
    - vJoy Device：如有多个 vJoy 设备，选择要控制的编号。
  - **General->Setup**：
    - Sensitivity：鼠标移动与摇杆倾斜的比例（值越小越敏感，建议 30–100）。
    - Non-Linear Sensitivity：值越小，中心附近越敏感。
    - Deadzone：建议设为刚好相机不漂移的最小值。
    - Mouse Check Frequency：鼠标位置检测与重置的频率。
  - **General->Hotkeys**：
    - Quit Application：立即退出脚本的快捷键。
    - Toggle the controller on/off：控制器开关键（默认 F1）。
  - **Mouse2Joystick->Axes**：反转轴向（原 Y 轴方向与常规相反）。
  - **Mouse2Joystick->Keys**：设置按键（详见前文）。
  - **KeyboardMovement->Keys**：
    - Movement：设置移动按键。
    - Extra Keyboard Keys：设置行走切换、ZL 锁定、陀螺仪键。
  - **Extra Settings**：
    - 启用 BotW 鼠标滚轮换武器功能（其他游戏应关闭）。
    - 启用 ZL 锁定键功能（BotW 专用）。
    - Cursor：选择是否隐藏鼠标光标。

***

## 脚本下载
- 最新版本请见 [GitHub Releases](https://github.com/CemuUser8/mouse2joystick_custom_CEMU/releases)。
- [备用下载链接](https://bitbucket.org/CemuUser8/files/downloads/mouse2joystick_Custom_CEMU.zip)。

***

## 额外提醒
- **不建议在 CEMU 内修改按键**；在脚本中重新映射更省事。
- **游戏内的相机设置对速度影响最大，可优先调整。**
- **若以管理员身份运行 CEMU，脚本也须以管理员身份运行。**

***

如需帮助可在此留言或私信作者。

&nbsp;

## rpcs3（或其他使用 XInput 的非 CEMU 应用）说明
1. 安装 [最新 vJoy](https://sourceforge.net/projects/vjoystick/files/latest/download)。
2. 运行程序或 AutoHotKey 脚本。
3. 在托盘图标打开设置，选择 [“Use vXBox” 且在 “Activate Executable” 下选择 “No”](https://i.imgur.com/s2TnMep.png) -> 按 “Ok” 重新加载脚本。
4. 首次使用会提示安装 ScpVBus，均选“是”。
5. 脚本重新加载后会连接虚拟 Xbox 控制器；Windows 10 会自动安装驱动，Win7 需预装。
6. 在设置中 [Mouse2Joystick -> Keys](http://i.imgur.com/eMMnEGj.png) 修改按键。
   - 点击 [KeyList Helper](http://i.imgur.com/VF2vwfE.png) 映射按键，可参照 [示例界面](https://i.imgur.com/IhTR03m.png)；如需同一按钮两个按键，可按 README 说明添加。
7. 在 [KeyboardMovement -> Keys](http://i.imgur.com/okKlFwE.png) 设置移动按键；无须 ZL Lock 与 Gyro，按 Backspace 清除。
8. 在 rpcs3 中选择 XInput。
9. 使用时按 `F1`（默认）启用虚拟控制器。

完成后，鼠标控制右摇杆，键盘方向键控制左摇杆。

作者本人未亲测，但已有用户确认该流程可行。

