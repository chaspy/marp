---
marp: true
theme: studysapuri
---

<!-- _class: cover -->

### LangChain Meetup Tokyo #5

# Slack Platform(Deno) の RAG 実装で LangChain(js) を使うの挫折した話

## Takeshi Kondo / @chaspy 

---

# 自己紹介

- Takeshi Kondo / @chaspy
  - Director of Engineering / 開発部長
  - 『スタディサプリ小学・中学・高校・大学受験講座』担当
  - Recruit co., ltd
- 先週月曜から今週火曜までカナダに行ってきました🇨🇦
  - お土産のチョコレートを持ってきたので食べてください！

![bg right:38% h:400](../images/chaspy.jpg)

---

# 謝罪

- LangChain Meetup なのに挫折話で本当すみません...
  - ぜひこうしたらできるよみたいな話教えてください...
  - 本当は Agentic RAG の実装話をしたかったが進捗ダメです

---

# 既存の Slack Bot + RAG

- Azure 上で構築
- chat/completions API で datasource を指定
- Slack Next Gen Platform (Deno/TypeScript)上で実行
- 詳細は過去資料参照
  - [「現場で実践！RAG活用術 Lunch LT ― 運用して分かった"つらみ"とその対策」で登壇してきました＆質問の回答 #RAG_Findy](https://blog.studysapuri.jp/entry/2024/07/17/feedback-cycle-practice-through-simplified-assessment-of-rags)

---

# 既存の Slack Bot + RAG

![h:400](./image1.png)

<br>
<br>
graph LR
    Slack[Slack platform] --> |質問|C

    subgraph Azure
        C[Azure OpenAI]
        C -->|Find DataSource| D[AI Search]
        E[Blob Storage]
        H[index]
        D-->|VectorSearch|H
    end

    G[GitHub] -->|Upload|E
    E -->|indexing|H


---

# 既存の Slack Bot + RAG の課題

- chat/completion API + DataSource なので、例えば index は1つしか指定できない
- 問い合わせ内容からクエリ生成や、問い合わせ内容に応じたフィルタリング・ソートなどができない
- 社内で使われるにつれ、より細かい制御 = Agentic RAG を作りたくなってきた
- 実装量増えるし、LangChain 使ってみよう

---

# Thank You!

- Takeshi Kondo / @chaspya
  - Director of Engineering / 開発部長
  - 『スタディサプリ小学・中学・高校・大学受験講座』担当
  - Recruit co., ltd

![bg right:38% h:400](../images/chaspy.jpg)
