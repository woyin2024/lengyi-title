<div align="center">

# Title.skill
A Skill purpose-built for titling new-media articles.<br>
**Writing patterns hand-picked from 100+ viral articles — not clickbait tricks.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)[![Type](https://img.shields.io/badge/Type-Agent%20Skill-success)](./SKILL.md)[![Corpus](https://img.shields.io/badge/Corpus-TOP50%20Titles-orange)](./references/corpus.md)

<p align="center">
  <a href="./README.md" style="display:inline-block;padding:6px 18px;background:#4f46e5;color:#fff;border-radius:6px 0 0 6px;text-decoration:none;font-weight:600;">English</a> <a href="./README.zh.md" style="display:inline-block;padding:6px 18px;background:#f3f4f6;color:#4b5563;border-radius:0 6px 6px 0;text-decoration:none;font-weight:600;">简体中文</a>
</p>

</div>

<p align="center">
  <img src="public/产品图.png" width="100%" alt="title.skill product overview" />
</p>

---

## 🌟 Why this Skill?

Anyone who writes for WeChat knows the brutal truth: **great content with a weak title gets zero clicks.**

I run 「沃垠AI」(Woyin AI), a top AI tech media account in China. In 2026, the account published 100 original articles, from which we picked the TOP50 performers. None of those titles relied on clickbait words like "SHOCKING" or "revealed", and none was written on a whim.

So I pulled all 50 titles together with their reads, shares and share rates, and dissected each one: character counts, sentence segmentation, brand naming, number usage, punctuation frequency, word choices... Finally I **reverse-engineered the findings into a complete title-writing methodology, and packaged it as this Skill**.

It is not another listicle of hollow "headline writing tips". It is a **data-backed, verifiable, executable rule system** — behind every rule stand real reads, shares and comment data.

> If you also believe a great title is statistics, not inspiration — come use it, fork it, and star it.

---

## ✨ What it does

Feed it an article draft, a one-line topic, or an old title to optimize, and it outputs:

- **A three-platform title pack** with 5 WeChat article titles, 5 shared Xiaohongshu/WeChat-cover titles, and 5 Douyin titles
- **Platform-specific lengths**: 22-30 characters for WeChat articles, 20 max for Xiaohongshu/WeChat covers, and a recommended 8-18 with a 20-character delivery cap for Douyin
- **One reusable short-title set** for both WeChat cover artwork and Xiaohongshu, with no duplicated variants
- **Exact character count, paradigm, and growth goal** attached to every candidate
- **A top recommendation with reasoning** — why that title fits this article best
- **Clear growth-goal labels**: every candidate states whether it targets raw reads or shares/follower growth, without duplicating titles across groups
- **Old-title diagnosis**: for a rewrite request, it first points out the concrete problems (too long / no brand named / no number / redundant second half) in one or two sentences, then gives candidates — so you learn the logic, not just the result

## 🧠 Core insight: reads and follower growth are different goals

The soul of this Skill is a counter-intuitive split found in the TOP50 data:

> **Title types with the highest reads usually have low share rates; titles with high share rates tend to drive more follower growth.**

| Article type | Typical reads | Share rate | Notes |
| - | - | - | - |
| Tutorials / listicles | 15K-80K | **13-19%** | Share-rate ceiling; readers love saving them, great for follower growth |
| New-model news | **100K-240K** | 4-6% | Read ceiling; driven by timeliness |
| First-person builds | 10K-55K | 3-8% | Backed by persona and "cost"; the follower-growth secret |
| Hands-on comparisons | 15K-30K | 2-4% | First choice for real side-by-side tests |
| Industry takes / disruption narratives | 25K-145K | 1.5-3% | Big reads, little follower growth |

So its first step is never brainstorming words — it is deciding the goal: **are we chasing reads, or shares and followers?** Different goals lead to completely different paradigms.

## 🛠️ Architecture: how it works

The Skill uses an "instructions + reference corpus" progressive-disclosure structure, with three files doing three jobs:

```
┌────────────────────────────────────────────────────────────┐
│                        SKILL.md                            │
│  Main instructions: a 4-step workflow + output contract     │
│  ┌──────────────────────────────────────────────────────┐  │
│  │ Step 1  Set the goal → reads or shares/followers?     │  │
│  │ Step 2  Pick paradigms → 6 paradigms, 2-3 drafts each │  │
│  │ Step 3  Hard rules → length / structure / naming /    │  │
│  │         numbers / punctuation                         │  │
│  │ Step 4  Self-check → 7-item list, rewrite on any "no" │  │
│  └──────────────────────────────────────────────────────┘  │
└────────────────────────────────────────────────────────────┘
          │                                    │
          ▼                                    ▼
┌───────────────────────┐        ┌───────────────────────────┐
│ references/lexicon.md │        │  references/corpus.md     │
│ High-frequency lexicon│        │ Full corpus: 50 titles    │
│ — decides the "taste" │        │ with reads/shares data    │
│ Read before drafting  │        │ and paradigm labels       │
└───────────────────────┘        └───────────────────────────┘
```

### The six title paradigms

Every paradigm is induced from the corpus and annotated with real examples:

| Paradigm | Formula | Representative title |
| - | - | - |
| 1 Launch news | Positioning + brand name + "is here!" + lowest-barrier promise | 中国版Codex来了，Qwen3.7-Max免费用！ |
| 2 Hands-on tutorial | Intensity marker + topic + one-stop promise | 万字干货！Agent Skills从入门到精通 |
| 3 Listicle | "The N best X" + contrarian verdict | 最值得推荐的20个宝藏Skills，小众但真香 |
| 4 First-person build | Quantified cost + what I built + free & open-source | 烧了10亿Token，我做了一个Markdown编辑器，开源免费 |
| 5 Comparison test | Real test + 3-4 product names + surprising verdict or cost | 横评Opus 4.8、GPT-5.5、DeepSeek V4，356元测出来的真实排名 |
| 6 Industry take | Time/scale anchor + disrupted thing + emotion word | 40年没变过的Email，被腾讯重新定义了 |

### Hard rules (statistical facts, not style preferences)

- **Length**: WeChat gets three 22-27-character and two 28-30-character titles; Xiaohongshu/WeChat cover titles are capped at 20; Douyin targets 8-18 and is capped at 20
- **The first 15 characters must stand alone**: WeChat's list view truncates titles, so the strongest information goes first
- **Name names**: 92% of the top titles mention a specific model/product, with version numbers (Qwen3.7-Max, never "a certain LLM")
- **Numbers**: 56% contain Arabic numerals; non-round numbers like 8 and 16 feel more credible than round ones — they imply you actually counted
- **Punctuation**: 80% use commas to split into 2-3 segments; at most one exclamation mark; question marks only for genuine pain points
- **Banned words**: zero occurrences of empty clickbait like "震惊" (shocking), "揭秘" (revealed), "不看后悔" (you'll regret not reading), "封神了" across the entire corpus

### Dual reference files

- **`lexicon.md` (the lexicon)**: decides the "taste" of a title. Opening burst words, barrier/price promises, tutorial intensity markers, first-person verbs (deliberately colloquial: 搓了一个, 跑通了, 烧了), suspense endings, and the banned-word list. **Required reading before drafting** — one wrong word and the title smells like generic AI output.
- **`corpus.md` (the corpus)**: the full 50-title leaderboard with character counts, reads, shares, share rates, paradigm labels and publish dates. When unsure how a paradigm lands in practice, look up real examples here.


---

## 🚀 Quick start

### Installation

```
# Clone the repository
git clone https://github.com/woyin2024/lengyi-title.git
```

Put the whole `lengyi-title` folder into your agent's Skills directory:
- **Claude Code**: `C:\Users\Administrator\.claude\skills`
- **Codex**: `C:\Users\Administrator\.codex\skills`
- **WorkBuddy**: `~/.workbuddy/skills`
- **Other agents**: follow the Skill installation guide of your tool

### Usage

No rules to memorize. Just ask in natural language:

```
"Help me title this WeChat article: [paste the draft]"
"Optimize this title for me: [old title]"
"I'm writing a listicle about hidden Doubao tricks, mainly for follower growth — give me a few titles"
"Give me one set of reusable WeChat-cover/Xiaohongshu titles under 20 characters"
"Give me 5 title options each for WeChat, Xiaohongshu, and Douyin"
"Use the lengyi-title skill to title this article"
```

The agent loads the Skill automatically and outputs a three-platform title pack following the workflow: set goal → pick paradigms → adapt by platform → validate lengths → self-check.

---

## 📜 License

This project is open-sourced under the [MIT License](LICENSE).

Free to use, modify and distribute; for commercial use please obtain authorization (WeChat: lengcp2013). May your next 100K-read article start with a title from here.

---

## 👤 About the author

**Lengyi (冷逸)**, blogger of 「沃垠AI」, a top AI tech media in China. A vibe-coding developer who can't write code, obsessed with Prompts, Skills and Agents.

- **Unified handle across platforms**: 沃垠AI
- **Tags**: product & ops background, in-depth AI reviews, super OPC
- **Content matrix**: WeChat Official Account, Xiaohongshu, Zhihu, GitHub, Bilibili, X, etc.

Follow the WeChat Official Account「沃垠AI」for more AI insights:
<p align="center">
  <img src="public/公众号二维码.png" width="90%" alt="沃垠AI WeChat Official Account QR code" />
</p>

---

<div align="center">

### If it helped you, a ⭐ means a lot

**Thank you 🙏**

</div>
