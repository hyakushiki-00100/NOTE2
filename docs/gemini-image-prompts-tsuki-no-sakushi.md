# Gemini用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「月の錯視」用イラスト一式
**確定タイトル**: 「地平線の月はなぜ大きい? 「月の錯視」は写真に撮るとほとんど同じ大きさ、実は原因がまだ解明されていない」(51字・コードで確認済み)
**用途**: Gemini(画像生成)にそのまま貼り付けて使うプロンプト
**方針**: 過去記事(氷はなぜ水に浮くのか・誕生日のパラドックス 等)と同様、**文字入り版のみ**を用意する。

---

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | ✅ 既存の `profile/icon.png`(500×500・正方形、確認済み)をそのまま流用。作り直さない |
| 記事カバー | 🔲 プロンプト作成済み・Gemini での生成待ち(`covers/tsuki-no-sakushi.png` として保存予定) |
| 解説イラスト1(比較対象説: 地平線の月と目印/夜空高くの月の対比) | 🔲 プロンプト作成済み・生成待ち(`illustrations/tsuki-hikaku-taisho.png`) |
| 解説イラスト2(見かけの距離説: ポンゾ錯視の図) | 🔲 プロンプト作成済み・生成待ち(`illustrations/ponzo-sakushi.png`) |
| 解説イラスト3(太陽でも同じ現象が起きる対比) | 🔲 プロンプト作成済み・生成待ち(`illustrations/taiyou-sakushi.png`) |

すべて未生成。生成後、下記「生成後のチェックリスト」に沿って検証し、Opus QA(`note-qa`)にかけること。

---

## 共通スタイル指定(毎回のプロンプト冒頭に付けると絵柄が揃います)

```
Flat, warm, friendly children's educational illustration style (like a Japanese picture book for
elementary schoolers). Simple flat shapes, soft rounded corners, no photorealism, no realistic
human faces. Clean vector-like line art with a warm brown outline (#483628). Color palette limited
to: cream background (#FBF3E4), terracotta orange (#E08454, shadow #BF673C), deep teal
(#3A6960, light teal #92B5AB). Cheerful and gentle mood, appropriate for children. The palette has
no blue — represent "night sky" using the deep teal (#3A6960) tones, not blue.
```

---

## タイトル文字数の確認(コードで検証)

```bash
python3 -c "
t = '地平線の月はなぜ大きい? 「月の錯視」は写真に撮るとほとんど同じ大きさ、実は原因がまだ解明されていない'
print(len(t))
"
# => 51
```

51字は、過去記事の「氷はなぜ水に浮くのか」回(35字・3行)より明確に長く、「誕生日のパラドックス」回
(58字・5〜6行)に近い長さ。**行数に余裕を持たせ、5行を基本とする(窮屈なら6行まで許容)。**
1〜3行に無理に詰め込むと文字が小さくなりすぎるか、はみ出す恐れがあるため避ける。

---

## 1. 記事カバー

本文冒頭の核となるフック(地平線近くの満月はびっくりするほど大きく見えるのに、空高くに昇ると小さく
見える。でもカメラで撮って比べると、大きさはほとんど同じ。しかもその理由は、実はまだはっきり解明
されていない)を絵にする。タイトルは確定済みなので、そのまま画像内に焼き込む。

**注意(事実の取り扱い・トーンの整合)**:
- カバーは「地平線近くの月は大きく見える/空高くの月は小さく見える」という**現象そのもの**を描く
  ことに徹し、原因の説明(比較対象説・ポンゾ錯視・見かけの距離説)には踏み込まない(それらは解説
  イラスト1〜3で扱う)。カバーで特定の説を「正解」であるかのように示す矢印・図解を入れない。
- 「実は原因がまだ解明されていない」という記事の核心が伝わるよう、驚き・不思議さ・謎めいた雰囲気
  (「?」マークや、考え込む小さなキャラクターのシルエットなど)を添える。断定的な説明図にしない。
- 月そのものは、リアルな天体写真調にせず、子ども向けの可愛らしい丸い月のアイコンにする(誇張しすぎた
  大きさの差にはしない。地平線側は大きめ、空高く側は小さめ、程度の穏やかな対比にとどめる)。

