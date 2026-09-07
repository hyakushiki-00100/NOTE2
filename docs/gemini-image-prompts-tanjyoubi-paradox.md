# Gemini用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「誕生日のパラドックス」用イラスト一式
**確定タイトル**: 「クラスに23人集まれば、同じ誕生日の人が50%の確率でいる? 「誕生日のパラドックス」は、暗号の世界でも使われている」(58字・コードで確認済み)
**用途**: Gemini(画像生成)にそのまま貼り付けて使うプロンプト
**方針**: 過去記事(バーナム効果・氷はなぜ水に浮くのか 等)と同様、**文字入り版のみ**を用意する。

---

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | ✅ 既存の `profile/icon.png`(500×500・正方形、確認済み)をそのまま流用。作り直さない |
| 記事カバー | 🔲 プロンプト作成済み・Gemini での生成待ち(`covers/tanjyoubi-paradox.png` として保存予定) |
| 解説イラスト1(4人が握手、線が6本になる図) | 🔲 プロンプト作成済み・生成待ち(`illustrations/tanjyoubi-paradox-handshake.png`) |
| 解説イラスト2(人数と一致確率のグラフ、23人で50%超え) | 🔲 プロンプト作成済み・生成待ち(`illustrations/tanjyoubi-paradox-graph.png`) |

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

## タイトル文字数の確認(コードで検証)

```bash
python3 -c "
t = 'クラスに23人集まれば、同じ誕生日の人が50%の確率でいる? 「誕生日のパラドックス」は、暗号の世界でも使われている'
print(len(t))
"
# => 58
```

58字は、過去記事のバーナム効果回(50字・4〜5行)より長い。**行数に余裕を持たせ、5〜6行を基本とする。**
1〜3行に無理に詰め込むと文字が小さくなりすぎるか、はみ出す恐れがあるため避ける。

---

## 1. 記事カバー

本文の核となるフック(クラスにわずか23人いれば、同じ誕生日の人がいる確率は50%を超える。この
「ペアの数で考える」発想は、暗号の世界の「誕生日攻撃」にもつながっている)を絵にする。タイトルは
確定済みなので、そのまま画像内に焼き込む。

**注意(事実の取り扱い)**: カバーには本文にある大枠の数値(23人・50%)のイメージだけを持たせ、
253組・10人12%・30人71%等の細かい数値はカバーには書き込まない(それらは解説イラスト2で扱う)。
暗号の「誕生日攻撃」を示唆する意匠は、具体的な暗号技術の名称・製品名を書き込まない一般的な
記号(鍵・南京錠・0と1の並びなど)にとどめる。

```
A wide horizontal illustration (aspect ratio approximately 16:8.4), flat warm children's book style.
In the main foreground, a simple, friendly classroom scene: a small cluster of about 5 to 8 simple
student character silhouettes (varied simple hairstyles/heights, no realistic faces, just simple round
head shapes) standing together, with two of them, clearly distinguishable from the rest by a small
matching accent color or a small matching icon (e.g. both wearing the same small star sticker, or both
with the same small ribbon color), positioned near each other with a small sparkle or "!" mark between
them, to suggest "these two share the same birthday" — keep this pair subtle and charming, not
alarming, just a small delightful surprise.
Above or beside the group, include a few small simple calendar-page or birthday-cake icon motifs (no
readable specific dates, just generic small calendar/cake shapes) to reinforce the "birthday" theme.
In a small, clearly secondary corner of the image, include a small, simple, symbolic hint of digital
security — a simple small padlock icon or a short string of simple "0" and "1" digit shapes — to hint
at "this same idea is also used in cryptography," kept small and subordinate to the main classroom
scene; do not include any specific cipher/algorithm brand name or product name.
[共通スタイル指定を貼り付け]
Include a title at the top of the image in bold, clearly legible Japanese text: 「クラスに23人集まれば、同じ誕生日の人が50%の確率でいる? 「誕生日のパラドックス」は、暗号の世界でも使われている」.
CRITICAL — this title is 58 characters, noticeably LONGER than a typical short headline (longer than
past 50-character titles that already needed 4–5 lines), so it must be laid out across 5 TO 6 LINES
with a small enough font to comfortably fit without crowding or overlapping the illustration below.
Suggested balanced line breaks (5 lines):
line 1: 「クラスに23人集まれば、」
line 2: 「同じ誕生日の人が」
line 3: 「50%の確率でいる?」
line 4: 「「誕生日のパラドックス」は、」
line 5: 「暗号の世界でも使われている」
If 5 lines still feel crowded, 6 lines with similarly natural phrase breaks is also acceptable — do
not force it onto 2–4 lines, as the font would become too small to read comfortably or the text would
overflow or overlap the illustration below. Leave a clear, generous empty margin between the very top
edge of the image and the top of line 1's characters (at least 6% of the image height) — no part of
any character may touch or be cropped by the top edge. The title text must be crisp, correctly formed
Japanese characters and numerals/symbols (not garbled — pay special attention to "23", "50%", "?", and
the nested quotation marks around 誕生日のパラドックス), in the dark brown color (#483628), positioned
in the upper area with calm, uncluttered space behind it so it does not overlap the classroom
illustration below.
```

