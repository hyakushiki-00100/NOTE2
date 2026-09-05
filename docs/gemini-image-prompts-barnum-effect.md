# Gemini用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「バーナム効果」用イラスト一式
**確定タイトル**: 「星占いが「当たってる」と感じるのはなぜ? 「バーナム効果」、名前の由来は心理学者ではなく興行師だった」(50字)
**用途**: Gemini(画像生成)にそのまま貼り付けて使うプロンプト
**運用変更**: これまでは ChatGPT に貼り付けるプロンプトを用意していたが、ChatGPT が生成制限に達したため、
今回から **画像生成先を Gemini に切り替える**。プロンプトの書き方自体は変えていない(自然言語での描写・
共通スタイル指定・文字入れ指示は Gemini でもそのまま通じる想定)。
**方針**: 過去記事(猫は液体か・コリオリの力・モスキート音・フェルミのパラドックス)と同様、**文字入り版のみ**を用意する。

---

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | ✅ 既存の `profile/icon.png`(500×500・正方形、確認済み)をそのまま流用。作り直さない |
| 記事カバー | 🔲 プロンプト作成済み・Gemini での生成待ち(`covers/barnum-effect.png` として保存予定) |
| 解説イラスト1(同じ1枚の紙に、何人もの学生が驚く) | 🔲 プロンプト作成済み・生成待ち(`illustrations/barnum-01-same-sheet.png`) |
| 解説イラスト2(1948年実験→1949年論文→1956年命名、の年表) | 🔲 プロンプト作成済み・生成待ち(`illustrations/barnum-02-timeline.png`) |

すべて未生成。生成後、下記「生成後のチェックリスト」に沿って検証し、Opus QA(`note-qa`)にかけること。

---

## 共通スタイル指定(毎回のプロンプト冒頭に付けると絵柄が揃います)

```
Flat, warm, friendly children's educational illustration style (like a Japanese picture book for
elementary schoolers). Simple flat shapes, soft rounded corners, no photorealism, no realistic
human faces. Clean vector-like line art with a warm brown outline (#483628). Color palette limited
to: cream background (#FBF3E4), terracotta orange (#E08454, shadow #BF673C), deep teal
(#3A6960, light teal #92B5AB). Cheerful and gentle mood, appropriate for children.
```

---

## 1. 記事カバー

本文の核となるフック(星占い・性格診断が、実は誰にでも当てはまる言葉でできている。名前の由来は
心理学者ではなく19世紀の興行師)を絵にする。タイトルは確定済みなので、そのまま画像内に焼き込む。

**注意(事実の取り扱い)**: P.T.バーナムは実在の歴史上の人物のため、特定の実写風の肖像(似顔絵)として
描かない。「19世紀風の興行師・サーカスの呼び込み役」を思わせる**一般的なアーキタイプの人物像**
(シルクハット・口ひげ・ステッキなど、興行師を連想させる記号的な意匠)に留め、実在の人物の写実的な
肖像だと誤解されないようにする。生没年など本文に無い具体的な情報は描き込まない。

```
A wide horizontal illustration (aspect ratio approximately 16:8.4), flat warm children's book style.
In the main foreground, a single sheet of paper (or a small scroll) covered in a few soft, sparkly,
wavy abstract "text" lines (NOT real readable words, just gentle squiggly lines suggesting writing),
decorated with small star and moon motifs to evoke a horoscope/personality-quiz page. Around this
single paper, place 3 different simple character silhouettes (clearly distinct from each other —
different simple hairstyles/heights/silhouette shapes, no realistic faces, no faces at all is fine)
each looking at the SAME paper with a delighted, surprised expression — small sparkle icons, a tiny
heart, or a small "!" near each character's head, to show each of them feels "this is exactly me"
about the very same page. A soft warm night sky with a few small stars and a crescent moon fills the
upper background, reinforcing the horoscope theme.
In one small back corner of the image (clearly secondary, much smaller than the main paper and
characters), include a small, generic, old-fashioned showman/circus-ringmaster silhouette archetype
(simple top hat, mustache, cane) — a symbolic hint at "the name's origin is a showman," NOT a
realistic portrait of a specific historical person. Keep this figure small and subordinate to the
main scene.
[共通スタイル指定を貼り付け]
Include a title at the top of the image in bold, clearly legible Japanese text: 「星占いが「当たってる」と感じるのはなぜ? 「バーナム効果」、名前の由来は心理学者ではなく興行師だった」.
CRITICAL — this title is long (50 characters, noticeably longer than a typical short headline), so it
must be laid out across MULTIPLE LINES with a small enough font to comfortably fit without crowding
or overlapping the illustration below. Suggested balanced line breaks (4 lines):
line 1: 「星占いが「当たってる」と」
line 2: 「感じるのはなぜ?」
line 3: 「「バーナム効果」、名前の由来は」
line 4: 「心理学者ではなく興行師だった」
If 4 lines still feel crowded, 5 lines with similarly natural phrase breaks is also acceptable — do
not force it onto 2–3 lines, as the font would become too small or the text would overflow. The
title text must be crisp, correctly formed Japanese characters (not garbled), in the dark brown color
(#483628), positioned in the upper area with calm, uncluttered space behind it so it does not overlap
the character illustration below.
```

