# weread-cli

[English](#english) | [中文](#中文)

Command-line client for [WeRead （微信读书）](https://weread.qq.com) via the official Agent API Gateway — search books, manage your shelf, read notes & highlights, view reading stats.

通过官方 Agent API 网关调用的[微信读书](https://weread.qq.com)命令行客户端——搜书、管理书架、查看笔记划线、阅读统计。

---

## <a id="english"></a>English

### Install

```bash
# Requires Python 3.8+, no dependencies (stdlib only)
curl -sL https://raw.githubusercontent.com/nailong-dawang/weread-cli/main/bin/weread -o weread
chmod +x weread
```

### Setup

1. Log in at https://weread.qq.com/r/weread-skills to get your API key (format `wrk-xxxxxxxx`)
2. Set it as a Bearer <redacted> — the CLI reads it from the `custom.weread` connector or the `WEREAD_API_KEY` env var

### Usage

```bash
# Search books (scope=10 for ebooks)
weread search "三体" --scope 10 --count 10

# Book details
weread book <bookId>

# My shelf
weread shelf

# Notes & highlights
weread notes <bookId> --count 20

# Reading statistics
weread readdata

# Personalized recommendations
weread recommend --count 10

# Call any API directly
weread call <api_name> --param key=value ...
```

### API reference

Detailed parameters and response fields are documented in the repo's `.md` files (mirrored from Tencent's upstream WeChatReading repo):

| File | Covers |
|---|---|
| `search.md` | Search (scope selection is required reading) |
| `book.md` | Book details / chapters / progress |
| `shelf.md` | Shelf (including album counting rules) |
| `notes.md` | Notes & popular highlights |
| `readdata.md` | Reading statistics |
| `review.md` | Book reviews |
| `discover.md` | Discover good books |
| `profile.md` | User profile |

Run `weread call /_list` to see all available APIs.

**Read the corresponding doc before calling any API — don't guess field meanings from names.**

### Notes

- Every request body must include `"skill_version": "1.0.4"` (handled automatically)
- If the response contains `upgrade_info`, pause and follow the upgrade instructions
- Business params sit flat at the top level with `api_name` — not nested under `params`
- Timestamps display as YYYY-MM-DD; reading duration (seconds) as "Xh Ym"
- Book links use the `deepLink` from responses as `[Read](url)`; don't construct URLs manually

---

## <a id="中文"></a>中文

### 安装

```bash
# 需要 Python 3.8+，无第三方依赖（纯标准库）
curl -sL https://raw.githubusercontent.com/nailong-dawang/weread-cli/main/bin/weread -o weread
chmod +x weread
```

### 配置

1. 在 https://weread.qq.com/r/weread-skills 登录获取 API Key（格式 `wrk-xxxxxxxx`）
2. 通过 `custom.weread` 连接器或 `WEREAD_API_KEY` 环境变量以 Bearer <redacted> 方式使用

### 用法

```bash
# 搜书（scope=10 为电子书）
weread search "三体" --scope 10 --count 10

# 书籍详情
weread book <bookId>

# 我的书架
weread shelf

# 笔记划线
weread notes <bookId> --count 20

# 阅读统计
weread readdata

# 个性化推荐
weread recommend --count 10

# 直接调任意接口
weread call <api_name> --param key=value ...
```

### 接口文档

详细参数、回包字段见仓库内的 `.md` 文件（从腾讯上游 WeChatReading 仓库原样镜像）：

| 文件 | 内容 |
|---|---|
| `search.md` | 搜索（scope 选型约束必读） |
| `book.md` | 书籍详情/章节/进度 |
| `shelf.md` | 书架（含专辑计数规则） |
| `notes.md` | 笔记划线/热门划线 |
| `review.md` | 书籍点评 |
| `discover.md` | 推荐好书 |
| `profile.md` | 用户信息 |

运行 `weread call /_list` 查看所有可用接口。

**调用任何接口前先读对应说明文件，禁止凭字段名猜测含义。**

### 说明

- 每次请求 body 必须带 `"skill_version": "1.0.4"`（CLI 已自动处理）
- 回包出现 `upgrade_info` 时暂停并按指引升级
- 业务参数与 `api_name` 平铺在顶层，不要包在 `params` 里
- 时间戳展示为 YYYY-MM-DD；阅读时长（秒）转为"X小时Y分钟"
- 书籍链接用回包 `deepLink` 做 `[打开阅读](url)` 跳转，不手动拼接

## License

MIT