```
A wide horizontal illustration (aspect ratio approximately 16:8.4), flat warm children's book style.
The lower half of the composition shows a warm evening horizon: a simple, gentle silhouette of low
hills, a few simple trees, and one or two small simple house/building shapes along the horizon line,
in dark brown (#483628) or deep teal (#3A6960) flat silhouette. Just above this horizon silhouette,
place ONE large, warm terracotta-orange (#E08454) circular moon shape (simple flat icon, soft rounded
edge, no realistic craters, maybe a few simple soft crater dots) — this moon should look impressively
big and inviting, sitting low and close to the horizon silhouette.

The upper half of the composition is a calm deep-teal (#3A6960) night sky with a few small simple
cream-colored star dots scattered around. High up in this night sky (near the moon's typical
"high in the sky" position, away from the horizon), place a SECOND moon shape — the SAME actual size
and same simple flat style as the horizon moon (identical circle size, to visually hint that the two
moons are truly the same size), but in a paler cream/light-teal tone (#92B5AB) to suggest it looks
smaller and less vivid against the open sky. Do not draw the two moons touching or overlapping; keep
them as two clearly separate moons in two different parts of the sky.

Add one small, simple, curious character silhouette (a small round head shape, no realistic face,
just a simple round shape with a small "?" mark floating near it) positioned small and secondary
somewhere in the lower part of the scene, looking up at the horizon moon with a curious, wondering
pose — to evoke "why does it look so different?" without answering the question. Keep this character
small and clearly secondary to the two moons, which are the main visual focus.

[共通スタイル指定を貼り付け]

Include a title at the top of the image in bold, clearly legible Japanese text:
「地平線の月はなぜ大きい? 「月の錯視」は写真に撮るとほとんど同じ大きさ、実は原因がまだ解明されていない」.
CRITICAL — this title is 51 characters, noticeably longer than a short headline, so it must be laid
out across 5 LINES with a font size small enough to comfortably fit without crowding or overlapping
the illustration below. Suggested natural phrase breaks (5 lines):
line 1: 「地平線の月はなぜ大きい?」
line 2: 「「月の錯視」は写真に撮ると」
line 3: 「ほとんど同じ大きさ、」
line 4: 「実は原因が」
line 5: 「まだ解明されていない」
If 5 lines still feel crowded given the font size, 6 lines with similarly natural phrase breaks is
also acceptable — do not force it onto 2–4 lines, as the font would become too large or the text
would overflow or overlap the illustration below. CRITICAL: leave a clear, generous empty margin
between the very top edge of the image and the top of line 1's characters (at least 6% of the image
height) — no part of any character may touch or be cropped by the top edge. The title text must be
crisp, correctly formed Japanese characters (not garbled — pay special attention to the nested
「」quotation marks around 月の錯視 and to the "?" and "、" punctuation), in the dark brown color
(#483628), positioned in the upper area (over the night sky) with calm, uncluttered space behind it
so it does not overlap the horizon-and-moons illustration below.
```

**生成後の確認ポイント**: タイトルが5〜6行に収まり、文字が窮屈になっていないか(2〜4行に詰め込まれて文字が小さすぎたり、はみ出したりしていないか)。ネストした鉤括弧「「月の錯視」」や「?」「、」が正しく描画されているか拡大して確認。地平線近くの大きい月と空高くの小さく見える月が、実際には**同じ大きさの円**で描かれているか(片方が明らかに大きい円で描かれていたら、記事の核心=見かけの大きさはほぼ同じ、と矛盾するため失敗)。特定の説(比較対象・ポンゾ・見かけの距離)を示す図解要素が紛れ込んでいないか確認(カバーは現象の提示のみに留める)。月の絵柄がリアルな天体写真調になっていないか(可愛いフラットアイコンになっているか)確認。

---

## 2. 解説イラスト1: 比較対象説(地平線の月と目印/夜空高くの月の対比)

本文該当箇所(「『なぜそう見えるのか』は、実はまだよく分かっていない」節、比較対象説の段落)の要旨:
地平線近くには木や建物、山など、大きさを比べられる目印がたくさんある。何もない夜空にぽつんと浮かぶ
月より、身近なものと並んだ月のほうが、大きく感じられるという説(比較対象説)。

**重要(本文にない事実を追加しない)**:
- これは「〜という説」であり、確定した正解ではない。ラベルは「比較対象説」という名称のみを付け、
  「これが正解」「証明された」といった断定的な文言・矢印での因果強調は入れない。
- **2つの月は、実際には同じ大きさの円として描く**(本文冒頭の「視角はほぼ同じ」という事実と矛盾
  させないため)。「大きく感じられる/小さく感じられる」という**印象の違い**は、周囲に目印があるか
  ないかという**構図の違いだけ**で表現し、月そのもののサイズは変えない。
