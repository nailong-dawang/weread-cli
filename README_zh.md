# weread-cli

微信读书 CLI —— 搜书、管书架、看笔记划线、浏览书评、阅读统计、发现好书。通过微信读书 Agent API 网关调用。

[English](README.md)

## 配置

1. 去 https://weread.qq.com 获取 API Key（格式 `wrk-xxxxxxxx`）
2. 设为环境变量：

```bash
export WEREAD_API_KEY="wrk-xxxxxxxx"
```

## 用法

```bash
./bin/weread search "三体" [--scope 10] [--count 10]   # 搜书
./bin/weread book <bookId>                              # 书籍详情
./bin/weread shelf                                      # 我的书架
./bin/weread notes <bookId> [--count 20]                # 笔记划线
./bin/weread readdata                                   # 阅读统计
./bin/weread recommend [--count 10]                     # 个性化推荐
./bin/weread call <api_name> [--param k=v ...]          # 直接调任意接口
```

网关：`POST https://i.weread.qq.com/api/agent/gateway`，`Authorization: Bearer $WEREAD_API_KEY`。

各接口的详细参数见本仓库的 `*.md` 文档（search、book、shelf、notes、review 等）。

## 许可证

MIT