**生成後の確認ポイント**: タイトルが4〜5行に収まり、文字が窮屈になっていないか。1行が極端に長くなっていないか(目視で確認)。3人のキャラクターが「同じ1枚の紙」に対してそれぞれ驚き・共感の表情をしているか(紙が複数枚に分かれて見えると本文の趣旨とずれるため、紙は1枚であることが明確か確認)。興行師のシルエットが小さく背景的な扱いになっており、実在の人物の写実的な肖像に見えていないか確認。

---

## 2. 解説イラスト1: 同じ1枚の紙が、何人もの学生に配られる(1948年の実験)

本文該当箇所(「1948年、ある教室で行われた実験」節)の要旨: 心理学者フォアラーが、自分の授業の
学生たちに性格診断のテストを受けてもらった。学生は「1人ずつ違う診断結果」だと説明されたが、
実際には**全員に同じ1枚の文章**(市販の星占いの本から抜き出した文をつなげたもの)が配られていた。
学生は「自分の性格をどれくらい正確に表しているか」を5点満点でたずねられ、平均は4.26点だった。

**重要(本文にない事実を追加しない)**:
- 本文の学生数は39人だが、イラストで正確に39人の見分けられる人物を描くことは現実的でなく、
  かつ小さい図で人数を強調しすぎると「大人数」に誇張して見えるおそれがある。**画像内に学生の人数を
  示す数字は入れない。** 教室の一部を切り取ったような、無理のない少人数(5〜6人程度)のグループで
  「同じ教室にいる学生たち」を代表させ、正確な人数の主張はしない。
- 画像内に含めてよい数字は **4.26 のみ**(本文にある平均点)。それ以外の数値(人数・年齢・点数の
  内訳など)を新たに書き加えない。

```
A single illustration, flat warm children's book style: a simple classroom scene. 5 to 6 simple
student characters (varied simple hairstyles/heights, no realistic faces, seated at desks or standing
in a small cluster) are each holding up an identical sheet of paper — every sheet must look exactly
the same (same shape, same soft wavy abstract "text" lines on it, same small star/moon doodle in the
corner of the page) to make clear they all received the SAME single sheet, not different ones.
Each student has a surprised, delighted expression (wide eyes, small sparkle or "!" icon near their
head) as if reacting "this describes me exactly!" — but keep the group small and classroom-sized, NOT
a huge crowd; do not depict more than about 6 distinct student figures, and do not write any numeral
for a headcount anywhere in the image.
At the top of the image, include a short Japanese caption: "同じ1まいの紙なのに、みんな「当たってる」と思った".
Optionally, near the bottom of the image, include one small tag/label reading in Japanese
"5点満点中 平均 4.26点" — this is the ONLY number allowed to appear anywhere in this image. Do not add
any other digits, ages, or scores.
[共通スタイル指定を貼り付け]
All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read for
children, in the dark brown color (#483628).
```

**生成後の確認ポイント**: 全員が持っている紙が「同じ1枚」に見えるデザインになっているか(紙ごとに柄が違って見えたら失敗)。学生の人数を示す数字が画像内に無いか(あれば本文の39人と食い違うリスクがあるため削除・作り直す)。画像内の数字が「4.26」以外に増えていないか確認する(4.26という数字自体が正しく描画されているか、桁が崩れていないかも拡大して確認)。

---

## 3. 解説イラスト2: 1948年の実験 → 1949年の論文発表 → 1956年の命名、という年表

本文該当箇所(「「バーナム効果」というもう一つの呼び名」節)の要旨:
1948年にフォアラーが実験を実施 → 1949年に論文として発表 → 1956年に別の心理学者ポール・ミールが
この現象を「バーナム効果」と名付けた(名前の由来は19世紀の興行師P・T・バーナム)。