**生成後の確認ポイント**: タイトルが5〜6行に収まり、文字が窮屈になっていないか(1〜4行に詰め込まれて文字が小さすぎたり、はみ出したりしていないか)。「23」「50%」「?」やネストした鉤括弧が正しく描画されているか拡大して確認。誕生日が一致する2人の表現が、不安をあおるものではなく、ちょっとした驚き・発見として描かれているか確認。暗号を示唆する意匠(鍵・0と1など)が小さく背景的な扱いになっており、具体的な製品名・アルゴリズム名を書き込んでいないか確認。

---

## 2. 解説イラスト1: 4人が握手して、線が6本になる図

本文該当箇所(「4人の教室で、ペアの数を数えてみる」節)の要旨: 教室に4人(Aさん・Bさん・Cさん・
Dさん)いるとき、この4人から2人を選ぶ組み合わせは、A-B、A-C、A-D、B-C、B-D、C-Dの**6通り**。
4人が全員と1回ずつ握手をすると、握手は**6回**になる。

**組み合わせ数の確認(イラスト担当が自分でも検証)**:
4人から2人を選ぶ組み合わせの数 = C(4,2) = 4×3÷2 = **6**。本文の記述(6通り・6回)と一致する。

```bash
python3 -c "
from itertools import combinations
people = ['A','B','C','D']
pairs = list(combinations(people, 2))
print(len(pairs), pairs)
"
# => 6 [('A', 'B'), ('A', 'C'), ('A', 'D'), ('B', 'C'), ('B', 'D'), ('C', 'D')]
```

**重要(本文にない事実を追加しない)**:
- 画像内に含めてよい数字は **4(人)と6(通り/本)のみ**。253・23等、この節より後に出てくる数値は
  このイラストには入れない。
- **線の本数が実際に数えられる構図にする。** 4人を正方形(または菱形)の4つの角に配置し、隣り合う
  4本の辺(外周)+対角線2本 = 合計6本の直線で、4人の**全ての組み合わせ**を過不足なく結ぶ。
  線が重なって見分けにくくならないよう、対角線2本は交差点で色や太さを変えず、シンプルな直線のまま
  はっきり描く。
- 4人にはA・B・C・Dの簡単なラベルを付け、本文の呼び方(Aさん・Bさん・Cさん・Dさん)と対応させる。

```
A single illustration, flat warm children's book style: exactly 4 simple, friendly student character
silhouettes (no realistic faces, simple round head shapes, varied simple hairstyles so they are visually
distinct), each standing at one corner of an imaginary square, positioned at the TOP-LEFT, TOP-RIGHT,
BOTTOM-LEFT, and BOTTOM-RIGHT of the composition. Label each character with a single bold Japanese
letter tag near their head: "Aさん" (top-left), "Bさん" (top-right), "Cさん" (bottom-left), "Dさん"
(bottom-right).

Draw a straight, simple, warm-brown connecting line between EVERY pair of the 4 characters, so that
ALL 6 possible pairs are connected — this means: the 4 outer sides of the square (A–B top side, A–C
left side, B–D right side, C–D bottom side) PLUS the 2 diagonals crossing through the middle (A–D and
B–C) — for a total of exactly 6 straight lines, no more, no fewer. Each line should look like a simple
handshake/connection line (you may add a small pair of simple cartoon hands "shaking" at the midpoint
of each line, or a small sparkle at each line's midpoint, to reinforce "these two are shaking hands/
being compared"). The two diagonal lines crossing in the middle should remain clearly visible as two
distinct straight lines (not merged into one thick line), so a viewer can trace and count all 6 lines
individually.

Near the bottom of the image, include a short Japanese caption confirming the count: "4人で 6本(6とおり)".
Do not add any other numbers (e.g. no "23", no "253") anywhere in this image — only "4" (number of
people) and "6" (number of lines/combinations) are allowed to appear.
[共通スタイル指定を貼り付け]
All Japanese text and numerals must be crisp, correctly formed characters and digits (not garbled),
large and easy to read for children, in the dark brown color (#483628).
```

