# Binance bStocks 命名规则发现

> **币安代币化股票将采用 `{TICKER}B` 后缀 — 由 APK 反编译 + 公开 API 在 6/1 上线前证实**

## 核心发现

Binance 的代币化股票（bStocks）将采用 **`{TICKER}B`** 命名规则。证据包括：

- APK 3.15.7 反编译：`bStocks` 品牌名、`tokenized/mint`、`tokenized/redeem` API 端点
- 公开 API `get-tokenised-asset`：返回 `ADIB`（Tokenized ADI），`tagBits: "28672"`
- `uq: "ADI"` 字段确认锚定底层真实美股 Analog Devices
- 6/1 上线日 tagBits 被清零，资产从列表消失
- Web3 钱包配置：配置 key `STOCK` (t=40) = 线上 UI `Tradfi/证券`，10 个子分类 + 2 个关联板块全部默认 `hideOndoAssets`。逻辑：隐藏 Ondo（`on` 后缀），为 bStocks（`B` 后缀）腾出展示空间

## 命名对比

| 发行方 | 后缀 | 示例 |
|---|---|---|
| Ondo Finance | `on` | `AAPLon`、`TSLAon` |
| Backed Finance (xStocks) | `x` | `AAPLx`、`AMZNx` |
| **Binance (bStocks)** | **`B`** | `ADIB`（推测 `AAPLB`、`TSLAB`） |

## 证据文件

- `report/ADIB-NAMING-REPORT.md` — 完整分析报告
- `work/api/` — 11 个 API 原始返回（含时间戳 2026-05-31）
- `work/strings/` — APK DEX 字符串扫描（7147 文件）

所有 API 数据来自公开接口（无需登录），任何人在 5/31 查询得到相同结果，6/1 起返回空。
