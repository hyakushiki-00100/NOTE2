# ChatGPT用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「フェルミのパラドックス」用イラスト一式
**確定タイトル**: 「宇宙人は、なぜ見つからないの? 「フェルミのパラドックス」、実は本人は論文もメモも残していない」(47字)
**用途**: ChatGPT(画像生成)にそのまま貼り付けて使うプロンプト
**方針**: 過去3記事と同様、**文字入り版のみ**を用意する。

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | ✅ 既存の `profile/icon.png`(500×500)をそのまま流用。作り直さない |
| 記事カバー | ⚠️ 生成済みだが Opus QA で FAIL(1行目タイトルの文字上部が画像上端で切れている)。下記の修正版プロンプトで**再生成が必要** |
| 解説イラスト1(宇宙の年齢・恒星数・銀河の年齢のスケール比較) | ⚠️ 生成済みだが Opus QA で FAIL(3枚目パネルのキャプションだけでは「銀河横断に100億年以上かかる」と誤読され、本文の「移動時間≪銀河の年齢」という比較の論旨が反転して見える)。下記の修正版プロンプトで**再生成が必要** |
| 解説イラスト2(3つの仮説を対等に並べた図) | ✅ 生成済み・Opus QA PASS(`illustrations/fermi-paradox-hypotheses.png`) |

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

## 1. 記事カバー 【要再生成・修正版】

本文の核となるフック(星がたくさんあり、時間も十分長いのに、宇宙人からの連絡が一つも無い)と、
タイトルの見どころ(フェルミ本人は論文もメモも残していない、という意外性)の両方を絵にする。
タイトルは確定済みなので、そのまま画像内に焼き込む。

**修正理由(Opus QAで指摘・FAIL)**: 旧版は1行目のタイトル文字の上部が画像の上端で切れていた
(既出3記事のカバーはいずれも上端に余白があり、本カバーだけの退行)。タイトル全体をもう少し
下げて、上に十分な余白を確保して再生成する。

```
A wide horizontal illustration (aspect ratio approximately 16:8.4), flat warm children's book style.
Background: a calm night sky full of many small warm-toned stars, filling most of the upper area.
In the lower-center/left area, a single simple, friendly, generic cartoon-style physicist character
(NOT a realistic portrait or likeness of any specific real historical person — a generic, simple,
round-faced character with no identifiable real facial features), seated at a small round lunch
table, looking up at the night sky with a curious/puzzled expression. A small simple speech bubble
near the character reads in Japanese "みんな、どこにいるんだ?".
On the table in front of the character, draw a small blank open notebook with empty, unwritten pages
and a small pencil resting on it (clearly empty pages, no scribbles), symbolizing that this person
left no written notes about the question.
Far in the background sky, among the stars, include ONE tiny, cute, non-scary stylized alien
silhouette (simple rounded shape, no realistic or scary features) half-hidden behind a distant small
star or planet shape, playfully small and easy to miss — a subtle visual nod to the unanswered
question, NOT asserting that aliens definitely exist (it should read as ambiguous/playful, not as a
confirmed sighting).
[共通スタイル指定を貼り付け]
Include a title at the top of the image in bold, clearly legible Japanese text, broken into exactly
3 lines with these natural phrase breaks (do not break mid-word):
Line 1: 「宇宙人は、なぜ見つからないの?」
Line 2: 「フェルミのパラドックス」、
Line 3: 実は本人は論文もメモも残していない
This title is long (47 characters total), so keep the font small enough that all 3 lines comfortably
fit within the image width without touching the edges or overlapping the night-sky scene below.
CRITICAL: leave a generous empty margin (at least 8% of the image height) between the very top edge
of the image and the top of line 1's characters — the title block must NOT start right at the top
edge, and no part of any character (including diacritical marks like "゛") may be cropped or touch the
top border. Position the whole 3-line title block starting noticeably below the top edge, with calm,
uncluttered space (plain cream or dark sky background, no busy stars) directly behind it so it stays
crisp and readable. The title text must be crisp, correctly formed Japanese characters (not garbled),
in the dark brown color (#483628).
```

