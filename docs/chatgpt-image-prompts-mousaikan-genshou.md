# ChatGPT用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「毛細管現象」用イラスト一式
**確定タイトル**: 「タオルの端が、ひとりでに濡れていく? 「毛細管現象」だけでは、高い木のてっぺんまで水を届けられない」(49字)
**用途**: ChatGPT(画像生成)にそのまま貼り付けて使うプロンプト。実際の画像生成はユーザーがこのプロンプトを
ChatGPTに貼り付けて行う。このドキュメントの作成者(illustrator)は画像そのものを生成していない。
**方針**: 過去記事(mosquito-on, jishin-sokuho 等)と同様、**文字入り版のみ**を用意する。

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | 既存の `profile/icon.png`(500×500)をそのまま流用。**作り直さない** |
| 記事カバー(`covers/mousaikan-genshou.png`) | ✅ 1回目の生成で目視上は合格(タイトル3行・タオルと木の構図とも問題なし)。ただし現時点では
  画像ファイルへのアクセスができず保存未了(下記「既知の問題」参照) |
| 解説イラスト1(`illustrations/mousaikan-tube-comparison.png`、太い管/細い管の水面比較) | ✅ 1回目の生成で目視上は合格(細い管の水面が明確に高く、取り違えなし)。保存未了 |
| 解説イラスト2(`illustrations/mousaikan-nureseishitsu.png`、ガラス面/ロウ面の濡れ性対比) | ❌ 1回目の生成でロウ面側のラベルに「0はじかれる」という文字化けが発生。ラベル文言を
  シンプルな2行構成に修正済み。再生成待ち |
| 解説イラスト3(`illustrations/mousaikan-shokubutsu.png`、植物の給水と蒸散の引っぱり) | ❌ 1回目の生成で、プロンプト内の見出し語("LOW"・"BELOW"・"ABOVE"・"ONE"・番号"1)""2)")が
  そのまま英単語として画像内に描画される不具合、および日本語ラベルの文字重複(文字化け)が発生。
  プロンプトを見出し語を使わない自然文に全面的に書き直した。再生成待ち |

**既知の問題(2026-09-14時点)**: この記事の画像はChatGPTで4枚とも生成されユーザーから共有されたが、
この環境からアップロード画像ファイルへのアクセスができない状態が続いており、カバー・イラスト1は
目視確認のみで保存(リポジトリへのコミット)ができていない。イラスト2・3は上記の不具合のため
いずれにせよ再生成が必要。画像アクセスが復旧し次第、4枚とも(再生成分を含め)保存・ピクセル検証を行うこと。

---

## 共通スタイル指定(毎回のプロンプト冒頭に付けると絵柄が揃います)

```
Flat, warm, friendly children's educational illustration style (like a Japanese picture book for
elementary schoolers). Simple flat shapes, soft rounded corners, gentle and calm mood, no
photorealism, no realistic human faces. Clean vector-like line art with a warm brown outline
(#483628). Color palette limited to exactly these four colors: cream background (#FBF3E4),
terracotta orange (#E08454, shadow tone #BF673C), deep teal (#3A6960, light teal #92B5AB), and the
dark brown outline/text color (#483628). Cheerful, curious, textbook-diagram mood, appropriate for
children.
```

---

## 1. 記事カバー(`covers/mousaikan-genshou.png`、1280×670)

### タイトルの行分け・文字サイズ(コードで確認、過去記事と比較して計算)

タイトル文字数の確認:
```bash
python3 -c "
t='タオルの端が、ひとりでに濡れていく? 「毛細管現象」だけでは、高い木のてっぺんまで水を届けられない'
print(len(t))
"
# => 49
```

自然な句読点・区切りで3行に分けると次の通り(疑問符・読点の直後で改行、単語やフレーズの途中では折らない):
- 1行目(18字): `タオルの端が、ひとりでに濡れていく?`
- 2行目(12字): `「毛細管現象」だけでは、`
- 3行目(18字): `高い木のてっぺんまで水を届けられない`
- 合計48字(+行送りで置き換わる区切りの空白1字 = タイトル全体49字と一致)