**生成後の確認ポイント**: 実際に線を1本ずつ数えて、**ちょうど6本**になっているか確認する(4辺+対角線2本=6本。対角線が交差部分で1本の太い線に見えてしまい2本と数えにくくなっていないか特に注意)。4人がA・B・C・Dのラベルと矛盾なく対応しているか。画像内の数字が「4」「6」以外に増えていないか(「23」「253」等、後の節の数値が紛れ込んでいたら失敗)。

---

## 3. 解説イラスト2: 人数と一致確率のグラフ(23人で50%を超える)

本文該当箇所(「数字で見る一致の確率」節)の要旨: 人数と一致確率の関係は次の通り。

- 10人:約12%
- 23人:約51%
- 30人:約71%
- 41人:約90%
- 70人:約99.9%

23人という数字は、ふつうの1クラスの人数よりも少ないくらいなのに、半分を超える確率になる。

**重要(本文にない事実を追加しない)**:
- グラフの点として使ってよい数値は、本文にあるこの**5組の(人数, 確率)のみ**
  (10人-約12%、23人-約51%、30人-約71%、41人-約90%、70人-約99.9%)。それ以外の人数・確率の
  目盛りや数値を新たに書き加えない(例えば5人・15人・50人・100%ちょうど、といった数値を追加しない)。
- 縦軸の50%のラインは、本文で強調されている基準線として明示してよい(23人の点がこの線を超えて
  いることを視覚的に示すため)。ただしこれは「50%」というラベル1つを追加するのみで、他の目盛り
  (25%・75%等)を追加しない。
- 横軸(人数)・縦軸(確率)の目盛りラベルは、上記5つの人数・50%の基準線・軸そのものの名称
  (「人数」「一致する確率」)以外の文字・数値を追加しない。
- 小学生が見て分かるよう、無機質な折れ線グラフだけで終わらせず、各データ点のそばに小さく
  「人」のシルエットのアイコン(人数が増えるほど人のアイコンの集まりが大きくなる、程度の
  絵的な補助表現)を添えてよい。ただし人のアイコンの数を本文にない具体的な人数として数えられる
  ように描かない(装飾として、多い/少ないの印象を補う程度にとどめる)。

```
A single illustration, flat warm children's book style: a simple, friendly line-graph chart on a cream
background. Draw a horizontal axis (x-axis) labeled in Japanese "人数(にんずう)" and a vertical axis
(y-axis) labeled in Japanese "一致する確率(%)". The vertical axis should visually represent 0% at the
bottom and 100% near the top, but do NOT add numeric tick marks for every 10% — only add ONE horizontal
dashed reference line clearly labeled "50%" partway up the chart, in the deep teal color (#3A6960), to
mark the halfway point.

Plot exactly 5 data points along a single smooth, rising curve, from left (fewer people) to right (more
people), each point clearly marked with a small dot and a nearby label showing BOTH the number of people
and the percentage, in Japanese, exactly as follows (do not alter these numbers, do not add any other
data points):
- point 1 (leftmost, lowest): "10人" / "約12%"
- point 2: "23人" / "約51%"
- point 3: "30人" / "約71%"
- point 4: "41人" / "約90%"
- point 5 (rightmost, highest): "70人" / "約99.9%"

The curve must rise steeply between point 1 and point 2, and this is the KEY visual moment: the point
labeled "23人" / "約51%" must sit clearly ABOVE the dashed "50%" reference line (make this crossing
visually obvious, e.g. highlight the "23人" point with a small star, a different accent color
(terracotta orange #E08454), or a small "!" mark, distinguishing it from the other 4 points which can
be in the deep teal color #3A6960). The curve should then continue rising more gradually through points
3, 4, and 5, flattening out as it approaches the top near point 5, to show the probability approaching
(but the image should not claim it reaches) 100%.

Optionally, add a small decorative row of simple person-silhouette icons below the x-axis, growing from
a small cluster near point 1 to a larger cluster near point 5, as a friendly visual hint that "more
people" is the theme of the horizontal axis — keep this purely decorative and do not make the icons
individually countable as an exact headcount.

At the top of the image, include a short Japanese caption: "人数が増えると、一致する確率もぐんと上がる".
Do not add any numbers, tick marks, or labels other than the 5 (人数/確率) pairs listed above and the
single "50%" reference line — no other percentages, no other headcounts, no grid lines with unlabeled
numbers.
[共通スタイル指定を貼り付け]
All Japanese text and numerals (including "12%", "51%", "71%", "90%", "99.9%", "10人", "23人", "30人",
"41人", "70人", "50%") must be crisp, correctly formed characters and digits (not garbled or swapped —
pay special attention to not confusing "23人/約51%" with any other point), large and easy to read for
children, in the dark brown color (#483628) for axis labels and captions.
```