**生成後の確認ポイント**: タイトル1行目の文字の上端が画像の一番上で切れていないか(必ず拡大して確認する。
前回はここが切れていてFAILになった)。タイトルが3行に収まり、どの行も窮屈になっていないか(47字と長いため
特に確認)。物理学者キャラクターが実在の人物の写実的な肖像に見えていないか(生成モデルが実在の人物に寄せて
しまうことがあるため、あくまで一般的な子ども向けキャラクターになっているか確認)。ノートが「空白」である
こと(=論文もメモも残していない、というタイトルの見どころ)が絵から読み取れるか。宇宙人のシルエットが
主役にならず、あくまで背景の小さな遊び要素にとどまっているか。

---

## 2. 解説イラスト1: 宇宙の年齢・天の川銀河の恒星の数・銀河の年齢のスケール比較 【要再生成・修正版】

本文該当箇所(L44〜66)の要旨: 宇宙が誕生してから約138億年。天の川銀河には1000億〜4000億個もの星がある。
銀河の年齢は100億年以上あり、銀河の端から端まで移動するのに何百万年かかっても、その長さと比べれば短い。
これだけの時間と数があるのに、誰も来ていない・電波も届いていない、という不思議につながる図。

**修正理由(Opus QAで指摘・FAIL)**: 旧版のカード3(ロケット+目盛りバー+「銀河の年れい 100億年よりも長い」の
キャプションのみ)は、本文の「移動には何百万年かかるが、銀河の年齢100億年以上と比べれば短い」という**2つの
数字の比較**を表現できておらず、「銀河を横断するのに100億年以上かかる」という逆の意味に誤読されかねなかった。
カード3には、移動にかかる時間(何百万年)と銀河の年齢(100億年以上)の**両方の数字**を、ロケットの移動距離が
バー全体のごく一部でしかないと分かる形で描き直す。

**重要(本文にない数値を追加しない)**: 元の📎マーカーには「地球の年齢」も並べる案があったが、
本文の確定稿には地球の年齢の具体的な数値は一切書かれていない(本文が挙げる時間の数値は「宇宙の年齢:約138億年」
と「銀河の年齢:100億年以上」の2つのみ)。地球の年齢の年数を本文に無いのに描き加えることは誤情報の追加になる
ため、**3つ目の要素は「地球の年齢」ではなく、本文L62に明記されている「銀河の年齢:100億年以上」を使う。**
ラベルに使ってよい数値は次の3つの本文記載の値だけ:
1. 宇宙の年齢: 約138億年
2. 天の川銀河の恒星の数: 1000億〜4000億個
3. 銀河の年齢: 100億年以上

```
A single wide illustration, flat warm children's book style, laid out as 3 equal-sized side-by-side
picture cards (like 3 panels of a simple picture-book spread), left to right, connected by nothing
more than even spacing (no arrows between them, no axis line, no ranking implied — the 3 cards are
simply presented together as 3 separate facts).

CRITICAL: each card's number label must attach ONLY to its own icon, with no ambiguity about which
number belongs to which picture. Use a clear caption directly below each card's icon (not floating
between cards).

Card 1 (leftmost): a simple bursting/glowing bright starburst shape (representing the birth of the
universe, like a soft simple "big bang" burst of light, NOT scary or explosion-like, just a warm
glowing burst) with a few small stars radiating outward from it. Caption directly below, in Japanese:
"宇宙の年れい　やく138億年".

Card 2 (middle): a simple spiral galaxy shape (like a pinwheel/spiral with a bright center and curved
arms), filled with many tiny dot-stars along its arms, clearly showing "a huge number of small stars"
inside one spiral galaxy shape. Caption directly below, in Japanese:
"天の川銀河の星の数　1000億〜4000億こ".

Card 3 (rightmost): a long simple horizontal timeline bar spanning the full width of the card,
representing the galaxy's age. Near the very LEFT end of this long bar only, draw a tiny short
highlighted segment (a small distinctly-colored short stretch, visually a very small fraction — no
more than roughly 5% — of the bar's total length) with a small rocket/spaceship icon next to that
short segment, and a small leader line from that short segment up to a caption reading in Japanese
"はしっこまで移動:何百万年". Below the FULL long bar (spanning its entire width), add a second
caption reading in Japanese "銀河の年れい:100億年よりも長い". The visual point is that the rocket's
journey occupies only a tiny sliver at one end of the bar, while the whole bar represents a vastly
longer span — do NOT make the rocket's segment look like it spans a large or comparable portion of
the bar.
Do NOT put a specific number of years for Earth's age anywhere in this image — only use the Japanese
captions given above, exactly as written, and no other numeric labels.

[共通スタイル指定を貼り付け]
All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read
for children, in the dark brown color (#483628). Keep the 3 cards visually equal in size and framing
so no single card looks more important than the others.
```

