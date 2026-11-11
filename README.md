# tdgcdtd.dpdns.org

个人网站，托管在 GitHub Pages，域名 `tdgcdtd.dpdns.org`。DNS 在 Cloudflare，记录为 CNAME → `tdgcdtd.github.io`，开启代理（橙色云朵），HTTPS 证书由 Cloudflare 提供，SSL 模式为 Full。

目前内容：**美股指数每日波动** —— 标普 500 与纳斯达克 100 每个交易日的涨跌幅和原因。

## 文件

- `index.html`：网页本身（读取 `data/days.json` 并显示）
- `data/days.json`：每日数据。更新网站只需要改这个文件
- `CNAME`：告诉 GitHub Pages 使用的自定义域名，不要删

## 每日更新方法（data/days.json）

在 `days` 数组**最前面**加一个新交易日，并把 `updated` 改成当天日期：

```json
{
  "date": "2026-11-10",
  "weekday": "周二",
  "sp500": { "close": 7520.93, "pct": -0.38 },
  "ndx": { "close": 27740.79, "pct": -0.60 },
  "headline": "一句话总结",
  "reasons": ["原因 1", "原因 2", "原因 3"],
  "sources": [{ "title": "来源名称", "url": "https://..." }]
}
```

规则：

- `date` 是美国交易日；`ndx` 是纳斯达克 100（不是纳斯达克综合指数）
- 数字必须来自当天的公开收盘报道，至少两个来源互相核对
- `reasons` 用简单的中文、自己的话写 3–4 条，面向投资初学者，专业词要顺带解释
- 只陈述事实，不写买卖建议，不预测走势
- 最多保留最近 60 个交易日
- 美股休市日不添加
