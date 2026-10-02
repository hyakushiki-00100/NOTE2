# Gemini用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「ライデンフロスト効果」(`articles/leidenfrost-koka.md`)用イラスト一式
**確定タイトル**: 「熱いフライパンで、水が玉になって転がるのはなぜ? 「ライデンフロスト効果」、熱すぎると水はかえって長持ちする」(54字。「?」と直後のスペースは半角)
**用途**: Gemini(画像生成)にそのまま貼り付けて使うプロンプト。画像生成そのものはこの文書の作成者ではなく、
オーナーが Gemini に貼り付けて行う。
**方針**: 過去記事(バンドワゴン効果・氷はなぜ水に浮くのか 等)と同様、**文字入り版のみ**を用意する。

**このプロンプト集で入れている対策(前回までの失敗パターン)**:
- 共通スタイル指定は、各プロンプトのコードブロック内に**全文埋め込み済み**。コードブロックをそのまま1回コピーすれば足りる。
- プロンプト本文には英大文字の見出し・番号付きの見出しを書いていない(前回、見出し語「STAGE 1/2/3」が画像に描き込まれたため)。
  色コードも小文字で書き、「色コードは画像に書かない」と明記している。
- 各プロンプトの最後に「画像に描いてよい文字は次の日本語だけ」と列挙し、それ以外の文字・英語・数字を禁止している。
- 矢印は「どこから出て、どこで終わるか」を具体的に書いている。

**安全・内容面の制約(全画像共通)**:
- 人物・手・顔は一切描かない(子どもや人物がフライパンを扱う姿は、まねを誘うため描かない)。ライデンフロスト等の肖像も描かない。
- 油・食材・炎は描かない(熱さは控えめな波線で表す)。危険をあおる表現にしない。
- 本文にない数値・固有名詞は描かない。図1には数字・目盛り・単位を一切入れない。
- 水蒸気は目に見えない(本文40〜42行目)ため、白い湯気の雲・もくもくした煙は描かない。図2の「蒸気の膜」は淡いティールの帯で模式的に表す。

---

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | ✅ 既存の `profile/icon.png` をそのまま流用。作り直さない |
| 記事カバー(`covers/leidenfrost-koka.png`、1280×670) | ⬜ 未生成 |
| 解説イラスト1(`illustrations/leidenfrost-01.png`、温度と水のつぶが消えるまでの時間の山形の模式図) | ⬜ 未生成 |
| 解説イラスト2(`illustrations/leidenfrost-02.png`、そこまで熱くないフライパン/とても熱いフライパンの断面図) | ⬜ 未生成 |

生成後、下記「生成後のチェックリスト」に沿ってサイズ・内容をコードと目視で検証し、Opus QA(`note-qa`)にかけること。

---

## 共通スタイル指定

以下の各プロンプトには**あらかじめ本文中に埋め込み済み**なので、コピペ時に別途貼り付ける必要はありません
(参考として内容だけここに残しています)。

```
Flat, warm, friendly children's educational illustration in the style of a Japanese picture book for elementary school children. Simple flat shapes with soft rounded corners and clean vector-like lines with a dark brown outline (#483628). No photorealism. Use only these colors: cream background (#fbf3e4), terracotta orange (#e08454) with its shadow tone (#bf673c), deep teal (#3a6960) with its light tone (#92b5ab), and dark brown (#483628) for outlines and text. Do not introduce any other colors and do not use gradients that create new colors. The color codes are instructions for you only; never write color codes, letters or numbers into the image. The mood is calm, gentle and cheerful, suitable for children, and nothing should look scary or dangerous. Do not draw any people, hands, faces or portraits anywhere in the image.
```