**重要(本文にない事実を追加しない)**: 年表に描くのは本文にある **この3つの出来事のみ**
(1948年実験・1949年論文発表・1956年ミールによる命名)。P・T・バーナムの生没年や、その他の
具体的な数値・日付を新たに書き加えない。バーナムの興行師としての一般的なイメージ(シルクハット等の
記号的な意匠)を1956年のノードに小さく添えるのは可(名前の由来を示すため)だが、実在の人物の
写実的な肖像として描かない。

```
A single illustration, flat warm children's book style: a simple horizontal timeline running from
left to right, with a clean line connecting exactly THREE labeled points in this order (left to
right, chronological, do not reorder):

1) LEFTMOST point, labeled "1948年": a small classroom/desk icon with a single sheet of paper, and a
   short caption below in Japanese "教室で じっけん" (Forer's classroom experiment).
2) MIDDLE point, labeled "1949年": a small folded document/paper-with-text icon (representing a
   published paper, not a specific readable title), and a short caption below in Japanese
   "ろんぶんで はっぴょう" (the experiment is published as a paper).
3) RIGHTMOST point, labeled "1956年": a small "naming/tag" icon (e.g. a name-tag or a spotlight/stage
   curtain shape) paired with a small, generic, old-fashioned showman silhouette archetype (simple
   top hat, mustache — symbolic only, NOT a realistic portrait of a specific historical person), and
   a short caption below in Japanese "「バーナム効果」と 名づけられた" (a different psychologist,
   Meehl, names the effect after the showman P. T. Barnum).

A simple arrow or connecting line should visually lead from point 1 to point 2 to point 3, left to
right, making the chronological order unambiguous. Do NOT add any other dates, numbers, or events to
the timeline — exactly these three points, in this order, with no additional numeric details (e.g. no
birth/death years for the showman, no other statistics).
[共通スタイル指定を貼り付け]
All Japanese text and year numerals (1948年 / 1949年 / 1956年) must be crisp, correctly formed
characters and digits (not garbled or swapped), large and easy to read for children, in the dark
brown color (#483628).
```

**生成後の確認ポイント**: 3つのノードが左→右の順に「1948年→1949年→1956年」の時系列で並んでいるか(順番の入れ替わりに注意。特に1948/1949/1956は数字が似ているため、桁の誤描画・入れ替わりが起きやすい。拡大して1文字ずつ確認する)。ラベルの内容が本文と一致しているか(教室で実験/論文で発表/バーナム効果と命名、の3つ以外の出来事や数値が増えていないか)。1956年のノードに添えた興行師のシルエットが、生没年など本文に無い情報を伴わず、かつ写実的な肖像に見えていないか確認する。

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
  ```bash
  python3 -c "from PIL import Image;print(Image.open('covers/barnum-effect.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/barnum-01-same-sheet.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/barnum-02-timeline.png').size)"
  ```
- [ ] 日本語テキスト(タイトル・ラベル・キャプションとも)が崩れていないか拡大して確認
- [ ] カバーのタイトルが4〜5行に収まり、窮屈になっていないか確認(50字と長めのタイトルのため特に注意)
- [ ] カバー: 興行師のシルエットが小さく背景的な扱いで、実在の人物の写実的な肖像に見えていないか確認
- [ ] イラスト1: 学生全員が持つ紙が「同じ1枚」に見えるデザインになっているか(柄が食い違っていたら失敗)
- [ ] イラスト1: 画像内の数字が「4.26」以外に増えていないか、また学生の人数を示す数字が入っていないか確認(本文の39人と食い違うリスクを避けるため、人数は数字で示さない方針)
- [ ] イラスト2: ノードの並びが左から「1948年→1949年→1956年」の順になっているか(年号の桁が入れ替わっていないか1文字ずつ確認)
- [ ] イラスト2: 描かれている出来事が本文の3つ(教室で実験・論文発表・ミールによる命名)以外に増えていないか。バーナムの生没年など本文に無い数値が追加されていないか確認
- [ ] プロフィールアイコンは既存の `profile/icon.png` をそのまま使い、作り直していないか確認

保存先の目安: `covers/barnum-effect.png` /
`illustrations/barnum-01-same-sheet.png`(同じ紙に驚く学生たち)/
`illustrations/barnum-02-timeline.png`(1948→1949→1956の年表)

生成後、本文中の📎マーカーに対応するファイルパスが一致していることを確認してください(マーカー自体を
実画像への記法に差し替えるのは `note-formatter` の担当です):
- `illustrations/barnum-01-same-sheet.png` … 本文「1948年、ある教室で行われた実験」節末の📎マーカーと一致
- `illustrations/barnum-02-timeline.png` … 本文「「バーナム効果」というもう一つの呼び名」節末の📎マーカーと一致
