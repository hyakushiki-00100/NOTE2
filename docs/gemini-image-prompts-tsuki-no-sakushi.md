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
| 記事カバー | ✅ 2回目生成で保存済み(`covers/tsuki-no-sakushi.png`、1280×670)。連続生成の不具合は簡潔化したプロンプトで解消。ただし月の直径がまだ約269px対約200px(約1.3倍差)残っていたため、空高くの月をPythonで269pxに拡大する画像編集を行い、完全に一致させてから保存した |
| 解説イラスト1(比較対象説: 地平線の月と目印/夜空高くの月の対比) | ✅ 2回目生成で合格・保存済み(`illustrations/tsuki-hikaku-taisho.png`、1200×670)。計測の結果、月の直径は左134px・右135pxでほぼ完全一致。「M」の誤字も消えた |
| 解説イラスト2(見かけの距離説: ポンゾ錯視の図) | ✅ Geminiでの生成が2回とも棒の長さを一致させられなかったため、方針転換してPythonで直接描画。保存済み(`illustrations/ponzo-sakushi.png`、1200×900、棒の長さは260px/260pxで完全一致)。初版はオーナーから「錯視に見えない」との指摘を受け、奥の棒を収束線にほぼぴったり沿わせ、手前の棒との間隔も詰めて再構成した |
| 解説イラスト3(太陽でも同じ現象が起きる対比) | 🔲 プロンプト作成済み・生成待ち(`illustrations/taiyou-sakushi.png`) |

カバー・イラスト1・イラスト2は1回目の生成物をピクセル計測で検証した結果、いずれも「同じ大きさ」という
本文の核心と矛盾する不一致が見つかったため不合格とし、プロンプトを修正した(詳細は各セクション参照)。
イラスト1は2回目の修正版プロンプトで合格したが、イラスト2(ポンゾ錯視)は2回目もGeminiが「同じ長さ」を
守れなかったため、生成AIに頼らずPythonで直接描画する方式に切り替えた(このイラストは幾何学的な正確さが
本質的に必要なため、コードで描く方が確実)。カバーは引き続きGeminiでの再生成を試すが、この方式でも
うまくいかない場合は同様にコード生成へ切り替える。生成後は目視だけでなく、下記「生成後のチェックリスト」
に沿ってコードで計測・検証し、Opus QA(`note-qa`)にかけること。

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

**注意(Geminiの暴走生成について)**: このプロンプトを投げると Gemini が何枚も連続で生成して
止まらなくなる、という報告があったため、番号付きリスト形式だった「5行への分割案」を地の文の
説明に書き換え、`CRITICAL` の強調も1箇所に減らして全体を短くした(番号付きの箇条書きが「複数の
画像を作る指示」と誤解された可能性を考えた修正)。それでも同様の挙動が起きる場合は、この
コードブロックの内容だけを1回で貼り付け、続けて別の指示を同じメッセージに含めないようにしてほしい。

**注意(事実の取り扱い・トーンの整合)**:
- カバーは「地平線近くの月は大きく見える/空高くの月は小さく見える」という**現象そのもの**を描く
  ことに徹し、原因の説明(比較対象説・ポンゾ錯視・見かけの距離説)には踏み込まない(それらは解説
  イラスト1〜3で扱う)。カバーで特定の説を「正解」であるかのように示す矢印・図解を入れない。
- 「実は原因がまだ解明されていない」という記事の核心が伝わるよう、驚き・不思議さ・謎めいた雰囲気
  (「?」マークや、考え込む小さなキャラクターのシルエットなど)を添える。断定的な説明図にしない。
- 月そのものは、リアルな天体写真調にせず、子ども向けの可愛らしい丸い月のアイコンにする(誇張しすぎた
  大きさの差にはしない。地平線側は大きめ、空高く側は小さめ、程度の穏やかな対比にとどめる)。

