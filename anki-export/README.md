# Anki 导入说明

## CSV 文件清单

| 文件 | 内容 | 卡数 |
|---|---|---|
| `linxos.csv` | 凝思操作系统 | 104 |
| `dm8.csv` | 达梦数据库 | 107 |
| `all-杭州培训.csv` | 全部合并 | 211 |

CSV 列(无表头,3 列):
1. 正面(题目 + 提示)
2. 背面(答案 + 解释 + 记忆钩子)
3. 标签(`杭州培训::凝思::用户管理` 这种层级标签 + `weak` 标签标记薄弱题)

## 导入步骤(电脑端 Anki Desktop)

1. 装 [Anki Desktop](https://apps.ankiweb.net/) 如果还没装
2. 打开 Anki → **文件 → 导入** → 选 `all-杭州培训.csv`
3. 弹出导入设置:
   - **Note Type**: `Basic`(基本)
   - **Deck**: 新建 `杭州培训` (或选已有)
   - **字段映射**: 字段 1 → Front, 字段 2 → Back, 字段 3 → Tags
   - **Allow HTML in fields**: 勾选(因为答案里有 `<code>` `<br>` 标签)
4. 点 Import,完成

## 同步到手机

1. 注册 [AnkiWeb 账号](https://ankiweb.net/) (免费)
2. Anki Desktop 右下角点 **Sync** 同步到 AnkiWeb
3. 手机装:
   - iOS: **AnkiMobile**(¥168 一次买断,官方)
   - Android: **AnkiDroid**(免费)
4. 手机 app 登录 AnkiWeb → 同步 → 看到 `杭州培训` 牌组

## 优先刷"薄弱"标签

Anki 里搜索:
```
tag:weak
```

会过滤出今晚已标的 49 道薄弱题(凝思 28 + 达梦 21)。先把这些刷透。

## 题库更新后怎么重新导入

1. 我重新跑导出脚本 → 生成新 CSV(覆盖旧的)
2. `git pull` 拉最新
3. Anki 重新 Import,选「**Update existing notes when first field matches**」(根据正面文本去重更新)

## 字段细节(给好奇的)

- **正面** = `q + <小字>提示: hint</小字>`
- **背面** = `答案列表 + 解释 + 记忆钩子`
- **薄弱标签** = 答错过的题加 `weak` + `weak_count_N` (N 是错的次数)