**文字サイズの根拠(過去記事との比較で計算)**:
過去記事 `jishin-sokuho`(39字・最長行15字)と `mosquito-on`(40字)のカバーでは、実測で問題なく
3行に収まった実績がある。本記事は49字で最長行が18字(jishin比 +3字/行、約1.2倍)のため、同じ
1280px幅のキャンバスに収めるには文字サイズを比例して縮小する必要がある。

概算: カバー幅1280pxのうち左右マージンを引いた実効テキスト幅を約1075px(全体の84%)とし、
太字の日本語フォントは1文字あたりの見かけ幅をおよそ「フォントサイズ×0.95」とすると、
- jishin(最長15字): 1075 ÷ (15×0.95) ≈ 75px相当のフォントサイズで実測OKだった
- 本記事(最長18字): 1075 ÷ (18×0.95) ≈ 63px相当のフォントサイズが目安

つまり **jishin/mosquito のカバーで使われたサイズよりおよそ15〜20%小さいフォントサイズ**を
目安として明示する。3行分の行の高さ(行間込みで1行あたりフォントサイズの約1.3倍 ≈ 82px)×3行
+行間 ≈ 260〜280px。これに上マージン(画像高さ670pxの約8% ≈ 54px)を足すと、タイトルブロックは
画像上部から約330〜340px(画像高さの約半分)に収まり、残り半分強を下のイラストに使える計算になる
(過去記事のレイアウト比率と概ね一致)。

```
A wide horizontal illustration (aspect ratio approximately 16:8.4, matching a 1280×670 canvas), flat
warm children's picture-book style, calm and curious educational mood.

In the lower-center area of the image, draw a simple cheerful scene: a soft, rounded bath towel
(cream-white fabric with a warm terracotta-orange stripe near its edge) with one corner dipping into
a small round bowl or cup of water. Along the towel fabric just above the water line, draw a gentle
upward gradient of a slightly darker, damp-looking tone spreading a short distance up from the
water's surface, showing the water climbing up into the fabric on its own. A few small simple wavy
light-teal lines near the bowl's water surface suggest calm water.

To the right of the towel scene, draw one tall, simple, friendly-looking tree (a slim trunk with a
single rounded leafy top in deep teal) reaching up toward the upper edge of the image, noticeably
taller than the towel-and-bowl scene beside it, to visually hint that the same "water climbing on its
own" idea also relates to how a much taller tree gets its water. Keep the tree simple and iconic
(like a lollipop-shaped picture-book tree), not detailed or realistic.

Leave calm, uncluttered cream background space in the upper 45-50% of the image, above the towel and
tree illustration, for the title text.

[共通スタイル指定を貼り付け]

Include a title in the upper area of the image, in bold, clearly legible Japanese text, broken into
exactly 3 lines with these natural phrase breaks (do not break in the middle of a word or phrase, do
not merge or reorder the lines):
Line 1: タオルの端が、ひとりでに濡れていく?
Line 2: 「毛細管現象」だけでは、
Line 3: 高い木のてっぺんまで水を届けられない
This title is 49 characters total across 3 lines (18 / 12 / 18 characters). Because the longest line
has 18 characters, size the font noticeably smaller than a typical short 3-word title — roughly
15-20% smaller than you would use for a 3-line title with a 15-character longest line — so that all 3
lines comfortably fit within the image width with a calm margin on both sides, without touching the
left or right edges and without overlapping the towel/tree illustration below.
CRITICAL: leave a generous empty margin (at least 8% of the image height) between the very top edge
of the image and the top of line 1's characters — no part of any character (including small marks
like "゛", "」", or "?") may be cropped or touch the top border.
The title text must be crisp, correctly formed Japanese characters (not garbled), in the dark brown
color (#483628), positioned with calm uncluttered plain background directly behind it so it stays
readable.
```