```
A single wide horizontal illustration, flat warm children's book style. Lower half: a warm evening
horizon with a simple gentle silhouette of low hills, a few trees, and one or two small houses, in
dark brown (#483628) or deep teal (#3A6960) flat silhouette, with one large terracotta-orange
(#E08454) circular moon (simple flat icon, soft rounded edge, a few soft crater dots, no realistic
photo texture) sitting low and close to the horizon. Upper half: a plain deep-teal (#3A6960) night
sky filling the entire upper half from edge to edge (not a small cloud or bubble shape), with a few
cream star dots, containing a second moon high up in a paler cream/light-teal tone (#92B5AB).

Both moons must be exactly the same diameter — about 14% of the image width each, like two circles
cut from the same stencil — do not draw the sky moon smaller just because it sits higher up, and do
not write any letter or number on or near either moon. Add one small, simple curious character
silhouette (a round head shape, no realistic face, a small "?" floating near it) low in the scene,
looking up at the horizon moon, small and clearly secondary to the two moons.

[共通スタイル指定を貼り付け]

Add a bold, clearly legible Japanese title across the top of the image, over the night sky, in the
dark brown color (#483628), broken naturally into five short lines: 地平線の月はなぜ大きい? / 「月の
錯視」は写真に撮ると / ほとんど同じ大きさ、/ 実は原因が / まだ解明されていない. Use a font size small
enough that all five lines sit comfortably without crowding, overlapping each other, or overlapping
the illustration below, with a calm empty margin above line 1 and behind the whole title block. The
nested 「」marks around 月の錯視 and the "?" and "、" punctuation must render as crisp, correct
Japanese characters.
```