**生成後の確認ポイント**: 3枚のカードの数値ラベルが、それぞれ対応する絵(バースト=宇宙の年齢、渦巻銀河の
星々=恒星数、カード3のタイムラインバー=銀河の年齢)と正しく対応しているか(取り違えていないか)。
**カード3で、ロケットの移動区間がバー全体のごく一部(端のわずかな区間)にしか見えず、「移動は短い・
銀河の年齢は長い」という対比が一目で伝わるか**(前回のFAILの再発防止として最重要)。本文に無い「地球の年齢」
の具体的な年数が描き加えられていないか。3枚のカードのサイズ・扱いが均等で、どれか1枚だけが目立つ構成に
なっていないか。

---

## 3. 解説イラスト2: 宇宙人が見つからない理由、3つの仮説を対等に並べる

本文該当箇所(L86〜108)の要旨: グレートフィルター(生命が文明まで育つ途中に、乗り越えられない高いハードルが
どこかにある)/ 動物園仮説(進んだ文明がいても、あえて地球に姿を見せていない)/ 生命が誕生すること自体が
宇宙全体でとても稀である可能性。**本文は「どの説が正しいかは、確認できていません」と明記**しており、
3つとも並列の「まだ証明されていない仮説」として扱っている。

**重要(優劣をつけない)**: 3つの仮説を同じ大きさ・同じ扱いで横に並べ、どれか1つだけを正解のように強調したり、
チェックマーク・王冠・スポットライトなど「これが答え」に見える演出を付けない。3枚それぞれに同じ形の
「まだ証明されていない」を示す小さな「?」マークを均等に付ける。

```
A single wide illustration, flat warm children's book style, laid out as exactly 3 equal-sized
side-by-side picture cards (same size, same frame style, same visual weight — no card is bigger,
brighter, centered-and-raised, or otherwise emphasized over the others). Add one shared small heading
above all 3 cards, in Japanese: "まだ証明されていない仮説たち". On each of the 3 cards, place an
identical small "?" badge icon in the same corner position, to show all 3 are equally unconfirmed
guesses (not a ranked list, not a "correct answer" among them).

Card 1 (leftmost) — グレートフィルター: a simple, gentle hurdle-race path shown as a row of 4-5 small
low hurdle/bar shapes in a line, all about the same short height, EXCEPT one hurdle further along the
row that is noticeably taller than the rest, with a small "?" mark drawn right above that one tall
hurdle (showing nobody knows exactly which hurdle it is or where along the path it sits). Do not
label the tall hurdle as being at the start or the end of the row — its exact position along the row
should read as ambiguous/unspecified, just "somewhere among the hurdles, one is much taller". Caption
below the card, in Japanese: "グレートフィルター:こえられない高いハードルが、どこかにあるかも".

Card 2 (middle) — 動物園仮説: a small, cute, round cartoon planet Earth shape sitting behind a soft
simple round glass dome or transparent curtain (gentle, not a cage, not bars, nothing that looks like
imprisonment), with ONE small, gentle, curious silhouette figure peeking from behind a soft cloud or
curtain at a distance outside the dome, simply watching quietly without approaching or touching.
Keep the mood calm and a little whimsical, not threatening or sad. Caption below the card, in
Japanese: "動物園仮説:見えないところで、そっと見ているだけかも".

Card 3 (rightmost) — 生命が稀である可能性: a small row of 4-5 simple bare round planet shapes with no
markings on them (plain, empty-looking), and ONE different planet among them (positioned anywhere in
the row, not necessarily first or last) that has a single tiny green sprout/plant icon on it,
representing that life appearing at all is rare. Caption below the card, in Japanese:
"生命が生まれること自体、宇宙ではとてもまれかも".

[共通スタイル指定を貼り付け]
All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read
for children, in the dark brown color (#483628). Double-check that the 3 cards are equal in size,
color intensity, and framing — no gold stars, no checkmarks, no crown, no spotlight, and no card
placed higher/larger than the others, since the article treats all 3 as equally unproven ideas.
```