**生成後の確認ポイント**:
- タイトルが指定通り3行(18/12/18字、計49字)に収まり、上端・左右端で文字が切れていないか(必ず拡大して確認)。
- 文字がjishin/mosquito等の過去カバーと比べて窮屈になっていないか(最長行が18字と長いため、フォントが
  小さめに調整されているか)。
- タオルの端が水につかり、水面から上に向かって色が変化する「濡れて登っていく」表現になっているか
  (単に濡れているだけでなく、上向きの動きが示唆されているか)。
- 右側の木がタオルの場面より明確に背が高く描かれ、画像上端に向かって伸びているか(「高い木」のニュアンスが
  伝わるか)。
- 配色が指定の4色(クリーム/テラコッタオレンジ/ディープティール/ダークブラウン)の範囲内に収まっているか。

---

## 2. 解説イラスト1: 太い管と細い管の水面の高さの違い(`illustrations/mousaikan-tube-comparison.png`)

本文該当箇所(L14・L26付近、本文L28の📎マーカー)の要旨: 同じ水に、太さの違う管を同時につけると、
細い管の方が水面がより高い位置まで登る。管が細いほど水は高く登る、という「管の太さ」の効果を示す図。

**重要(取り違え防止)**: 太い管は水面の上がり方が小さく(低く)、細い管は水面の上がり方が大きい(高く)。
左右どちらに配置してもよいが、ラベルと高さの対応を絶対に逆にしないこと。

```
A single simple illustration, flat warm children's picture-book style: one shallow, wide round bowl
of calm water (light teal #92B5AB water, cream-colored bowl with a dark brown outline), viewed from
the front/side like a cutaway. Two transparent drinking-straw-like tubes stand upright in the same
bowl of water, side by side, both starting from the exact same water surface level in the bowl.

On the LEFT: a visibly THICK tube (wide diameter). Inside it, the water has climbed only a SMALL
distance above the bowl's water surface — mark this with a short horizontal dashed line at the top of
the water inside the thick tube, and a small vertical double-arrow beside the tube measuring this
short rise. Label this tube in Japanese below it: "太い管".

On the RIGHT: a visibly THIN tube (narrow diameter), clearly thinner than the left tube. Inside it,
the water has climbed a CLEARLY TALLER distance above the bowl's water surface — mark this with a
horizontal dashed line at the top of the water inside the thin tube (positioned noticeably higher up
the tube than the thick tube's dashed line), and a small vertical double-arrow beside it measuring
this taller rise. Label this tube in Japanese below it: "細い管".

CRITICAL for placement: the water level inside the THIN tube must be drawn clearly and visibly HIGHER
than the water level inside the THICK tube (roughly twice as high), while both tubes start from the
exact same water surface in the shared bowl. The thick tube's rise must stay short; do not make the
two tubes' internal water levels equal, and do not make the thick tube's water level higher than the
thin tube's.

Add one small caption above the whole scene, in Japanese: "管が細いほど、水は高くのぼる".

[共通スタイル指定を貼り付け]
All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read
for children, in the dark brown color (#483628).
```

**生成後の確認ポイント**: 太い管・細い管が同じ水面(同じ器)から立ち上がっているか(比較の前提が公平か)。
**細い管の水面の方が太い管より明確に高い**か(逆になっていたら失敗、作り直す)。ラベル「太い管」「細い管」が
実際の管の太さと対応しているか(取り違えていないか)。本文にない具体的な高さの数値(cm等)を書き加えていないか。

---

## 3. 解説イラスト2: ガラス面とロウを塗った面での水のふるまいの違い(`illustrations/mousaikan-nureseishitsu.png`)

本文該当箇所(L24、本文L32の📎マーカー)の要旨: 「濡れ性」の説明。ガラスに水を入れると、水はガラスの壁に
くっついて広がろうとする。ロウを塗ったつるつるの面だと、水は丸い玉のようになってはじかれる。

**重要(取り違え防止)**: ガラス面=水が壁にくっついて広がる(濡れ性が高い)。ロウ面=水が玉になってはじかれる
(濡れ性が低い)。左右どちらに配置してもよいが、ラベルと形状の対応を絶対に逆にしないこと。