**生成後の確認ポイント**: 5つのデータ点の(人数, 確率)の組み合わせが、本文の数値(10人-約12%、23人-約51%、30人-約71%、41人-約90%、70人-約99.9%)と一つずつ完全に一致しているか、ラベルを1つずつ拡大して確認する(人数と確率の組み合わせが入れ替わっていないか特に注意)。**「23人」の点が「50%」の基準線を明確に超えて上に位置しているか**(超えていない・線上ギリギリで曖昧に見える場合は失敗、作り直す)。軸ラベル・目盛りが「人数」「一致する確率(%)」「50%」の基準線・5つのデータ点以外の数値を含んでいないか確認(0%・25%・75%・100%ちょうど等の目盛りが勝手に追加されていないか)。曲線の形が「10人→23人」の間で急に立ち上がり、23人以降はゆるやかに上昇していく形になっているか確認。

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
  ```bash
  python3 -c "from PIL import Image;print(Image.open('covers/tanjyoubi-paradox.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/tanjyoubi-paradox-handshake.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/tanjyoubi-paradox-graph.png').size)"
  ```
- [ ] 日本語テキスト(タイトル・ラベル・キャプションとも)が崩れていないか拡大して確認
- [ ] カバーのタイトルが5〜6行に収まり、窮屈になっていないか確認(58字と長めのタイトルのため特に注意。2〜4行に詰め込まれていないか)
- [ ] カバー: 「23」「50%」「?」やネストした鉤括弧が正しく描画されているか。誕生日が一致する2人の表現が不安をあおる描写になっていないか確認
- [ ] カバー: 暗号を示唆する意匠(鍵・0と1など)が小さく背景的な扱いで、具体的な製品名・アルゴリズム名を書き込んでいないか確認
- [ ] イラスト1: 線を実際に1本ずつ数えて、ちょうど6本になっているか確認(4辺+対角線2本。対角線が交差部分で1本の太い線に見えて数えにくくなっていないか特に注意)
- [ ] イラスト1: 画像内の数字が「4」「6」以外に増えていないか確認(「23」「253」等、後の節の数値が紛れ込んでいないか)
- [ ] イラスト2: 5つのデータ点(人数, 確率)が本文の数値と一つずつ完全に一致しているか確認(10人-約12%、23人-約51%、30人-約71%、41人-約90%、70人-約99.9%)
- [ ] イラスト2: 「23人」の点が「50%」の基準線を明確に超えて描かれているか確認(超えていなければ失敗)
- [ ] イラスト2: 軸ラベル・目盛りに本文にない数値(0%・25%・75%・100%ちょうど等)が勝手に追加されていないか確認
- [ ] プロフィールアイコンは既存の `profile/icon.png` をそのまま使い、作り直していないか確認

保存先の目安: `covers/tanjyoubi-paradox.png` /
`illustrations/tanjyoubi-paradox-handshake.png`(4人が握手、線が6本になる図)/
`illustrations/tanjyoubi-paradox-graph.png`(人数と一致確率のグラフ、23人で50%超え)

生成後、本文中の📎マーカーに対応するファイルパスが一致していることを確認してください(マーカー自体を
実画像への記法に差し替えるのは `note-formatter` の担当です):
- `illustrations/tanjyoubi-paradox-handshake.png` … 本文「4人の教室で、ペアの数を数えてみる」節末の📎マーカーと一致
- `illustrations/tanjyoubi-paradox-graph.png` … 本文「数字で見る一致の確率」節末の📎マーカーと一致