**生成後の確認ポイント**: 3枚のカードが同じ大きさ・同じ扱いで並び、どれか1つだけが「正解」のように強調
(チェックマーク・中央配置での拡大・スポットライト等)されていないか。「?」マークが3枚とも均等に付いて
いるか。グレートフィルターの図で、高いハードルの位置が「過去」「未来」など本文に無い具体的な位置づけを
勝手に示していないか(本文は「どこにあるかは分かっていない」としている)。動物園仮説の図が、地球を檻に
入れたような威圧的・不安を煽る表現になっていないか(トーン方針: 不必要に怖がらせる表現は避ける)。

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
  ```bash
  python3 -c "from PIL import Image;print(Image.open('covers/fermi-paradox.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/fermi-paradox-scale.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/fermi-paradox-hypotheses.png').size)"
  ```
- [ ] 日本語テキスト(タイトル・ラベルとも)が崩れていないか拡大して確認
- [ ] カバーのタイトルが3行(47字)に収まり、窮屈になっていないか確認
- [ ] カバー: 物理学者キャラクターが実在の人物の写実的な肖像になっていないか(一般的なキャラクター表現に
      とどまっているか)確認
- [ ] カバー: 空のノートが「論文もメモも残していない」という見どころとして視覚的に読み取れるか確認
- [ ] イラスト1: 3枚のラベル「宇宙の年れい 約138億年」「天の川銀河の星の数 1000億〜4000億こ」
      「銀河の年れい 100億年よりも長い」が、それぞれ対応する絵と取り違えられていないか確認
- [ ] イラスト1: 本文に無い「地球の年齢」の具体的な年数が描き加えられていないか確認
- [ ] イラスト2: 3つの仮説(グレートフィルター/動物園仮説/生命が稀である可能性)が同じ大きさ・同じ扱いで
      並び、どれか1つだけが正解のように強調されていないか確認(チェックマーク・王冠・スポットライト等が
      無いか)
- [ ] イラスト2: グレートフィルターの図で、ハードルの位置が「過去」「未来」等の本文に無い位置づけを
      勝手に示していないか確認
- [ ] イラスト2: 動物園仮説の図が威圧的・不安を煽る表現(檻・鉄格子等)になっていないか確認
- [ ] プロフィールアイコンは既存の `profile/icon.png` をそのまま使い、作り直していないか確認

保存先の目安: `covers/fermi-paradox.png` /
`illustrations/fermi-paradox-scale.png`(宇宙の年齢・恒星数・銀河の年齢のスケール比較)/
`illustrations/fermi-paradox-hypotheses.png`(3つの仮説を対等に並べた図)

生成後、本文中の📎マーカーを画像貼り付け手順に反映してください(マーカー自体は `note-formatter` が
実画像への差し替えを行う担当のため、ここでは生成物のファイルパスが本文の📎マーカーの指定と
一致していることのみ確認する):
- `illustrations/fermi-paradox-scale.png` … 本文L46のマーカーと一致
- `illustrations/fermi-paradox-hypotheses.png` … 本文L88のマーカーと一致

## 注記(このドキュメントの位置づけ)

このドキュメントは ChatGPT(画像生成)に貼り付けるプロンプトの作成のみを行ったものであり、
実際の画像ファイル(`covers/fermi-paradox.png` 等)はまだ生成・保存されていない。
プロンプトをChatGPTに貼り付けて画像を生成したのち、上記チェックリストに沿って検証し、
サイズ調整(PIL等での1280×670・横1200pxへのリサイズ)を行うこと。
