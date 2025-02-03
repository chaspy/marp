---
marp: true
---

<style>
  :root {
    --white: #ffffff;
    --text-black: #24243f;
    --text-sub: #808d96;
    --sapuri-blue: #0b41a0;
    --caution-pink: #de30ca;
    --action-green-plus: #36a4a1;
  }

  section {
    width: 1280px;
    height: 720px;

    font-size: 32px;
    line-height: 1.5;
    color: var(--text-black);
    background-color: var(--white);
    background-image: linear-gradient(
      180deg,
      var(--sapuri-blue) 8px,
      var(--white) 8px,
      var(--white) 100%
    );

    place-content: start start;
    padding-block: 68px;
    padding-inline: 100px;
  }

  section footer {
    display: none;
  }

  section::after {
    color: var(--text-sub);
    font-size: 60%;
    content: attr(data-footer) "\2003\2003" attr(data-marpit-pagination) " / "
      attr(data-marpit-pagination-total);
    inset: auto 40px 20px auto;
  }

  section.invert {
    color: var(--white);
    background: var(--sapuri-blue);
  }

  section.invert::after {
    color: inherit;
  }

  h1 {
    color: inherit;
    font-size: 1.3rem;
    font-weight: bolder;
    margin-block: 1rem;
    padding: 0;
  }

  h2 {
    color: inherit;
    font-size: 1rem;
    font-weight: bolder;
    margin-block: 0.5rem;
    padding: 0;
  }

  h3 {
    color: inherit;
    font-size: 1rem;
    font-weight: inherit;
    margin-block: 0.5rem;
    padding: 0;
  }

  :is(h1, section.agenda h2) em {
    color: var(--text-sub);
  }

  :is(h1, section.agenda h2) em::after {
    content: "\2002";
  }

  section.cover {
    color: var(--white);
    background: var(--sapuri-blue);

    display: grid;
    grid:
      "logo" auto
      "event-title" auto
      "title" 2fr
      "sub-title" 1fr
      / 1fr;
    gap: 0.5rem;
  }

  section.cover::after {
    display: none;
  }

  section.cover :is(h1, h2, h3, p) {
    margin: 0;
  }

  section.cover h1 {
    font-size: 1.7rem;
    place-content: safe center center;
  }

  section.cover h2 {
    font-weight: inherit;
  }

  section.cover h3 {
    font-size: 0.7rem;
  }

  section.agenda {
    display: grid;
    grid-template-columns: auto 1fr;
    grid-template-rows: repeat(8, auto);
    gap: 0 1.3rem;
  }

  section.agenda h1 {
    color: var(--sapuri-blue);
    font-size: 1.2rem;
    margin-block-start: 0.3rem !important;
    grid-row: 1 / -1;
  }

  section.agenda h1::after {
    content: "\2002|";
  }

  section.section-title {
    place-content: safe center center;
  }

  section.section-title h1 {
    font-size: 1.7rem;
  }

  section[data-marpit-advanced-background-split="right"] {
    padding-inline-end: 60px;
  }

  section.lead {
    place-content: safe center center;
  }

  section.lead h1 {
    font-size: 2.2rem;
    text-align: center;
  }

  section.lead h2 {
    font-size: 1.7rem;
    text-align: center;
  }

  section.lead p {
    text-align: center;
  }

  p,
  ul {
    color: inherit;
    margin-block: 0.5rem;
  }

  em {
    font-style: inherit;
  }

  :is(p, ul) strong {
    color: var(--sapuri-blue);
    font-weight: bolder;
  }

  :is(p, ul) strong em {
    color: var(--caution-pink);
    font-weight: bolder;
  }

  :is(p, ul) em {
    font-weight: bolder;
  }

  ul {
    padding-inline-start: 2rem;
  }

  li {
    margin-block: 0.5rem;
  }

  li::marker {
    color: var(--text-sub);
    font-weight: bolder;
  }

  ul {
    list-style-type: "→\2003";
  }

  ul > li > ul {
    list-style-type: "◆\2003";
  }

  ul > li > ul > li > ul {
    list-style-type: "⦁︎\2003";
  }

  ul > li > ul > li > ul > li > ul {
    list-style-type: "⚬\2003";
  }

  small {
    font-size: 0.7rem;
    display: block;
  }

  a {
    color: var(--action-green-plus);
    text-decoration: underline;
  }
</style>

<!-- _class: cover -->

![w:200](data:image/png;base64,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)

### Event title

# タイトル

## @quipperman

---

<!-- _class: agenda -->

# Agenda

## _01_ セクション1

## _02_ セクション2

## _03_ セクション3

## _04_ セクション4

---

<!-- _class: section-title -->

# _01_ セクションタイトル

---

# @quipperman

195X年4月、範馬勇一郎の息子として生を享ける。この日、全世界の国家指導者達は一様に、東洋の国にとてつもない兵器が生まれるということを直感で理解し、核兵器の保有を決意させたとまで言われている。これを裏付けるように、勇次郎の自我は赤子のそれではなく、出胎時、自らを取り上げる産婆に対してテレパシーのような威圧を送って腰を抜かせ、またその直後には母親の乳房に噛付いて授乳を強要し、さらにはどこからか現れたヤドクガエルを素手で握り殺した。母親は勇次郎の出産後、出家して仏門に帰依しており、「最初で最後の子でした」と述べている。

---

# 箇条書き

- Text
  - text

---

# テキストサイズ

# 見出しはこのサイズ(24pt)&ボールドでお願いします

文章はこのサイズでお願いします。(18pt)
強調したい文字はこのように**サプリブルー＆ボールド**で表現してください。どうしてももっと目立たせたい場合は、**_サプリピンク＆ボールド_** も可としますが、多用は避けてください（却ってポイントがわからなくなりがちです）。

<small>
注釈であればこのサイズまでOKです。(13pt)<br>
ただし、奥の人はあまりはっきりと視認できない可能性があります。
</small>

---

# タイトル

画像がある場合は→くらいのバランスで挿入してください。

![bg auto right](https://placehold.jp/512x512.png)

---

<!-- _class: lead -->

# 重要ポイントはこのように大きく中央揃えで表現しましょう。

---

<!-- _class: lead invert -->

全面に画像を配置する場合は上部のライン及び
フッターを削除してOK。

![bg auto](https://placehold.jp/4c5263/596076/1280x720.png)

---

<!-- _class: lead -->

## ご清聴ありがとうございました