- 目印として描いてよいのは本文にある「木・建物・山」程度の一般的なモチーフのみ。特定の建物名・
  地名等は書き込まない。

```
A single illustration, flat warm children's book style, split into two clearly separated side-by-side
panels of EQUAL size, with a simple vertical divider line down the middle. Leave a generous margin
(at least 8% of the image height/width) around all four edges of the entire image so nothing touches
the border.

LEFT panel, labeled at the top in bold Japanese "地平線近くの月": a warm evening/night scene with a
simple horizon line featuring a few simple silhouettes of trees, a small house or two, and a low hill,
all in dark brown or deep teal flat silhouette. Just above this horizon, place a terracotta-orange
(#E08454) circular moon of a certain size — call this moon size "M". The moon should sit close to and
just above the trees/houses/hill, so the comparison objects are clearly visible right next to the moon.

RIGHT panel, labeled at the top in bold Japanese "空高くの月": a calm deep-teal (#3A6960) night sky
with a few small cream-colored star dots, but NO ground, NO trees, NO buildings, NO hills — just open
sky. Place a circular moon of the EXACT SAME SIZE "M" as the left panel's moon (identical diameter —
this is critical, since the whole point is that the two moons are actually the same size), positioned
high up with plenty of empty sky around it and no nearby objects to compare it to.

Below both panels, add a short Japanese caption spanning the width of the image: "月の大きさは、実はどちらも同じ".
Below that, add a second short caption: "まわりに目印があると、大きく感じられる、という説(比較対象説)".
Both captions must be well within the image bounds (not touching the bottom edge), with generous
margin below them.

[共通スタイル指定を貼り付け]

All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read
for children, in the dark brown color (#483628). Do not add any numbers, percentages, or measurement
marks to this image — it is a purely visual, illustrative comparison.
```

**生成後の確認ポイント**: 左右の月が**ピクセル上で本当に同じ大きさ**に描かれているか(定規や画像編集ソフトで測るか、目視で明確に確認する。片方が大きく描かれていたら失敗、作り直す)。左パネル(地平線近く)には木・建物・山などの目印があり、右パネル(空高く)には何も無い開けた夜空になっているか。ラベルが「比較対象説」という名称のみで、「証明された」「これが正解」等の断定表現になっていないか確認。地名・実在の建物名などが書き込まれていないか確認。

---

## 3. 解説イラスト2: 見かけの距離説(ポンゾ錯視の図)

本文該当箇所(同じく「『なぜそう見えるのか』は、実はまだよく分かっていない」節、見かけの距離説・
ポンゾ錯視の段落)の要旨: 奥行きを感じさせる(遠近感のある)線の間に、同じ大きさの図形を置くと、
奥にあるほうの図形が大きく見えてしまう。これが「ポンゾ錯視」と呼ばれる有名な錯視で、見かけの距離説は
これと似たしくみで月の錯視が起きていると考える。

**重要(本文にない事実を追加しない)**:
- これも「〜という説」の一部を説明する図。ポンゾ錯視という現象そのものは事実(有名な錯視)として
  描いてよいが、「これが月の錯視の正体である」と断定する表現(例: 「これが原因です」という文言や、
  月そのものを描き込んで直接結びつける)は避ける。ポンゾ錯視という現象を単体で正しく見せることに
  徹する(月の絵は入れない。本文でも「似たしくみ」という言い方に留めている)。
- 標準的なポンゾ錯視の構図にする: 奥行きを感じさせる、上に向かって狭まっていく(または下に向かって
  広がっていく)2本の収束する線(線路や道のように奥へ伸びる線)の間に、**同じ長さの横棒(または
  同じ大きさの図形)を、奥側(線が狭い側)に1本、手前側(線が広い側)に1本、それぞれ配置する**。
  2本の横棒は実際には**まったく同じ長さ**で描く(これが錯視の肝であり、Geminiが自動でうまく描けない
  場合はダッシュ線の目盛りなどで「同じ長さ」であることを補足してもよい)。

