# Hermes Agent Windows 安装脚本（国内优化版）

> 适用于 Windows 10/11，一键安装 Hermes Agent，自动配置国内大模型 API

## 功能特性

- **全自动检测**：自动检测 WSL 2、Ubuntu 等依赖环境
- **国内优化**：内置多个安装源，自动降级到国内镜像
- **多模型支持**：DeepSeek、Moonshot/Kimi、智谱 GLM、阿里 Qwen、百川、字节豆包、MiniMax、阶跃星辰、零一万物、腾讯混元
- **API 自动发现**：输入提供商名称即可自动匹配 API 端点
- **交互式配置**：向导式引导，操作简单

## 系统要求

| 项目 | 要求 |
|------|------|
| 操作系统 | Windows 10 / Windows 11 |
| 权限 | 管理员身份运行 |
| 网络 | 能访问 GitHub（或国内镜像） |

## 快速开始

### 方法一：一键安装

```powershell
# 以管理员身份打开 PowerShell，运行：
irm https://raw.githubusercontent.com/你的用户名/hermes-agent-installer/main/hermes-agent-installer.ps1 | iex
```

### 方法二：下载脚本运行

1. 下载 `hermes-agent-installer.ps1`
2. 右键 → **使用 PowerShell 运行**（或以管理员身份打开 PowerShell 后执行脚本）
3. 按提示完成配置

## 安装流程

```
[1/8] 检查系统要求
[2/8] 检查 WSL 状态
[3/8] 配置 WSL 2 默认版本
[4/8] 检查 Ubuntu 安装状态
[5/8] 安装 Hermes Agent
[6/8] 配置国内大模型 API
[7/8] 测试 API 连接
[8/8] 生成配置文件
```

## 支持的模型提供商

| 提供商 | 模型示例 | API 端点 |
|--------|----------|----------|
| DeepSeek | deepseek-chat | api.deepseek.com |
| Moonshot / Kimi | moonshot-v1-8k | api.moonshot.cn |
| 智谱 GLM | glm-4 | open.bigmodel.cn |
| 阿里 Qwen | qwen-turbo | dashscope.aliyuncs.com |
| 百川 | baichuan4 | api.baichuan-ai.com |
| 字节豆包 | doubao-pro | ark.cn-beijing.volces.com |
| MiniMax | abab6.5s | api.minimax.chat |
| 阶跃星辰 | step-1v | api.stepfun.com |
| 零一万物 | yi-large | api.lingyiwanwu.com |
| 腾讯混元 | hunyuan | hunyuan.tencentcloudapi.com |

## 安装后使用

```bash
# 进入 WSL
wsl

# 启动 Hermes Agent
hermes
```

## 配置文件

安装完成后，配置文件位于 WSL 内的 `~/.hermes/config.yaml`：

```yaml
models:
  default:
    provider: deepseek
    api_key: "your-api-key"
    base_url: "https://api.deepseek.com/v1"
    model: "deepseek-chat"

settings:
  temperature: 0.7
  max_tokens: 4096
  stream: true
```

## 常见问题

### Q: 提示"请以管理员身份运行"

右键点击 PowerShell，选择 **以管理员身份运行**，然后重新执行脚本。

### Q: WSL 安装失败

手动打开 Microsoft Store 搜索 **Ubuntu 22.04 LTS** 下载安装，安装完成后再运行此脚本。

### Q: API Key 验证失败

确保 API Key 填写正确，部分厂商（如 MiniMax）可能需要在控制台额外配置。

### Q: 国内访问 GitHub 慢

脚本会自动尝试切换到国内镜像源，如果仍然失败，可手动从 https://aka.ms/wsl2kernel 下载离线包。

## 项目结构

```
hermes-agent-installer/
├── hermes-agent-installer.ps1   # Windows 安装脚本
└── README.md                    # 本文件
```

## License

MIT License

## 参考链接

- [Hermes Agent 官方仓库](https://github.com/NousResearch/hermes-agent)
- [WSL 2 安装文档](https://docs.microsoft.com/zh-cn/windows/wsl/install)
- [Ubuntu 22.04 LTS 下载](https://aka.ms/wslubuntu2204)