**生成後の確認ポイント**: タイトルが5〜6行に収まり、文字が窮屈になっていないか(2〜4行に詰め込まれて文字が小さすぎたり、はみ出したりしていないか)。ネストした鉤括弧「「月の錯視」」や「?」「、」が正しく描画されているか拡大して確認。地平線近くの大きい月と空高くの小さく見える月が、実際には**同じ大きさの円**で描かれているか(**要ピクセル計測**。1回目の生成では約370px対約137pxと約2.7倍もの差があり、目視だけでは見落としていた。定規代わりにPythonで直径を測って必ず数値で確認する)。空側の月が孤立した雲・吹き出しのような区画に閉じ込められておらず、上半分全体が単色の夜空になっているか確認。月やその近くに「M」等の文字・記号が誤って書き込まれていないか確認。特定の説(比較対象・ポンゾ・見かけの距離)を示す図解要素が紛れ込んでいないか確認(カバーは現象の提示のみに留める)。月の絵柄がリアルな天体写真調になっていないか(可愛いフラットアイコンになっているか)確認。

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
(#E08454) circular moon. The moon should sit close to and just above the trees/houses/hill, so the
comparison objects are clearly visible right next to the moon.

RIGHT panel, labeled at the top in bold Japanese "空高くの月": a calm deep-teal (#3A6960) night sky
with a few small cream-colored star dots, but NO ground, NO trees, NO buildings, NO hills — just open
sky. Place a circular moon positioned high up with plenty of empty sky around it and no nearby
objects to compare it to.

CRITICAL — exact size match: the two moons must have EXACTLY the same diameter in pixels, as if cut
from the same circular stencil (this is essential, since the whole point of this illustration is that
the two moons are actually the same size). As a concrete target, make each moon's diameter
approximately 14% of the panel's width, and make sure both panels' moons match this same size exactly
— do not draw the right-panel moon any smaller just because it has no nearby objects for scale. Do
not write any letter, number, or label on or near either moon (no "M", no size markers) — each moon
is a plain colored circle with a soft brown outline and a few soft crater dots only.

Below both panels, add a short Japanese caption spanning the width of the image: "月の大きさは、実はどちらも同じ".
Below that, add a second short caption: "まわりに目印があると、大きく感じられる、という説(比較対象説)".
Both captions must be well within the image bounds (not touching the bottom edge), with generous
margin below them.

[共通スタイル指定を貼り付け]

All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read
for children, in the dark brown color (#483628). Do not add any numbers, percentages, or measurement
marks to this image — it is a purely visual, illustrative comparison.
```

**生成後の確認ポイント**: 左右の月が**ピクセル上で本当に同じ大きさ**に描かれているか(**要ピクセル計測**。1回目の生成では約188px対約171pxと約9%の差があり、目視だけでは見落としていた。Pythonで直径を測って必ず数値で確認する)。左パネルの月の上や近くに「M」等の文字・記号が誤って書き込まれていないか確認。左パネル(地平線近く)には木・建物・山などの目印があり、右パネル(空高く)には何も無い開けた夜空になっているか。ラベルが「比較対象説」という名称のみで、「証明された」「これが正解」等の断定表現になっていないか確認。地名・実在の建物名などが書き込まれていないか確認。

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

Place TWO horizontal bars, one near the top and one near the bottom, both centered on the vertical
midline of the image:
- One bar placed HIGH UP, near the top where the two converging lines are close together (the
  "far away" position) — draw this bar in terracotta orange (#E08454).
- One bar placed LOWER DOWN, near the bottom where the two converging lines are far apart (the
  "close up" position) — draw this bar in deep teal (#3A6960).

CRITICAL — fixed equal length, NOT matched to the lines: both bars must be drawn with the exact same
fixed pixel length as each other — for example, each bar should be about 22% of the image's total
width, regardless of how far apart the two converging lines are at that height. Do NOT resize either
bar to snugly fit the gap between the lines at its own height — the gap between the lines is narrower
at the top and wider at the bottom, but the two bars themselves must NOT follow that difference.
Because of this: the TOP (orange) bar will naturally stick out a little PAST the two converging lines
on both sides (since the line-gap is narrower than the bar there), and the BOTTOM (teal) bar will
naturally fall short of reaching the two converging lines, leaving a visible empty gap on both sides
(since the line-gap is wider than the bar there). This mismatch between the bars and the lines is
correct and intentional — it must look like two identical-length bars simply placed at different
heights inside the same converging-lines shape, not like two bars custom-fit to the shape. To help
confirm the equal length visually, add a small thin dashed vertical tick mark at each end of both
bars, and a faint dashed vertical extension line connecting the top bar's tick marks straight down to
the bottom bar's tick marks, showing that the two bars line up exactly if compared directly (even
though they sit at different distances from the converging lines around them).

Add a bold Japanese title at the top of the image, in the open space above the converging lines'
meeting point: "ポンゾ錯視". Below the whole illustration, add a short Japanese caption: "この2本の棒、じつは同じ長さです" and beneath that a second smaller caption: "奥にあるほうが、大きく見えてしまいます".
Do NOT include any moon, sun, or celestial imagery in this illustration — it illustrates the general
optical-illusion phenomenon on its own, not the moon directly.

[共通スタイル指定を貼り付け]

All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read
for children, in the dark brown color (#483628). Leave a generous margin (at least 8% of the image
height/width) around all four edges so nothing (lines, bars, text) touches the border.
```

**生成後の確認ポイント**: 2本の収束する線が、上に向かって狭まる(遠近感のある)構図になっているか。
2本の横棒(奥側・手前側)が**実際に同じ長さ**で描かれているか(**要ピクセル計測**。目視だけで判断しない
— 過去に「線の間にぴったり収める」という誤った期待から、実際には長さが違う棒が生成された経緯があるため
特に厳重に確認する)。**むしろ、奥側(オレンジ)の棒は収束線からはみ出し気味に、手前側(ティール)の棒は
収束線に届かず隙間ができている状態が正しい**(収束線の間隔そのものに棒を合わせてしまっていたら失敗、
作り直す)。月や太陽の絵が紛れ込んでいないか確認(この図は現象単体の説明であり、月に直接結びつける描写は
しない)。「これが正解」「証明された」等の断定表現が入っていないか確認。

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