**改訂履歴**: 1回目の生成でロウ面側のラベルに「0はじかれる」のような余分な文字が混入する文字化けが
発生した。ラベルの文中に丸括弧や記号を詰め込みすぎると崩れやすい可能性を考え、ラベルをより短く
シンプルな2行構成に分割した。

```
A single illustration, flat warm children's picture-book style, divided into two side-by-side panels
on a shared cream background, each panel showing a flat horizontal surface viewed from a slight angle
with a drop of water resting on it.

LEFT PANEL: a smooth, pale, slightly bluish flat surface representing glass (light teal #92B5AB tint,
with a thin dark brown outline suggesting a glass panel). On top of it, a puddle of water spreads out
thin and wide, with its edges gently curving UP where they meet the surface (like the water is
clinging to and climbing the surface slightly at its edges), showing the water "wants" to stick to
and spread across the glass. Below this panel, add two short separate Japanese caption lines,
stacked vertically, in plain text with no brackets or parentheses: first line "ガラス", second line
"水がくっつきたがる".

RIGHT PANEL: a flat surface with a warm terracotta-orange (#E08454) glossy-looking coating,
representing a wax-coated surface. On top of it, the water forms a single small, neat, ROUND bead
(like a marble), sitting up high with a narrow point of contact with the surface, clearly not
spreading out at all. Below this panel, add two short separate Japanese caption lines, stacked
vertically, in plain text with no brackets or parentheses: first line "ロウを塗った面", second line
"水がはじかれる".

CRITICAL for shape: the LEFT panel's water must be spread thin and wide with edges curving up
(clinging to the surface); the RIGHT panel's water must be a compact round bead barely touching the
surface (being pushed away from it). Do not swap these two shapes between the panels, and do not make
both panels look the same.

[共通スタイル指定を貼り付け]
All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read
for children, in the dark brown color (#483628).
```

**生成後の確認ポイント**: 左パネル(ガラス)で水が薄く広がり、縁が持ち上がるように表現されているか。
右パネル(ロウ面)で水が丸い玉になっているか。**左=広がる・右=玉になる、の対応が逆になっていないか**
(逆なら失敗、作り直す)。**ラベルの文字が崩れていないか(余分な数字・記号が紛れ込んでいないか)拡大して
必ず確認する**(1回目の生成で「0はじかれる」のような文字化けが発生した経緯があるため)。

---

## 4. 解説イラスト3: 根から吸われた水が道管を通り、蒸散の引っぱりで高いところまで運ばれる図(`illustrations/mousaikan-shokubutsu.png`)

本文該当箇所(L36〜48、本文L50の📎マーカー)の要旨:
- 道管という細い管の中でも毛細管現象と同じ仕組みで水が少し持ち上がるが、**その力だけで持ち上げられる高さは
  せいぜい数メートルほど**(道管の太さから計算できる目安)。
- 10メートルを超える高い木では、それだけでは足りない。
- 葉の裏側の穴から水が水蒸気になって出ていく「蒸散」によって、道管の中の水が上へ引っぱられる。
- 水分子どうしは手をつなぐように結びついているので、途中でちぎれずに一本の水の糸のように引き上げられる
  (凝集力)。
- 高い木のてっぺんまで水が届くのは、**毛細管現象だけの力ではなく**、蒸散の「引っぱり」と水分子どうしの
  「結びつき」が合わさった結果(凝集力-張力説)。

**最重要(誤った単純化の防止)**: この図は「毛細管現象だけで説明が完結する」ように見えてはいけない。
必ず、(a)毛細管現象だけで届く高さには限りがあること(木の低い位置までしか届かないこと)、
(b)そこから上は蒸散の引っぱりと水分子どうしの結びつきで運ばれていること、の**2段階が視覚的に区別できる**
構図にする。本文にない具体的な数値(何メートル、何%等)は書き加えない。使ってよい目安は本文にある
「数メートルほど」という言葉のみ(具体的な数字を新たに書き込まない)。