色の使い分け(3枚で統一): フライパン=テラコッタオレンジ(側面・断面の陰は #bf673c)、水=ディープティール、
蒸気の膜=淡いティール、熱を表す波線・矢印=テラコッタの陰影色、線・文字=ダークブラウン。

---

## 1. 記事カバー(`covers/leidenfrost-koka.png`, 1280×670)

本文冒頭のフック(よく熱したフライパンに水のしずくが落ちると、ジュッと消えずに丸い玉になってころころ転がる)を絵にする。
タイトルは確定済みなので、そのまま画像内に焼き込む。タイトルが5行になるため、**左側にタイトル、右側にフライパン**の
左右レイアウトにする。

**注意**: 人物・手・油・食材・炎・ガスコンロのつまみ等は描かない。フライパンと水の玉だけが主役。本文の数値(200℃・1756年等)や
人名はカバーに入れない。

```
A wide horizontal illustration for a 1280x670 pixel canvas (aspect ratio about 1.91 to 1), with a plain cream background.

On the right side of the image, occupying roughly the right 45 percent of the width, draw one simple frying pan seen from slightly above, so that the round flat inside of the pan is visible as a wide oval. The pan is terracotta orange (#e08454) with its outer side wall in the shadow tone (#bf673c) and a dark brown handle. The handle points toward the lower right and must stay completely inside the image. Nobody is holding the pan: there are no hands and no people anywhere. There is no oil, no food and no flame. To show that the pan is hot, draw only three or four short, gentle wavy lines in the shadow tone (#bf673c) just below the bottom of the pan; keep them small and calm, not like fire.

On the flat inside of the pan, draw four round water balls of slightly different sizes, colored deep teal (#3a6960) with one small cream highlight on each, like shiny marbles. They sit on the pan as round balls, not flat puddles. Behind two of the balls, draw two or three short curved motion lines in dark brown, so that it looks like those balls are rolling and sliding across the pan. Do not draw any white steam, smoke or clouds above the pan or the balls.

On the left side of the image, occupying roughly the left 55 percent of the width, place the title in bold, clearly legible Japanese text in dark brown (#483628), left-aligned, in exactly five lines broken like this:
熱いフライパンで、
水が玉になって転がるのはなぜ?
「ライデンフロスト効果」、
熱すぎると水は
かえって長持ちする
The full title is 「熱いフライパンで、水が玉になって転がるのはなぜ? 「ライデンフロスト効果」、熱すぎると水はかえって長持ちする」 and every character must match it exactly, with no characters added, removed or changed. Choose a font size so that the longest line, the second line with fifteen characters, fits within the left area without touching the frying pan; all five lines use the same font size. Leave a clear empty margin above the first line equal to at least 8 percent of the image height, so that no part of any character touches or is cut off by the top edge. Also leave a margin of at least 5 percent of the image width at the left edge and at least 8 percent of the image height below the last line. The title and the frying pan must not overlap.

Flat, warm, friendly children's educational illustration in the style of a Japanese picture book for elementary school children. Simple flat shapes with soft rounded corners and clean vector-like lines with a dark brown outline (#483628). No photorealism. Use only these colors: cream background (#fbf3e4), terracotta orange (#e08454) with its shadow tone (#bf673c), deep teal (#3a6960) with its light tone (#92b5ab), and dark brown (#483628) for outlines and text. Do not introduce any other colors and do not use gradients that create new colors. The color codes are instructions for you only; never write color codes, letters or numbers into the image. The mood is calm, gentle and cheerful, suitable for children, and nothing should look scary or dangerous. Do not draw any people, hands, faces or portraits anywhere in the image.

The only text allowed in the image is the Japanese title above, written in those five lines. Do not draw any other text, letters, English words, numbers, color codes, labels, logos or brand names anywhere in the image.
```

**生成後の確認ポイント**:
- タイトルが指定どおり5行(熱いフライパンで、/水が玉になって転がるのはなぜ?/「ライデンフロスト効果」、/熱すぎると水は/かえって長持ちする)で、文字が窮屈になっていないか。
- タイトルの文言が確定タイトルと一字一句一致しているか(「ライデンフロスト」のカタカナの欠落・入れ替わり、「長持ち」「転がる」の字形崩れに特に注意)。「?」が全角で描かれる程度の差は許容。
- タイトル1行目の文字上端が画像の上端で切れていないか(拡大して確認)。タイトルとフライパンが重なっていないか。
- 人物・手・油・食材・炎が描かれていないか。熱を表す波線が炎のように大きく、危険をあおる見た目になっていないか。
- 水が「丸い玉」として描かれ、平たい水たまりになっていないか。転がっている動きの線があるか。
- 白い湯気・煙・雲が描き込まれていないか。
- 英字・数字・色コード・ロゴが紛れ込んでいないか。

---

## 2. 解説イラスト1: 温度と水のつぶが消えるまでの時間(`illustrations/leidenfrost-01.png`)

本文該当箇所: 34行目の📎(「もっと熱いのに、もっと長く残る」節の末尾)。要旨: 途中までは熱いほど水は早く蒸発する。
ところがある温度を越えると水は玉になって長く残るようになり、さらに熱くすると、また早く消えるようになる。

**重要(本文にない事実を追加しない)**:
- 本文は「何℃から起きるのかは、一つの数字には決まりません」と書いている。**数字・目盛り・単位・補助線は一切描かない。**
  山の頂点に点・縦の点線・印をつけない(頂点を特定の温度として示さない)。
- 吹き出しは「頂点の一点」ではなく、山の部分全体(長く残る範囲)を指すように、山の下を淡いティールで塗った範囲に向ける。
- 曲線の形: 左端は中くらいの高さ → 下がって谷(すぐ消える)→ 急に上がって丸い山(長く残る)→ ゆるやかに下がる。
  谷のそばに「広がって泡立つ水」、山の範囲に「丸い水の玉」の小さなアイコンを添える(本文22〜24行目の記述に対応)。

```
A wide horizontal illustration with a 16 to 9 aspect ratio and a plain cream background, showing a very simple picture-style chart for children. It is not a scientific graph: there are no numbers, no tick marks, no units, no grid lines and no dashed lines anywhere.

Draw a horizontal axis as a thick dark brown arrow running along the bottom of the image from the left side to the right side, with its arrowhead pointing to the right. Directly below the right half of this arrow, write the Japanese label 「フライパンの温度」 horizontally.

Draw a vertical axis as a thick dark brown arrow running up the left side of the image from the bottom to near the top, with its arrowhead pointing up. The two arrows meet at the lower left corner. Just above the arrowhead at the top of this vertical arrow, write the Japanese label 「水のつぶが消えるまでの時間」 horizontally, reading from left to right.

Between the two axes, draw one smooth, thick curved line in terracotta orange (#e08454). The curve starts at the left, near the vertical axis, at about the middle height of the chart. Moving to the right, it goes down to a low valley at about one third of the way across. From the valley it rises steeply to a broad, rounded hilltop a little to the right of the center; this hilltop is clearly the highest part of the whole curve. After the hilltop, the curve slopes gently downward toward the right end, finishing at a little below the middle height. Do not put a dot, a marker, a vertical line or any label exactly on the top of the hill.

Fill the area under the hill part of the curve, from where the curve starts rising after the valley until where it has come down again on the right, with the light teal color (#92b5ab), so that the whole hill reads as one broad range rather than one point. Inside this light teal area, draw one small round water ball in deep teal (#3a6960) with a tiny cream highlight, sitting as a perfect little ball.

Just above the low valley, draw one small icon of a flat, spread-out puddle of water in deep teal with a few small cream bubbles in it, and next to that icon write the short Japanese label 「すぐ消える」.

Above the hill, draw one rounded speech balloon with a cream inside and a dark brown outline, containing the Japanese text 「蒸気のクッションで長持ち」. The tail of the balloon points down into the middle of the light teal area under the hill, not at the very top of the curve.

Keep a margin of at least 8 percent of the image height above the top label, and at least 6 percent of the width on the left and right, so no text or arrow touches the edges.

Flat, warm, friendly children's educational illustration in the style of a Japanese picture book for elementary school children. Simple flat shapes with soft rounded corners and clean vector-like lines with a dark brown outline (#483628). No photorealism. Use only these colors: cream background (#fbf3e4), terracotta orange (#e08454) with its shadow tone (#bf673c), deep teal (#3a6960) with its light tone (#92b5ab), and dark brown (#483628) for outlines and text. Do not introduce any other colors and do not use gradients that create new colors. The color codes are instructions for you only; never write color codes, letters or numbers into the image. The mood is calm, gentle and cheerful, suitable for children, and nothing should look scary or dangerous. Do not draw any people, hands, faces or portraits anywhere in the image.

All Japanese text must be crisp, correctly formed characters in dark brown, large enough for children to read. The only text allowed in the image is these Japanese words: 「フライパンの温度」「水のつぶが消えるまでの時間」「すぐ消える」「蒸気のクッションで長持ち」. Do not draw any other text, letters, English words, numbers, degree signs, units, color codes or symbols used as text anywhere in the image.
```

**生成後の確認ポイント**:
- **数字・目盛り・単位(℃等)・グリッド線・点線が一切描かれていないか**(最重要。1つでもあれば作り直すか除去する)。
- 曲線が「中くらい → 谷 → 高い山 → ゆるやかに下がる」の形になっているか。山が全体でいちばん高いか。右端でまた下がっているか。
- 山の頂点に点・縦線・印がついて、特定の温度を指しているように見えないか。
- 吹き出しのしっぽが頂点の一点ではなく、山の下の淡いティールの範囲を指しているか。
- 谷のそばに「広がって泡立つ水」と「すぐ消える」、山の範囲に「丸い水の玉」があり、取り違えていないか(谷に玉、山に水たまりになっていないか)。
- 横軸ラベル「フライパンの温度」・縦軸ラベル「水のつぶが消えるまでの時間」・吹き出し「蒸気のクッションで長持ち」の文字が崩れていないか、端で切れていないか。
- 英字・数字・色コードが紛れ込んでいないか。

---

## 3. 解説イラスト2: そこまで熱くないフライパン/とても熱いフライパンの断面図(`illustrations/leidenfrost-02.png`)

本文該当箇所: 74行目の📎(「水のつぶの下にできる「蒸気のクッション」」節の末尾)。要旨:
- **左「そこまで熱くないフライパン」**: 蒸気の膜が続かず、水はフライパンにじかにふれて広がる。熱がどんどん流れこみ、泡を立てて激しく沸騰し、あっという間に消える(本文68〜70行目)。
- **右「とても熱いフライパン」**: 丸い水の玉とフライパンのあいだに、うすい蒸気の層(蒸気の膜)がある。膜には「浮かせるクッション」(フライパンにほとんどふれずにすべる)と「熱をさえぎる」(熱は少しずつしか届かない)の2つの働きがある(本文44〜64行目)。

**重要(仕組みを歪めない)**:
- 水蒸気は目に見えない(本文40〜42行目)。**蒸気の膜は白い湯気の雲ではなく、淡いティールの平たい帯**で模式的に表す。左右とも白い湯気・煙を描かない。
- 膜の厚さは見やすさのために誇張した模式表現。厚さの数値は入れない。
- 「熱をさえぎる」は「完全に止める」ではない(本文「少しずつしか届きません」)。右側では太い熱の矢印が膜で止まり、**細い矢印が1本だけ**水の玉に届く形にする。
- 左右の対比: 左は太い熱の矢印が水に直接たくさん入る/右は膜で止まる。

```
A wide horizontal illustration with a 16 to 9 aspect ratio and a plain cream background, divided into a left half and a right half by one thin vertical dark brown line placed exactly at the horizontal center of the image. Both halves show a close-up side cross-section of the flat bottom of a frying pan, drawn the same way in both halves: a thick horizontal slab in terracotta orange (#e08454) with its cut face in the shadow tone (#bf673c), lying across the lower part of each half at the same height and with the same thickness on both sides. There are no people, no hands, no oil, no food and no flames.

At the top of the left half, write the Japanese label 「そこまで熱くないフライパン」. Below it, on top of the pan slab, draw water as a wide, flat, spread-out puddle in deep teal (#3a6960) that touches the top surface of the pan directly along its entire bottom, with no gap at all. Inside the puddle, draw many small round bubbles with cream insides and dark brown outlines: some bubbles are just forming on the pan surface at the bottom of the puddle, some are rising through the water, and two or three are popping at the top surface of the puddle with tiny splash marks, to show strong boiling. From the top surface of the pan, draw four thick wavy arrows in the shadow tone (#bf673c); each arrow starts at the pan surface and points upward, going straight into the puddle and ending inside the water, showing that a lot of heat flows directly into the water. Do not draw any white steam, smoke or clouds above the puddle.

At the top of the right half, write the Japanese label 「とても熱いフライパン」. Below it, draw one round water ball in deep teal (#3a6960) with a small cream highlight, a little smaller in width than the left puddle. The ball does not touch the pan at all. Between the bottom of the ball and the top surface of the pan, there is a thin, flat band in the light teal color (#92b5ab) with a thin dark brown outline; this band spreads under the whole bottom of the ball and fills the gap completely, so that the ball rests on the band like a cushion. The band is clearly thinner than the ball, about one fifth of the ball's height. This band represents invisible water vapor, so draw it as a smooth flat band, not as white fluffy steam or clouds. Directly below the band, write the short Japanese label 「蒸気の膜」, placed on the cut face of the pan slab or just beside the band, with a thin dark brown line connecting the label to the band.

Inside the light teal band, directly under the ball, draw two short, bold dark brown arrows pointing straight up; each arrow starts in the band and its tip touches the bottom of the ball, showing that the band pushes the ball up. To the left of the ball, at the height of the band, write the Japanese label 「浮かせるクッション」 and connect it with a thin dark brown line to these two upward arrows.

From the top surface of the pan in the right half, draw three thick wavy arrows in the shadow tone (#bf673c) pointing upward. These three thick arrows stop at the lower edge of the light teal band, each ending in a short flat bar, as if they hit a wall; they do not enter the ball. Next to them, draw only one thin, short wavy arrow in the same color that passes through the band and just reaches the bottom of the ball, showing that only a little heat gets through. To the right of the ball, write the Japanese label 「熱をさえぎる」 and connect it with a thin dark brown line to the point where the thick arrows stop at the band. Do not draw any white steam, smoke or clouds above the ball.

Keep a margin of at least 8 percent of the image height above the top labels and at least 5 percent of the width on the left and right, so that no text, arrow or shape touches the edges.

Flat, warm, friendly children's educational illustration in the style of a Japanese picture book for elementary school children. Simple flat shapes with soft rounded corners and clean vector-like lines with a dark brown outline (#483628). No photorealism. Use only these colors: cream background (#fbf3e4), terracotta orange (#e08454) with its shadow tone (#bf673c), deep teal (#3a6960) with its light tone (#92b5ab), and dark brown (#483628) for outlines and text. Do not introduce any other colors and do not use gradients that create new colors. The color codes are instructions for you only; never write color codes, letters or numbers into the image. The mood is calm, gentle and cheerful, suitable for children, and nothing should look scary or dangerous. Do not draw any people, hands, faces or portraits anywhere in the image.

All Japanese text must be crisp, correctly formed characters in dark brown, large enough for children to read. The only text allowed in the image is these Japanese words: 「そこまで熱くないフライパン」「とても熱いフライパン」「蒸気の膜」「浮かせるクッション」「熱をさえぎる」. Do not draw any other text, letters, English words, numbers, units, color codes or symbols used as text anywhere in the image.
```

**生成後の確認ポイント**:
- **左右の取り違えがないか(最重要)**: 左「そこまで熱くないフライパン」=水が平たく広がり、フライパンにじかにふれて泡立っている/右「とても熱いフライパン」=丸い水の玉の下に淡いティールの帯がある。
- 右の水の玉がフライパンに接しておらず、帯が玉の底とフライパンのあいだを埋めているか。左の水たまりにはすき間・帯が無いか。
- 蒸気の膜が白い湯気・もくもくした雲として描かれていないか。左右とも、水の上に白い湯気・煙が描かれていないか。
- 「浮かせるクッション」の線が、帯の中から玉の底へ向かう上向き矢印を指しているか。
- 「熱をさえぎる」の線が、太い熱の矢印が帯で止まっている位置を指しているか。太い矢印が玉の中まで入り込んでいないか。細い矢印が1本だけ玉に届いているか(「完全に遮断」に見えないこと)。
- 左の熱の矢印が水の中まで入っているか(左右の対比が成り立っているか)。
- 左右のフライパンの断面が同じ高さ・同じ厚さか(片方だけ極端に厚い・薄いと、温度以外の違いがあるように見える)。
- 5つのラベル(そこまで熱くないフライパン/とても熱いフライパン/蒸気の膜/浮かせるクッション/熱をさえぎる)の文字が崩れていないか、端で切れていないか。
- 数字・英字・色コード・炎・油・人物が紛れ込んでいないか。

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
  ```bash
  python3 -c "from PIL import Image;print(Image.open('covers/leidenfrost-koka.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/leidenfrost-01.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/leidenfrost-02.png').size)"
  ```
- [ ] 日本語テキスト(タイトル・軸ラベル・吹き出し・ラベルとも)が崩れていないか拡大して確認
- [ ] カバーのタイトルが確定タイトルと一字一句一致しているか確認(「熱いフライパンで、水が玉になって転がるのはなぜ? 「ライデンフロスト効果」、熱すぎると水はかえって長持ちする」・54字)
- [ ] カバーのタイトルが指定の5行で、上端・左端・フライパンに接していないか確認
- [ ] プロンプトの指示文(英語の文・見出し語・色コード等)が画像に描き込まれていないか確認(前回「STAGE 1/2/3」の描き込みがあったため)
- [ ] 全画像共通: 人物・手・顔・肖像・油・食材・炎が描かれていないか確認(安全上、まねを誘う描写を入れない)
- [ ] 全画像共通: 白い湯気・煙・雲が描かれていないか確認(本文「水蒸気は目に見えない」と矛盾させない)
- [ ] イラスト1: 数字・目盛り・単位・補助線が一切なく、山の頂点が特定の温度として示されていないか確認(最重要)
- [ ] イラスト1: 曲線が「中くらい → 谷 → 山 → ゆるやかに下がる」の形か確認
- [ ] イラスト2: 左右の場面(広がって沸騰/玉の下に蒸気の膜)とラベルの対応が正しいか確認(最重要)
- [ ] イラスト2: 「浮かせるクッション」「熱をさえぎる」の線・矢印が、それぞれ上向き矢印/熱の矢印が止まる位置を指しているか確認
- [ ] 全画像共通: 配色がブランドパレット6色(クリーム・テラコッタ・テラコッタ陰影・ディープティール・淡ティール・ダークブラウン)の範囲内に収まっているか確認
- [ ] 本文にない具体的な数値・固有名詞(温度・年号・人名等)が画像内に紛れ込んでいないか確認
- [ ] プロフィールアイコンは既存の `profile/icon.png` をそのまま使い、作り直していないか確認

保存先の目安: `covers/leidenfrost-koka.png` /
`illustrations/leidenfrost-01.png`(温度と水のつぶが消えるまでの時間の山形の模式図)/
`illustrations/leidenfrost-02.png`(そこまで熱くないフライパン/とても熱いフライパンの断面図)

生成後、本文中の📎マーカーに対応するファイルパスが一致していることを確認してください(マーカー自体を
実画像への記法に差し替えるのは `note-formatter` の担当です):
- `illustrations/leidenfrost-01.png` … `articles/leidenfrost-koka.md` 34行目の📎(「もっと熱いのに、もっと長く残る」節の末尾)
- `illustrations/leidenfrost-02.png` … `articles/leidenfrost-koka.md` 74行目の📎(「水のつぶの下にできる「蒸気のクッション」」節の末尾)
