# rainman-travel

[English](README.md) | 中文

一个 [Claude Code](https://docs.anthropic.com/en/docs/claude-code) Skill，用于深度旅行研究。维度从城市本身生长出来，而不是把所有城市塞进同一个模板。

## 它做什么

输入一个城市名，Claude 会：

1. **城市画像** — 从 11 个研究维度池中识别这座城市的独特性格
2. **12 个并行 Agent 深度研究** — 中英文双语 Web 搜索，覆盖选定维度
3. **生成 org-mode 知识文档** — 结构化、有据可查、给自己写的笔记（不是导游词）
4. **铸造两张便携卡片**（PNG）— 城市概览信息图 + 参观路线速查长图

## 维度池

不是每座城市都是古都。Skill 会动态选择 4-6 个最匹配的维度：

| 维度 | 典型城市 |
|---|---|
| 历史分层 | 西安、洛阳、南京 |
| 博物馆重点 | 西安、三星堆 |
| 古建遗存 | 大同、平遥、泉州 |
| 考古发现 | 安阳、良渚 |
| 宗教与信仰 | 拉萨、五台山、敦煌 |
| 美食体系 | 成都、潮汕、长沙 |
| 海洋与海岸 | 威海、厦门、舟山 |
| 自然地理 | 张家界、九寨沟 |
| 民族与民俗 | 丽江、大理、西双版纳 |
| 近现代史 | 威海、旅顺、延安 |
| 当代城市 | 上海、深圳、重庆 |

**实用信息**（交通、住宿、门票、当季贴士）始终包含——研究再深，不知道怎么去也白搭。

## 安装

```bash
git clone https://github.com/deusyu/rainman-travel.git
cp -r rainman-travel ~/.claude/skills/rainman-travel
```

重启 Claude Code 生效。

## 使用

```
/rainman-travel 厦门
```
```
/rainman-travel 西安 -f 唐代
```
```
/rainman-travel 成都 3天
```

| 参数 | 效果 |
|---|---|
| `-f <主题>` | 聚焦特定主题（如 `-f 川菜`、`-f 甲午`） |
| `-q` | 快速模式，跳过内容提炼 |
| `N天` | 指定行程天数（默认3天） |

## 产出

| 文件 | 位置 | 格式 |
|---|---|---|
| 知识文档 | `~/Documents/notes/` | Org-mode (.org) |
| 城市概览卡 | `~/Downloads/` | PNG 信息图 |
| 路线速查卡 | `~/Downloads/` | PNG 长图 |

## 设计理念

> 每座城市自带它该被研究的方式。西安需要考古视角，成都需要美食视角，拉萨需要宗教视角。Skill 的工作是发现哪个视角合适，而不是强加一个通用框架。

## 致谢

灵感来自 [@lijigang](https://github.com/lijigang) 的 [ljg-travel](https://github.com/lijigang/ljg-skills)。原版引入了考古学 DBA（Desk-Based Assessment）方法论做文化旅行研究。本版在此基础上增加了动态维度选择、美食/实用信息覆盖和自适应文档结构。

## 许可

[MIT](./LICENSE)