**改訂履歴**: 1回目の生成で、プロンプト内の見出し語("BOTTOM"、"BELOW"、"ABOVE"、"ONE"、番号付き
リストの"1)"「2)")が、そのまま英単語として画像内にテキスト描画されてしまう不具合が起きた。
また日本語ラベルの一部も「持ち上がる高で持ち上がる高さ」のように重複した文字化けが生じた。
今回はプロンプトを箇条書き・見出し語を使わない自然な説明文に全面的に書き直し、画像内に描画してよい
テキストは明示的に列挙したラベルのみである旨を強調した。

```
A single tall illustration, flat warm children's picture-book style, showing a cutaway cross-section
of the ground and a very tall tree, from its roots near the bottom edge of the image to its leafy top
near the upper edge.

Near the bottom of the image, draw simple roots in warm brown, spreading into the cream-colored
ground, with a few small light-teal wavy lines representing water in the soil being drawn up into the
roots. From the roots, a single simple vertical tube runs straight up through the center of the trunk,
representing the 道管 (water-carrying tube), filled with a continuous light-teal color all the way up
to the top of the tree, representing an unbroken column of water.

A short horizontal dashed line crosses the tube near the bottom of the trunk, close to the roots and
far below the halfway point of the tree's total height — this dashed line marks a boundary between two
visually different sections of the water column, described below.

In the short section of the tube between the roots and this dashed line, draw a few small upward
arrows in deep teal along the water column. Place a small Japanese label next to this short section,
connected to it with a thin leader line, reading exactly: "毛細管現象で持ち上がる高さ 数メートルほど".

In the long section of the tube above the dashed line, continuing all the way up through the rest of
the tall trunk to the very top leaves, draw the water column as a chain of small connected circles
linked by short connecting lines (like a beaded chain), representing water molecules holding onto each
other. Place a small Japanese label next to this long section, connected to it with a thin leader
line, reading exactly: "蒸散の引っぱりと水分子どうしの結びつきで、ここまで運ばれる".

Near the top of the tree, draw simple rounded leaves in deep teal. Near a few leaves, draw small,
gentle upward-curving wavy lines in light teal drifting away from the leaf surface into the air,
representing water vapor leaving through tiny pores, with a small Japanese label reading exactly:
"葉から水蒸気が出ていく". Draw one small upward arrow right at the top of the beaded water chain,
touching the base of these wavy vapor lines, showing the vapor loss is what pulls the water chain
upward from above.

The tree must be drawn tall, with the dashed boundary line placed low on the trunk, so it is visually
obvious that the short lower section (with the upward arrows) covers only a small bottom fraction of
the tree's total height, while the long upper section (with the beaded chain) covers the large
majority of the height, all the way to the top. Do not place the dashed boundary line near the middle
or top of the tree, and do not make the two sections similar in size.

Add one small caption near the top of the whole image, in Japanese, reading exactly: "毛細管現象だけで
なく、蒸散の引っぱりと水分子の結びつきが合わさって、高いところまで水が届く".

The only text allowed anywhere in this image is: the four Japanese labels and the one Japanese caption
quoted above, plus the single word "道管" as a label pointing to the tube. Do not add any other words,
letters, numbers, or English text anywhere in the image — no section headers, no "top"/"bottom" markers,
no numbering. Every piece of text in the final image must be one of the exact Japanese phrases listed
above, nothing else.

[共通スタイル指定を貼り付け]
All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read for
children, in the dark brown color (#483628). Keep the whole illustration simple and diagram-like,
similar to a picture book's cutaway illustration of a tree.
```

**生成後の確認ポイント**:
- **"LOW"「BELOW」「ABOVE」「ONE」等の英単語や、"1)"「2)」のような番号が、画像内にそのまま文字として
  描き込まれていないか拡大して確認する**(1回目の生成でプロンプトの見出し語が誤って画像内テキストとして
  描画される不具合が起きたため、最優先で確認すること。混入していたら失敗、作り直す)。
