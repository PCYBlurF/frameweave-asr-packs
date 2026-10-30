# FrameWeave ASR 包

FrameWeave 的可选本地语音识别运行时（whisper.cpp / FFmpeg / GGML 模型）。

本仓库**只存放 Release 资产**，不包含 FrameWeave 应用源码。

## 当前状态

已发布 **`asr-pack-v1`**：

- 压缩包：`asr-pack-v1.zip`
- 清单：`asr-pack-v1.manifest.json`
- 应用内下载/安装 UI 仍在开发中
- 开发环境仍可使用本地 `VB_WHISPER_ROOT` / `VB_FFMPEG`

## 下载

- Release 页面：<https://github.com/PCYBlurF/frameweave-asr-packs/releases/tag/asr-pack-v1>
- 安装包：<https://github.com/PCYBlurF/frameweave-asr-packs/releases/download/asr-pack-v1/asr-pack-v1.zip>
- 清单：<https://github.com/PCYBlurF/frameweave-asr-packs/releases/download/asr-pack-v1/asr-pack-v1.manifest.json>

压缩包大小：**194,601,662 字节**  
SHA-256：`3905c2c41729fe58c007371485b380d019e346fa62ed7a2d458b7816f97d32ea`

下载后必须使用 `manifest.json` 校验大小和 SHA-256；校验失败不得安装或启用。

## 包内容

```text
bin/ffmpeg.exe
bin/Release/whisper-cli.exe
bin/Release/whisper.dll
bin/Release/ggml.dll
bin/Release/ggml-base.dll
bin/Release/ggml-cpu-*.dll
bin/Release/SDL2.dll
models/ggml-base.bin
LICENSES/
SOURCE.txt
README.txt
```

## 组件与许可证

| 组件 | 版本 | 许可证 |
| --- | --- | --- |
| FFmpeg | n9.0.2-39-g7adfbe40dc，BtbN LGPL 构建 | LGPL-3.0 |
| whisper.cpp | 1.9.5（b5454） | MIT |
| SDL2 | 2.28.5 | Zlib |
| ggml-base.bin | base 模型，来自 ggerganov/whisper.cpp | MIT |

来源、上游地址和对应源码说明见包内 `SOURCE.txt` 与 `LICENSES/`。

## 校验

压缩包已在本地通过：

- 最小文件集 ASR smoke：`ASR_SMOKE_OK`
- 词级时间戳
- manifest 大小/SHA-256 校验

## 安装约定

应用内安装器计划使用：

```text
%LOCALAPPDATA%\FrameWeavesr.0.0```

安装器必须：

1. 先显示大小、来源和许可证；
2. 取得用户显式同意；
3. 下载到临时文件；
4. 校验大小和 SHA-256；
5. 校验成功后再原子安装；
6. 允许删除 ASR 包，且不影响项目或字幕；
7. 不静默下载，不把未校验的包投入使用。

## 开发

在安装器完成前，开发环境使用本地目录：

```text
VB_WHISPER_ROOT=<包含 bin/ 和 models/ 的目录>
```

可选覆盖：

```text
VB_FFMPEG=<ffmpeg.exe 路径>
VB_WHISPER_BIN=<whisper-cli.exe 路径>
VB_WHISPER_MODEL=<ggml 模型路径>
```

## 许可证与再分发

本仓库不包含也不发布任何用户素材。当前包只包含本地 ASR 运行时和模型。

FFmpeg 为 LGPL 静态构建；再分发时仍需遵守 LGPL 的对应源码/提供义务。建议正式对外发布前做一次法律确认。
