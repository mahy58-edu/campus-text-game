# 校园文字游戏 · Campus Text Game

一个用 **Python + tkinter** 写的校园题材文字小游戏，PyInstaller 打包成 Windows 单目录绿色版：
解压后双击 `Try1.exe` 就能玩，不需要装 Python。

> **注意：本仓库目前是「二进制分发」，不是完整的开源项目。**
> 上传的压缩包里只有编译后的 `Try1.exe` 与 `_internal` 运行时，**没有 `.py` 源码**。
> 源码整理好后会作为第二次提交补进来，见下面的 Roadmap。

![场景 1](screenshots/scene-1.jpg)

## 下载与运行

1. 到 [Releases](https://github.com/mahy58-edu/campus-text-game/releases) 下载 `Try1-1.0.0-win64.zip`
2. 解压到任意目录，**四张 jpg 必须和 `Try1.exe` 放在同一层**（程序按相对路径读图）
3. 双击 `Try1.exe`
4. 首次运行若被 SmartScreen 拦截：点「更多信息」→「仍要运行」

实测环境：Windows 10 / 11 x64（内部为 `python314.dll` + `PIL` + `tkinter` 运行时）。

## 已知问题

| 现象 | 原因 | 绕法 |
|---|---|---|
| 弹出 `Unhandled exception in script` | 程序用相对路径加载 `1.jpg` / `2.jpg` / `3.jpg` / `background.jpg`，从别的目录启动（或用没设「起始位置」的快捷方式）就找不到素材 | 在解压目录里直接双击；快捷方式要把「起始位置」设成该目录 |
| 压缩包 38 MB / 解压后 38 MB | PyInstaller 把 tkinter、Tcl/Tk、PIL 全打进去了 | 暂无，属正常 |

## 目录

```text
Try1/
  Try1.exe            # 启动器（PyInstaller bootloader）
  _internal/          # Python 3.14 运行时 + tkinter/tcl + Pillow
  1.jpg 2.jpg 3.jpg   # 场景插图
  background.jpg      # 背景图
```

`screenshots/` 里是同四张图的副本，只为让 README 能直接显示。

## Roadmap

- [ ] 补上游源码：`main.py` + `requirements.txt` + PyInstaller `.spec`
- [ ] 素材路径改成基于 `__file__` / `sys._MEIPASS`，彻底修掉「工作目录不对就崩」
- [ ] 体积优化：排除用不到的 Tcl/Tk 组件与 PIL 插件
- [ ] 加截图与玩法说明

## 许可证

[MIT](LICENSE)。素材图为 AI 生成，随项目一并提供。