- 図が「毛細管現象だけで説明が完結する」ように見えていないか(最重要)。点線の境界線が幹の**低い位置**に
  あり、「毛細管現象」ゾーンが木全体の高さのうちごく一部(明らかに半分未満)にとどまっているか。
- 境界線より上の大部分が、水分子の鎖(結びつき)の表現と、葉の蒸散(水蒸気が出ていく矢印・波線)による
  「引っぱり」の表現で占められているか。
- 日本語ラベルの文字が重複・崩れていないか(「持ち上がる高で持ち上がる」のような文字化けが無いか)拡大して確認する。
- 本文にある「数メートルほど」という言葉以外に、具体的な数値(高さの数字・パーセンテージ等)を新たに
  書き加えていないか。
- 根→道管→葉、という水の通り道が一本の連続した管として描かれ、水の連続性(ちぎれていない一本の糸のような
  イメージ)が視覚的に伝わるか。

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
  ```bash
  python3 -c "from PIL import Image;print(Image.open('covers/mousaikan-genshou.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/mousaikan-tube-comparison.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/mousaikan-nureseishitsu.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/mousaikan-shokubutsu.png').size)"
  ```
- [ ] 日本語テキスト(タイトル・ラベルとも)が崩れていないか拡大して確認
- [ ] カバー: タイトルが3行(18/12/18字、計49字)に収まり、上端・左右端で文字が切れていないか確認
- [ ] カバー: フォントサイズが過去記事(jishin/mosquito、最長15〜字)より小さめに調整されているか確認
      (最長行18字を1280px幅に収めるため)
- [ ] イラスト1: **細い管の水面が太い管より明確に高い**か確認(逆なら失敗)。両方の管が同じ水面(同じ器)
      から立ち上がっているか確認
- [ ] イラスト2: **左=ガラス=水が広がる/右=ロウ面=水が玉になる**の対応が逆になっていないか確認
- [ ] イラスト3: 「毛細管現象だけで説明が完結する」ように見えていないか確認(境界線が幹の低い位置にあり、
      蒸散の引っぱり+水分子の結びつきのゾーンが大部分を占めているか)
- [ ] イラスト3: 本文に無い具体的な数値(数メートル以外の数字)が書き加えられていないか確認
- [ ] 全画像: 配色が指定の4色(クリーム#FBF3E4/テラコッタオレンジ#E08454・陰影#BF673C/ディープティール
      #3A6960・淡色#92B5AB/ダークブラウン#483628)の範囲内に収まっているか確認
- [ ] プロフィールアイコンは既存の `profile/icon.png` をそのまま使い、作り直していないか確認

保存先の目安: `covers/mousaikan-genshou.png` /
`illustrations/mousaikan-tube-comparison.png`(太い管/細い管の水面の高さ比較)/
`illustrations/mousaikan-nureseishitsu.png`(ガラス面/ロウ面の濡れ性対比)/
`illustrations/mousaikan-shokubutsu.png`(植物の給水と蒸散の引っぱり)

生成後、本文中の📎マーカーを画像貼り付け手順に反映してください(マーカー自体は `note-formatter` が
実画像への差し替えを行う担当のため、ここでは生成物のファイルパスが本文の📎マーカーの指定と
一致していることのみ確認する):
- `illustrations/mousaikan-tube-comparison.png` … 本文L28のマーカーと一致
- `illustrations/mousaikan-nureseishitsu.png` … 本文L32のマーカーと一致
- `illustrations/mousaikan-shokubutsu.png` … 本文L50のマーカーと一致

## 注記(このドキュメントの位置づけ)

このドキュメントは ChatGPT(画像生成)に貼り付けるプロンプトの作成のみを行ったものであり、
実際の画像ファイル(`covers/mousaikan-genshou.png` 等)はまだ生成・保存されていない。
プロンプトをChatGPTに貼り付けて画像を生成したのち、上記チェックリストに沿って検証し、
サイズ調整(PIL等での1280×670・横1200pxへのリサイズ)を行うこと。