```
A single illustration, flat warm children's book style, on a cream background. Draw two straight,
thin, dark-brown (#483628) lines that converge like a railway track or road receding into the
distance: both lines start wide apart near the BOTTOM of the image and angle inward as they go
upward, meeting close together (nearly touching, but not fully closed) near the TOP of the image —
a simple, clear linear-perspective "receding into the distance" shape, like a stylized letter "A"
without the crossbar.

Place TWO horizontal bars across the gap between the two converging lines, both bars the SAME exact
pixel length as each other (this equal length is essential to the illusion):
- One bar placed HIGH UP, near the top where the two converging lines are close together (the
  "far away" position) — draw this bar in terracotta orange (#E08454).
- One bar placed LOWER DOWN, near the bottom where the two converging lines are far apart (the
  "close up" position) — draw this bar in deep teal (#3A6960).
Both bars must span fully from one converging line to the other at their respective heights, and
both bars must be drawn with IDENTICAL length in pixels. To help confirm the equal length visually,
add a small thin dashed vertical tick mark at each end of both bars, and optionally a faint dashed
extension line showing that if you slid the top bar down to the bottom bar's position, the two would
exactly match in length.

Add a bold Japanese title at the top of the image, in the open space above the converging lines'
meeting point: "ポンゾ錯視". Below the whole illustration, add a short Japanese caption: "この2本の棒、じつは同じ長さです" and beneath that a second smaller caption: "奥にあるほうが、大きく見えてしまいます".
Do NOT include any moon, sun, or celestial imagery in this illustration — it illustrates the general
optical-illusion phenomenon on its own, not the moon directly.

[共通スタイル指定を貼り付け]

All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read
for children, in the dark brown color (#483628). Leave a generous margin (at least 8% of the image
height/width) around all four edges so nothing (lines, bars, text) touches the border.
```

**生成後の確認ポイント**: 2本の収束する線が、上に向かって狭まる(遠近感のある)構図になっているか。2本の横棒(奥側・手前側)が**実際に同じ長さ**で描かれているか(目視・画像編集ソフトでの計測どちらでも確認し、明らかに長さが違っていたら失敗、作り直す)。奥側の棒が線の間の狭い部分に、手前側の棒が広い部分に、それぞれ過不足なく収まっているか(線からはみ出したり、届いていなかったりしないか)。月や太陽の絵が紛れ込んでいないか確認(この図は現象単体の説明であり、月に直接結びつける描写はしない)。「これが正解」「証明された」等の断定表現が入っていないか確認。

---

## 4. 解説イラスト3: 太陽でも同じことが起きている(夕日と真昼の太陽の対比)

本文該当箇所(「太陽でも、同じことが起きている」節)の要旨: 夕方、地平線近くに沈む太陽が、真昼の
太陽より大きく見えることがある。これも月の錯視と同じ現象だと考えられている。

**重要(本文にない事実を追加しない)**:
- 月のイラスト1と同様、**2つの太陽は実際には同じ大きさの円として描く**(見かけの錯視であって、
  太陽が物理的に大きさを変えているわけではないという本文の趣旨と矛盾させないため)。
- 太陽をリアルな天体写真調にしない。子ども向けの可愛らしい、シンプルな丸い太陽アイコン(柔らかい
  光の線を数本添える程度)にとどめ、誇張しすぎた大きさの差にしない。
- 「原因についての説」をこの図に持ち込まない(比較対象説・見かけの距離説の図解要素を太陽側に
  繰り返し描き込まない)。あくまで「月と同じ現象が太陽でも起きる」という対比のみを描く。

```
A single illustration, flat warm children's book style, split into two clearly separated side-by-side
panels of EQUAL size, with a simple vertical divider line down the middle. Leave a generous margin
(at least 8% of the image height/width) around all four edges of the entire image so nothing touches
the border.

LEFT panel, labeled at the top in bold Japanese "地平線に沈む夕日": a simple evening horizon scene
with a flat horizon line (a simple sea or field silhouette line is fine, no detailed landscape), in
warm terracotta-orange (#E08454) and cream (#FBF3E4) tones suggesting sunset colors. Just above the
horizon line, place ONE simple, cute, flat circular sun shape (soft rounded edge, a few simple short
flat triangle or line "rays" around it, no realistic solar texture, no face) — call this sun size "S".
The sun should sit low, close to and just above the horizon line.

RIGHT panel, labeled at the top in bold Japanese "真昼の空の太陽": a simple daytime sky using the
light teal (#92B5AB) tone as the sky color, with a small simple cloud shape or two for context, but
NO horizon objects nearby. Place a circular sun shape of the EXACT SAME SIZE "S" as the left panel's
sun (identical diameter, same simple style and same few short rays), positioned high up in the middle
of the sky with open space around it.

Below both panels, add a short Japanese caption spanning the width of the image: "太陽の大きさも、実はどちらも同じ".
Below that, add a second short caption: "月と同じしくみで、大きく見えたり小さく見えたりします".
Both captions must be well within the image bounds (not touching the bottom edge), with generous
margin below them.

[共通スタイル指定を貼り付け]

All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read
for children, in the dark brown color (#483628). Do not add any numbers, percentages, or measurement
marks to this image.
```

