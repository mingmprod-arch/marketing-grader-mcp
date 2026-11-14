# Marketing Grader MCP

[English](README.md)

<img src="assets/marketing-grader.svg" alt="Marketing Grader" width="80" height="80">

喺 AI 助手查看自己品牌嘅 DNA、已存圖文同已記錄行銷成效。呢個 repo 只提供連接設定同使用說明，唔包括 Marketing Grader 後端程式。

**遠端連接：** `https://grader.recmoment.net/mcp`

## 三步開始

1. 按下面方法，喺 AI 平台加入連接。
2. 登入自己嘅 Marketing Grader 帳戶，核對 OAuth 授權。
3. 叫 AI 列出可用品牌，確認今次查邊個品牌。

唔需要將密碼、社交 token 或 API key 填入設定檔。想讀 Search Console／GA4，就喺授權畫面明確揀選相關資源。

### Gemini CLI

```sh
gemini extensions install https://github.com/mingmprod-arch/marketing-grader-mcp
```

安裝後重新開啟 Gemini CLI，再輸入：

```text
/mcp auth marketing-grader
/mcp
```

根目錄 `gemini-extension.json` 已用 `httpUrl` 設定 Streamable HTTP。亦可以將 `configs/gemini.settings.json` 嘅 server entry 合併落既有設定；兩個方法揀一個，避免重複連接。

### Codex

```sh
codex mcp add marketing-grader --url https://grader.recmoment.net/mcp
codex mcp login marketing-grader
codex mcp list
```

### Claude Code

```sh
claude mcp add --transport http marketing-grader https://grader.recmoment.net/mcp
```

喺 Claude Code 用 `/mcp` 查看連接及登入。

### 其他 AI 平台

| 平台 | 方法 |
|---|---|
| ChatGPT | 喺帳戶支援嘅自訂遠端 MCP 連接流程加入上面網址，再完成 OAuth；視乎帳戶及管理員設定。 |
| Claude 網頁／桌面版 | 加入自訂 remote connector，填上面網址，再完成 OAuth。 |
| Grok | 喺 [Connectors](https://grok.com/connectors) 揀 **New Connector → Custom**，加入遠端網址；Business／Enterprise 可能要管理員先開通。 |
| Perplexity | 支援嘅 Pro、Max 或 Enterprise 帳戶用 **Plugins → Add custom** 加入遠端 MCP 網址。 |
| Mistral Vibe | 帳戶擁有人／管理員用 **Connectors → Add Connector → Custom MCP** 加入遠端網址。 |
| Cursor | 合併 `configs/cursor.mcp.json` 到 `.cursor/mcp.json` 或 `~/.cursor/mcp.json`，再喺 MCP 設定連接。 |
| VS Code／GitHub Copilot | 合併 `configs/vscode.mcp.json` 到 `.vscode/mcp.json`，或用 **MCP: Add Server** 加入 HTTP 網址。 |

[完整設定範本](configs/README.md)。自行加入連接、安裝 extension，同獲平台批准公開上架係分開嘅流程；呢個 repo 唔代表已獲各平台批准。

## 可以直接問

> 列出我可用嘅 Marketing Grader 品牌，再確認今次查邊個。

揀好品牌之後：

> 比較呢個品牌已存嘅 24 小時同 7 日帖文成效，附上記錄日期；缺資料寫未知。

或者：

> 整理我明確授權嘅 Search Console 同 GA4 報告，分開點擊、工作階段同各來源關鍵事件。

品牌 ID 要由 `list_brands` 取得，唔好自行估算。網站左下角所選品牌唔會自動等於 AI 對話嘅品牌。系統會檢查登入帳戶、角色同所查品牌；Google 報告另外要符合授權時選定嘅指定資源。

## 九個唯讀工具

| 工具 | 可以讀取 |
|---|---|
| `list_brands` | 帳戶可用品牌 |
| `get_brand_dna` | 已存品牌定位、網站、風格、語氣同允許素材 |
| `list_content_drafts` | 已存文案、hashtag、平台、狀態同日期 |
| `get_content_calendar` | 已有日期嘅社交草稿同 SEO 計劃 |
| `get_social_connections` | 已連接帳號名稱同記錄嘅到期日，唔包括憑證 |
| `get_post_performance` | 已存 24 小時／7 日帖文成效 |
| `get_ads_strategy` | 已存廣告策略 |
| `get_search_console_performance` | 明確授權嘅指定 Search Console 資源快照 |
| `get_marketing_performance` | 明確授權嘅 Search Console／GA4 資源報告 |

AI 可以解釋記錄，或者喺對話起草構思。呢個 MCP 不能儲存草稿、生成圖片、發帖、寄信、匯出客人名單、修改網站或廣告、花費預算或收款。Google 報告係已保存快照，要喺 Marketing Grader 更新。已連接唔代表已獲發佈權限。缺資料保留未知，互動或關鍵事件唔等於已核實收入或 ROI。

## 私隱、授權同收費

連接用 OAuth 同 PKCE，設定檔冇私人憑證。AI 平台會按工具要求取得允許讀取嘅記錄；連接前亦要核對該平台嘅資料政策。草稿同品牌文字只當資料，唔當指令。

可以喺 [連接管理](https://grader.recmoment.net/mcp-connections) 撤銷 AI 用戶端。撤銷或到期後可能要重新連接；唔會承諾永久有效。

九個工具只讀已有記錄，唔會啟動 Marketing Grader AI 生成、付費抓取、寄件或廣告操作。AI 平台可能另有收費；Marketing Grader 其他收費服務仍按帳戶方案處理。

[私隱政策](https://grader.recmoment.net/privacy) · [服務條款](https://grader.recmoment.net/terms) · [支援](https://grader.recmoment.net/terms#s19) · [安全說明](SECURITY.md)

## 套件同服務

呢個 repo 係託管服務嘅連接套件，唔包括後端、資料庫或私人基建。套件未聲明 MIT、Apache 或其他開源授權；使用服務按已公布條款處理。

[官方設定文件](docs/sources.md) · [維護者相容性備註](docs/maintainers.md)
