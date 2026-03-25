# rainman-travel

English | [中文](README.zh.md)

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) Skill for deep travel research. Dimensions grow from the city itself — not a fixed template forced onto every destination.

## What It Does

Input a city name, and Claude will:

1. **Profile the city** — identify its unique character from 11 possible research dimensions
2. **Launch 12 parallel agents** — deep-dive the selected dimensions with bilingual (CN/EN) web research
3. **Generate an org-mode knowledge document** — structured, source-backed, written as personal notes (not tourist copy)
4. **Cast two portable cards** (PNG) — a city overview infograph + a route reference card for your phone

## Dimension Pool

Not every city is an ancient capital. The skill dynamically selects 4–6 dimensions that fit:

| Dimension | Example Cities |
|---|---|
| Historical Layers | Xi'an, Luoyang, Nanjing |
| Museums | Xi'an, Sanxingdui |
| Ancient Architecture | Datong, Pingyao, Quanzhou |
| Archaeology | Anyang, Liangzhu |
| Religion & Belief | Lhasa, Wutaishan, Dunhuang |
| Food Culture | Chengdu, Chaoshan, Changsha |
| Maritime & Coastal | Weihai, Xiamen, Zhoushan |
| Natural Geography | Zhangjiajie, Jiuzhaigou |
| Ethnic & Folk Culture | Lijiang, Dali, Xishuangbanna |
| Modern & Contemporary | Shanghai, Shenzhen, Chongqing |
| Modern History | Weihai, Lushun, Yan'an |

**Practical Info** (transport, accommodation, tickets, seasonal tips) is always included — research without logistics is useless.

## Installation

### Option 1: Manual

```bash
git clone https://github.com/deusyu/rainman-travel.git
cp -r rainman-travel ~/.claude/skills/rainman-travel
```

### Option 2: Symlink

```bash
git clone https://github.com/deusyu/rainman-travel.git ~/path/to/rainman-travel
ln -s ~/path/to/rainman-travel ~/.claude/skills/rainman-travel
```

Restart Claude Code after installation.

## Usage

```
/rainman-travel 厦门
```
```
/rainman-travel 西安 -f 唐代
```
```
/rainman-travel 成都 3天
```
```
/rainman-travel 拉萨 -q
```

| Flag | Effect |
|---|---|
| `-f <topic>` | Focus on a specific theme (e.g. `-f 川菜`, `-f 甲午`) |
| `-q` | Quick mode — skip content analysis, research + doc only |
| `N天` | Specify trip duration for route planning (default 3 days) |

## Output

| File | Location | Format |
|---|---|---|
| Knowledge document | `~/Documents/notes/` | Org-mode (.org) |
| City overview card | `~/Downloads/` | PNG (1080px infograph) |
| Route reference card | `~/Downloads/` | PNG (1080px long card) |

## Dependencies

- [ljg-card](https://github.com/lijigang/ljg-skills) skill (for PNG card generation)
- Playwright (`npm install playwright && npx playwright install chromium` in ljg-card directory)

## Tested Cities

| City | Dimensions Selected | Key Findings |
|---|---|---|
| Weihai (威海) | History, Museums, Architecture, Archaeology, Humanities, Deep Content | Sino-Japanese War underwater archaeology (4000+ artifacts), Quanzhen Daoism birthplace |
| Xiamen (厦门) | Minnan Culture, Architecture, Food, Maritime, Religion, Contemporary | Amoy Deco style origin, satay sauce Nanyang adaptation, gongfu tea 11-step ceremony |

## Design Philosophy

> Every city carries its own way of being understood. Xi'an demands an archaeological lens. Chengdu demands a culinary one. Lhasa demands a spiritual one. The skill's job is to detect which lens fits, not to impose a universal framework.

## Credits

Inspired by [ljg-travel](https://github.com/lijigang/ljg-skills) by [@lijigang](https://github.com/lijigang). The original skill introduced the DBA (Desk-Based Assessment) methodology for cultural travel research. This version extends it with dynamic dimension selection, food/logistics coverage, and adaptive document structure.

## License

[MIT](./LICENSE)