**生成後の確認ポイント**: 左右の太陽が**実際に同じ大きさの円**で描かれているか(片方が明らかに大きく描かれていたら失敗、作り直す)。左パネル(夕日)は地平線のすぐ上、右パネル(真昼)は開けた空の高い位置に、それぞれ配置されているか。太陽がリアルな天体写真調になっておらず、可愛らしいフラットアイコンになっているか確認。比較対象説・ポンゾ錯視など「原因の説」の図解要素がこの図に紛れ込んでいないか確認(この図は月との対比のみを描く)。誇張しすぎた大きさの差になっていないか(常識的な範囲の対比か)確認。

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
  ```bash
  python3 -c "from PIL import Image;print(Image.open('covers/tsuki-no-sakushi.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/tsuki-hikaku-taisho.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/ponzo-sakushi.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/taiyou-sakushi.png').size)"
  ```
- [ ] 日本語テキスト(タイトル・ラベル・キャプションとも)が崩れていないか拡大して確認
- [ ] カバーのタイトルが5〜6行に収まり、窮屈になっていないか確認(51字と長めのタイトルのため特に注意。2〜4行に詰め込まれていないか)
- [ ] カバーのネストした鉤括弧「「月の錯視」」・「?」・「、」が正しく描画されているか確認
- [ ] カバー: 地平線近くの月と空高くの月が、実際には同じ大きさの円で描かれているか確認(明らかにサイズが違うと本文冒頭の「視角はほぼ同じ」という趣旨と矛盾するため要注意)
- [ ] カバー: 特定の説(比較対象説・ポンゾ錯視・見かけの距離説)を「正解」であるかのように示す図解要素が紛れ込んでいないか確認
- [ ] イラスト1(比較対象説): 左右の月が実際に同じ大きさの円で描かれているか確認(要計測・目視)
- [ ] イラスト1: 左パネルに木・建物・山などの目印があり、右パネルには何もない開けた夜空になっているか確認
- [ ] イラスト1: ラベルが「比較対象説」という名称のみで、断定表現(「証明された」「これが正解」等)になっていないか確認
- [ ] イラスト2(ポンゾ錯視): 2本の収束する線が正しい遠近構図になっており、2本の横棒が実際に同じ長さで描かれているか確認(要計測・目視)
- [ ] イラスト2: 奥側の棒が線の狭い部分に、手前側の棒が広い部分に、それぞれ過不足なく収まっているか確認
- [ ] イラスト2: 月・太陽の絵が紛れ込んでいないか確認(現象単体の説明図であること)
- [ ] イラスト3(太陽): 左右の太陽が実際に同じ大きさの円で描かれているか確認(要計測・目視)
- [ ] イラスト3: 太陽・月ともにリアルな天体写真調になっておらず、子ども向けの可愛らしいフラットアイコンになっているか確認
- [ ] イラスト3: 「原因の説」を示す図解要素(目印・収束する線など)が紛れ込んでいないか確認(月との対比のみを描く図であること)
- [ ] 全画像共通: 使用色がクリーム(#FBF3E4)・テラコッタオレンジ(#E08454/影#BF673C)・ディープティール(#3A6960/淡色#92B5AB)・ダークブラウン(#483628)の4色パレットに収まっているか確認(青色など範囲外の色が使われていないか)
- [ ] プロフィールアイコンは既存の `profile/icon.png` をそのまま使い、作り直していないか確認

保存先の目安: `covers/tsuki-no-sakushi.png` /
`illustrations/tsuki-hikaku-taisho.png`(比較対象説: 地平線の月と目印/夜空高くの月の対比)/
`illustrations/ponzo-sakushi.png`(見かけの距離説: ポンゾ錯視の図)/
`illustrations/taiyou-sakushi.png`(太陽でも同じ現象が起きる対比)

生成後、本文中の📎マーカーに対応するファイルパスが一致していることを確認してください(マーカー自体を
実画像への記法に差し替えるのは `note-formatter` の担当です):
- `illustrations/tsuki-hikaku-taisho.png` … 本文「『なぜそう見えるのか』は、実はまだよく分かっていない」節、比較対象説の段落末の📎マーカーと一致
- `illustrations/ponzo-sakushi.png` … 同節、見かけの距離説・ポンゾ錯視の段落末の📎マーカーと一致
- `illustrations/taiyou-sakushi.png` … 本文「太陽でも、同じことが起きている」節末の📎マーカーと一致
</content>
