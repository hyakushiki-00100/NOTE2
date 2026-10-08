# Gemini用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「お風呂で指がしわしわになるのはなぜ?」(`articles/yubi-no-shiwa.md`)用イラスト一式
**確定タイトル**: 「お風呂で指がしわしわになるのはなぜ? 水を吸っただけじゃない、神経が血管を細くしてつくるしわ」(46字。「?」と直後のスペースは半角)
**用途**: Gemini(画像生成)にそのまま貼り付けて使うプロンプト。画像生成そのものはこの文書の作成者ではなく、
オーナーが Gemini に貼り付けて行う。
**方針**: 過去記事(ライデンフロスト効果・氷はなぜ水に浮くのか 等)と同様、**文字入り版のみ**を用意する。

**このプロンプト集で入れている対策(前回までの失敗パターン)**:
- 共通スタイル指定は、各プロンプトのコードブロック内に**全文埋め込み済み**。コードブロックをそのまま1回コピーすれば足りる。
- プロンプト本文には英大文字の見出し・番号付きの見出しを書いていない(前回、見出し語「STAGE 1/2/3」が画像に描き込まれたため)。
  色コードも小文字で書き、「色コードは画像に書かない」と明記している。
- 各プロンプトの最後に「画像に描いてよい文字は次の日本語だけ」と列挙し、それ以外の文字・英語・数字・色コードを禁止している。
- 矢印は「どこから出て、どこで終わるか」を具体的に書いている。
- 左右に並べる図(イラスト1・2)は、左半分・右半分それぞれの中身を別の段落で書き分け、確認ポイントにも左右の取り違えを入れている。
- カバーのタイトルは5行の改行位置を具体的に指定し、上端の余白とイラストとの非重複を明記している。

**安全・内容面の制約(全画像共通)**:
- **手・指は絵本調のやわらかいイラストにする**(写実的な手・皮ふの質感は描かない)。生成AIは指の本数を間違えやすいため、
  **全画像とも「指1本の先だけ」のクローズアップ**にし、手のひら・手首・ほかの指が画面に出ない構図にしている
  (指の本数が問題にならない)。
- **肌の色**: 指はパレットのクリーム(#fbf3e4)で塗り、ダークブラウンの輪郭線で描く。背景の円を淡いティールにして
  指と区別する。特定の人種を連想させる肌色は使わない。しわの線はテラコッタの陰影色(#bf673c)。
- **人の顔・頭・全身は描かない**(指先だけ)。
- **神経のけが・病気・医療の場面(病院、医師、注射、検査器具、包帯など)は描かない。**本文22〜32行目の
  「神経が傷ついている人」「神経の検査」は図にしない(本文の📎の指示「病気やけがを連想させる絵は描かない」に従う)。
- 本文にない数値・固有名詞は描かない。本文中の年(1930年代・1973年・2003年・2017年 等)・研究者名・大学名・
  雑誌名・「12%」「40℃」「30分」等の数値も**画像には一切入れない**。図2の皮ふの断面に寸法の数値・目盛りは入れない。
- 図2の断面は模式図。血管は左右で**同じ位置・同じ高さ**に描き、右だけ細くする(位置まで変わると、別の場所の断面に見えるため)。

---

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | ✅ 既存の `profile/icon.png` をそのまま流用。作り直さない |
| 記事カバー(`covers/yubi-no-shiwa.png`、1280×670) | ✅ 生成・保存済み。生成画像はタイトル2・3行目(「なぜ?」「、」)が右の丸い絵に重なり、指の中ほどの横向きの弧線2本がしずくと合わさって笑った顔に見えたため、PILで弧線を消し、丸い絵を78%に縮めて右へ寄せた(タイトルとの間隔は最小約40px)。もとの丸の跡は背景色で埋め、タイトルの文字は残した |
| 解説イラスト1(`illustrations/yubi-no-shiwa-01.png`、ふつうの指先/お湯につかったあとのしわしわの指先の比較) | ✅ 生成・保存済み(1200×670) |
| 解説イラスト2(`illustrations/yubi-no-shiwa-02.png`、指先の皮ふの断面の左右比較と、しわができる流れ) | ✅ 生成・保存済み(1200×670) |

生成後、下記「生成後のチェックリスト」に沿ってサイズ・内容をコードと目視で検証し、Opus QA(`note-qa`)にかけること。

---

## 共通スタイル指定

以下の各プロンプトには**あらかじめ本文中に埋め込み済み**なので、コピペ時に別途貼り付ける必要はありません
(参考として内容だけここに残しています)。

```
Flat, warm, friendly children's educational illustration in the style of a Japanese picture book for elementary school children. Simple flat shapes with soft rounded corners and clean vector-like lines with a dark brown outline (#483628). No photorealism. Use only these colors: cream background (#fbf3e4), terracotta orange (#e08454) with its shadow tone (#bf673c), deep teal (#3a6960) with its light tone (#92b5ab), and dark brown (#483628) for outlines and text. Do not introduce any other colors and do not use gradients that create new colors. The color codes are instructions for you only; never write color codes, letters or numbers into the image. The mood is calm, gentle and cheerful, suitable for children, and nothing should look scary, painful or dangerous. Do not draw any faces, heads, bodies or portraits of people anywhere in the image. Whenever a finger appears, draw it as a soft, simple, rounded picture-book shape filled with cream (#fbf3e4) and outlined in dark brown, never realistic and without any skin texture, so that it does not suggest any particular skin color. Do not draw hospitals, doctors, nurses, needles, syringes, bandages, medical instruments or anything that suggests injury or illness.
```

色の使い分け(3枚で統一): 指=クリーム+ダークブラウンの輪郭、指の後ろの丸い窓=淡いティール、お湯・水滴=ディープティール、
しわの線=テラコッタの陰影色、角質層(皮ふのいちばん外側の層)=テラコッタオレンジ、血管=テラコッタの陰影色、
神経=ディープティールの線、流れを示す矢印=テラコッタオレンジ、線・文字=ダークブラウン。

---

## 1. 記事カバー(`covers/yubi-no-shiwa.png`, 1280×670)

本文冒頭のフック(お風呂に長くつかったあと、ふと手を見ると指先がしわしわになっていた)を絵にする。
タイトルは確定済みなので、そのまま画像内に焼き込む。タイトルが5行になるため、**左側にタイトル、右側に指先の丸い窓**の
左右レイアウトにする。

**注意**: 指の本数の誤りを避けるため、お湯から**指が1本だけ**出ている構図にする(手のひら・ほかの指は水面の下で見えない)。
顔・全身・湯船につかる人物は描かない。湯気(白いもくもく)は入れない。本文の数値・年・人名はカバーに入れない。

```
A wide horizontal illustration for a 1280x670 pixel canvas (aspect ratio about 1.91 to 1), with a plain cream background.

On the right side of the image, occupying roughly the right 40 percent of the width, draw one large circle with a light teal (#92b5ab) fill and a thick dark brown outline, like a round window giving a close-up view. The circle is vertically centered and stays completely inside the image, with a clear margin from the top, bottom and right edges. The lower quarter of the inside of the circle is bath water in deep teal (#3a6960), with a gently curved water surface and two or three small cream ripple lines on it.

One single finger rises straight up out of this bath water, seen from the palm side, with its softly rounded tip in the upper part of the circle and not touching the circle outline. Only this one finger is visible: the rest of the hand stays hidden under the water, so there is no palm, no wrist, no other fingers and no fingernail anywhere. The finger is a soft, simple, rounded picture-book shape filled with cream (#fbf3e4) and outlined in dark brown. On the soft rounded pad near the tip of the finger, draw five or six soft wavy wrinkle lines in the shadow tone (#bf673c), running mostly up and down along the finger, so that the fingertip looks gently wrinkled, like a raisin. The part of the finger near the water surface has no wrinkle lines. Add two or three small round water drops in deep teal with a tiny cream highlight on the finger. Do not draw any steam, smoke, clouds, soap bubbles, bath foam, toys or people.

On the left side of the image, occupying roughly the left 58 percent of the width, place the title in bold, clearly legible Japanese text in dark brown (#483628), left-aligned, in exactly five lines broken like this:
お風呂で指が
しわしわになるのはなぜ?
水を吸っただけじゃない、
神経が血管を細くして
つくるしわ
The full title is 「お風呂で指がしわしわになるのはなぜ? 水を吸っただけじゃない、神経が血管を細くしてつくるしわ」 and every character must match it exactly, with no characters added, removed or changed. Choose a font size so that the longest lines, the second and third lines with twelve characters each, fit within the left area without touching the circle; all five lines use the same font size. Leave a clear empty margin above the first line equal to at least 8 percent of the image height, so that no part of any character touches or is cut off by the top edge. Also leave a margin of at least 5 percent of the image width at the left edge and at least 8 percent of the image height below the last line. The title and the circle must not overlap.

Flat, warm, friendly children's educational illustration in the style of a Japanese picture book for elementary school children. Simple flat shapes with soft rounded corners and clean vector-like lines with a dark brown outline (#483628). No photorealism. Use only these colors: cream background (#fbf3e4), terracotta orange (#e08454) with its shadow tone (#bf673c), deep teal (#3a6960) with its light tone (#92b5ab), and dark brown (#483628) for outlines and text. Do not introduce any other colors and do not use gradients that create new colors. The color codes are instructions for you only; never write color codes, letters or numbers into the image. The mood is calm, gentle and cheerful, suitable for children, and nothing should look scary, painful or dangerous. Do not draw any faces, heads, bodies or portraits of people anywhere in the image. Whenever a finger appears, draw it as a soft, simple, rounded picture-book shape filled with cream (#fbf3e4) and outlined in dark brown, never realistic and without any skin texture, so that it does not suggest any particular skin color. Do not draw hospitals, doctors, nurses, needles, syringes, bandages, medical instruments or anything that suggests injury or illness.

The only text allowed in the image is the Japanese title above, written in those five lines. Do not draw any other text, letters, English words, numbers, color codes, labels, logos or brand names anywhere in the image.
```

**生成後の確認ポイント**:
- タイトルが指定どおり5行(お風呂で指が/しわしわになるのはなぜ?/水を吸っただけじゃない、/神経が血管を細くして/つくるしわ)で、文字が窮屈になっていないか。
- タイトルの文言が確定タイトルと一字一句一致しているか(「風呂」「吸」「神経」「血管」「細く」の字形崩れ、「しわしわ」の「わ」の欠落・重複に特に注意)。「?」が全角で描かれる程度の差は許容。「?」の後ろのスペースは改行に置き換わるので、行頭に空白が無くてよい。
- タイトル1行目の文字上端が画像の上端で切れていないか(拡大して確認)。タイトルと右の丸い窓が重なっていないか。
- 指が**1本だけ**か。手のひら・手首・ほかの指・爪が描かれていないか。写実的な手・皮ふの質感になっていないか。
- 指の色がクリーム(パレット内)で、特定の肌色(ベージュ・茶色等の新しい色)になっていないか。
- しわが指先の腹(先端の丸い部分)にあり、怖い・痛そうな見た目(ひび割れ・傷のように見える等)になっていないか。
- 顔・人物・湯気・おもちゃ・医療を連想させるものが描かれていないか。
- 英字・数字・色コード・ロゴが紛れ込んでいないか。

---

## 2. 解説イラスト1: ふつうの指先/お湯につかったあとの指先(`illustrations/yubi-no-shiwa-01.png`)

本文該当箇所: 34行目の📎(「しわになる場所と、ならない場所」節の末尾)。要旨:
- **左「ふつうの指先」**: 指先の腹がなめらかで、しわが無い。
- **右「お湯につかったあとの指先」**: 指先の腹がしわしわになっている(本文4〜8行目、18行目)。
- 右下に小さなメモ「腕は、指先のようなしわにはならない」(本文18行目「腕やおなかは同じようにお湯につかっていても、
  指先のようなしわにはなりません」の表現に合わせた短いラベル)。

**重要(内容面)**:
- 📎の指示どおり、しわは**指先の腹の部分**に描く。神経が傷ついた手など、病気やけがを連想させる絵は描かない。
- 指の本数の誤りを避けるため、左右とも**指1本の先だけ**を丸い窓の中に描く(指は窓の下端から入り、窓のふちで切れて見える)。
  左右で指の形・大きさ・位置をそろえ、違いが「しわの有無」だけに見えるようにする。
- 腕のメモには腕の絵を添えない(腕だけを切り取った絵は、子どもに不気味に見えるおそれがあるため。文字のメモだけにする)。

```
A wide horizontal illustration with a 16 to 9 aspect ratio and a plain cream background, divided into a left half and a right half by one thin vertical dark brown line placed exactly at the horizontal center of the image. Both halves are drawn the same way: a short Japanese label at the top, and below it one large circle with a light teal (#92b5ab) fill and a dark brown outline, like a round window giving a close-up view. The two circles have the same size and are at the same height. Inside each circle there is one single finger, seen from the palm side, pointing straight up. The finger enters the circle from the bottom edge of the circle and is cut off by the circle outline there, so only the upper part of one finger is visible, with its softly rounded tip in the upper part of the circle. There is no palm, no wrist, no other fingers and no fingernail anywhere in the image. The fingers in the two circles have exactly the same shape, size and position; they are soft, simple, rounded picture-book shapes filled with cream (#fbf3e4) and outlined in dark brown.

At the top of the left half, write the Japanese label 「ふつうの指先」. In the circle of the left half, the finger is completely smooth: there are no lines at all on the pad of the fingertip, and no water drops.

At the top of the right half, write the Japanese label 「お湯につかったあとの指先」. In the circle of the right half, on the soft rounded pad near the tip of the finger, draw five or six soft wavy wrinkle lines in the shadow tone (#bf673c), running mostly up and down along the finger, so that the fingertip looks gently wrinkled, like a raisin. The lower part of the finger, near the bottom edge of the circle, has no wrinkle lines. Add two or three small round water drops in deep teal (#3a6960) with a tiny cream highlight on this finger. The wrinkles must look soft and harmless, not like cracks, cuts or scratches.

In the lower right corner of the right half, below and to the right of the circle and not overlapping it, draw one small rounded rectangle with a cream fill and a thin dark brown outline, containing the short Japanese note 「腕は、指先のようなしわにはならない」 written in one line in smaller dark brown text. Do not draw an arm or any other body part for this note; it is text only.

Keep a margin of at least 8 percent of the image height above the top labels and at least 5 percent of the width on the left and right, so that no text, circle or shape touches the edges.

Flat, warm, friendly children's educational illustration in the style of a Japanese picture book for elementary school children. Simple flat shapes with soft rounded corners and clean vector-like lines with a dark brown outline (#483628). No photorealism. Use only these colors: cream background (#fbf3e4), terracotta orange (#e08454) with its shadow tone (#bf673c), deep teal (#3a6960) with its light tone (#92b5ab), and dark brown (#483628) for outlines and text. Do not introduce any other colors and do not use gradients that create new colors. The color codes are instructions for you only; never write color codes, letters or numbers into the image. The mood is calm, gentle and cheerful, suitable for children, and nothing should look scary, painful or dangerous. Do not draw any faces, heads, bodies or portraits of people anywhere in the image. Whenever a finger appears, draw it as a soft, simple, rounded picture-book shape filled with cream (#fbf3e4) and outlined in dark brown, never realistic and without any skin texture, so that it does not suggest any particular skin color. Do not draw hospitals, doctors, nurses, needles, syringes, bandages, medical instruments or anything that suggests injury or illness.

All Japanese text must be crisp, correctly formed characters in dark brown, large enough for children to read. The only text allowed in the image is these Japanese words: 「ふつうの指先」「お湯につかったあとの指先」「腕は、指先のようなしわにはならない」. Do not draw any other text, letters, English words, numbers, units, color codes or symbols used as text anywhere in the image.
```

**生成後の確認ポイント**:
- **左右の取り違えがないか(最重要)**: 左「ふつうの指先」=指先がなめらかでしわが無い/右「お湯につかったあとの指先」=指先の腹にしわがあり、水滴がついている。
- 左右とも指が**1本だけ**か。手のひら・手首・ほかの指・爪が描かれていないか。左右で指の形・大きさ・位置がそろっているか。
- しわが指先の腹(先端の丸い部分)にあり、ひび割れ・傷・ひっかき傷のように見えないか。
- 腕のメモ「腕は、指先のようなしわにはならない」が右下にあり、右の丸い窓と重なっていないか。文字が崩れていないか(「腕」の字形に注意)。腕の絵が勝手に描き足されていないか。
- 指の色がクリーム(パレット内)で、新しい肌色が使われていないか。
- 3つのラベル(ふつうの指先/お湯につかったあとの指先/腕は、指先のようなしわにはならない)が端で切れていないか。
- 顔・人物・医療を連想させるもの・英字・数字・色コードが紛れ込んでいないか。

---

## 3. 解説イラスト2: 指先の皮ふの断面(ふだん/長く水につかったあと)(`illustrations/yubi-no-shiwa-02.png`)

本文該当箇所: 64行目の📎(「中身がへると、外側があまってしわになる」節の末尾)。要旨:
- **左「ふだん」**: 皮ふの下の血管がふつうの太さで、表面はなめらか。
- **右「長く水につかったあと」**: 神経からの合図で血管が細くなり(本文40〜42行目)、皮ふの下の中身が減って(本文58行目)、
  表面が内側に引きこまれて波打つ(本文62行目)。
- 流れ: 「神経の合図」→「血管が細くなる」→「中身が減る」→「表面がしわに」を、画像下部の帯に左から右への矢印で示す。
- 外側の層(角質層)はテラコッタオレンジで色分けし、右側に「水を吸ってふくらむ」と小さく注記する(本文70〜72行目)。

**重要(仕組みを歪めない)**:
- 断面は模式図。寸法の数値・目盛りは入れない。層の厚さ・血管の太さは見やすさのための誇張。
- 血管は左右で**同じ位置・同じ高さ**に描き、右だけ細くする。
- 「神経の合図」は、神経の線の先から血管へ向かう短い矢印で表す(右側だけ。左には合図の矢印を描かない)。
  稲妻・火花のような強い表現にしない。
- しわは「表面が**内側(下)へ**引きこまれる」形。表面が上へ盛り上がってこぶ状になると本文と逆に見えるため、くぼみが下向きになるようにする。
- 角質層の「水を吸ってふくらむ」は小さな注記にとどめる。本文76行目のとおり、ふくらみの関わりの大きさは研究途中のため、
  角質層を右だけ極端に厚くして「主な原因」に見せない(左右で同じ厚さにする)。

```
A wide horizontal illustration with a 16 to 9 aspect ratio and a plain cream background. It is a simple, picture-style cross-section diagram for children, not a medical drawing. There are no numbers, no scales, no tick marks and no measurements anywhere.

The upper 70 percent of the image is divided into a left half and a right half by one thin vertical dark brown line placed exactly at the horizontal center of the image; this line does not continue into the bottom strip described later. Each half shows a close-up side cross-section of the skin of a fingertip as one wide rectangular block with softly rounded lower corners and a dark brown outline, drawn the same way in both halves: the two blocks have the same width, the same height and the same position, and their bottom edges are at exactly the same height. Each block is made of these parts, from top to bottom. First, along the top of the block, a thin outer layer of skin in terracotta orange (#e08454), about one eighth of the block height, with the same thickness in both halves. Below it, the inside of the skin, filled with cream (#fbf3e4). Running horizontally across the whole width of this cream inside, at the middle height of the block, one blood vessel drawn as a long tube in the shadow tone (#bf673c) with a dark brown outline. Below the blood vessel, one thin nerve drawn as a deep teal (#3a6960) line that comes up from the bottom edge of the block and ends a short distance below the blood vessel, without touching it. The blood vessel and the nerve are at exactly the same positions and heights in both halves.

At the top of the left half, write the Japanese label 「ふだん」. In the left block, the top surface of the skin is a straight, smooth, flat line, and the blood vessel is a thick tube, about one fifth of the block height. There is no arrow between the nerve and the blood vessel in the left block. To the right of the left block, write three short Japanese labels, each connected to its part with a thin dark brown line: 「角質層」 connected to the terracotta outer layer, 「血管」 connected to the blood vessel tube, and 「神経」 connected to the deep teal nerve line.

At the top of the right half, write the Japanese label 「長く水につかったあと」. In the right block, the blood vessel runs at exactly the same height as in the left block but is clearly thinner, about half as thick as the left one. From the top end of the nerve, draw one short bold arrow in terracotta orange that starts at the tip of the nerve line and points straight up, ending at the lower edge of the thin blood vessel, showing the nerve sending a signal to the blood vessel; draw it as a simple arrow, not as lightning or sparks. In the right block, the top surface of the skin is no longer flat: it is a gentle wavy line with three or four soft dips that sink downward into the block, as if the surface is pulled inward; the highest parts of the waves are at about the same height as the flat surface of the left block, and the dips go lower. The terracotta outer layer follows these waves with the same thickness as in the left block. Because of the dips, the cream inside of the right block is a little smaller than in the left block. Above the right block, write the small Japanese note 「水を吸ってふくらむ」 in smaller text, connected with a thin dark brown line pointing down to the terracotta outer layer.

In the bottom 25 percent of the image, across the full width, draw one horizontal row of four rounded rectangles with a cream fill and a dark brown outline, evenly spaced, containing these Japanese words in this order from left to right: 「神経の合図」, 「血管が細くなる」, 「中身が減る」, 「表面がしわに」. Between each pair of neighboring rectangles, draw one bold arrow in terracotta orange (#e08454) that starts at the right edge of the left rectangle and ends at the left edge of the next rectangle, pointing to the right. There are exactly three such arrows. There is no arrow before the first rectangle and no arrow after the last rectangle.

Keep a margin of at least 8 percent of the image height above the top labels and below the bottom row, and at least 5 percent of the width on the left and right, so that no text, arrow or shape touches the edges.

Flat, warm, friendly children's educational illustration in the style of a Japanese picture book for elementary school children. Simple flat shapes with soft rounded corners and clean vector-like lines with a dark brown outline (#483628). No photorealism. Use only these colors: cream background (#fbf3e4), terracotta orange (#e08454) with its shadow tone (#bf673c), deep teal (#3a6960) with its light tone (#92b5ab), and dark brown (#483628) for outlines and text. Do not introduce any other colors and do not use gradients that create new colors. The color codes are instructions for you only; never write color codes, letters or numbers into the image. The mood is calm, gentle and cheerful, suitable for children, and nothing should look scary, painful or dangerous. Do not draw any faces, heads, bodies or portraits of people anywhere in the image. Whenever a finger appears, draw it as a soft, simple, rounded picture-book shape filled with cream (#fbf3e4) and outlined in dark brown, never realistic and without any skin texture, so that it does not suggest any particular skin color. Do not draw hospitals, doctors, nurses, needles, syringes, bandages, medical instruments or anything that suggests injury or illness.

All Japanese text must be crisp, correctly formed characters in dark brown, large enough for children to read. The only text allowed in the image is these Japanese words: 「ふだん」「長く水につかったあと」「角質層」「血管」「神経」「水を吸ってふくらむ」「神経の合図」「血管が細くなる」「中身が減る」「表面がしわに」. Do not draw any other text, letters, English words, numbers, units, color codes or symbols used as text anywhere in the image.
```

**生成後の確認ポイント**:
- **左右の取り違えがないか(最重要)**: 左「ふだん」=表面が平らでなめらか、血管が太い、神経から血管への矢印が無い/右「長く水につかったあと」=表面が波打ち、血管が細い、神経の先から血管へ上向きの矢印がある。
- 血管が左右で**同じ高さ・同じ位置**にあり、右だけ細くなっているか(位置がずれていないか)。左右の断面ブロックの大きさ・下端の高さがそろっているか。
- 右の表面のくぼみが**下向き(内側へ引きこまれる向き)**か。上へ盛り上がったこぶになっていないか。
- 角質層(テラコッタの外側の層)が左右で同じ厚さで、右だけ極端に厚くなっていないか。右の波に沿っているか。
- 「水を吸ってふくらむ」の線が角質層を指しているか(血管や中身を指していないか)。
- 左の「角質層」「血管」「神経」の線が、それぞれテラコッタの外側の層/血管の管/ティールの神経の線を指しているか(取り違えがないか)。
- 右の神経→血管の矢印が、神経の先から出て血管の下端で終わっているか。稲妻・火花のような怖い表現になっていないか。
- 下の帯が「神経の合図 → 血管が細くなる → 中身が減る → 表面がしわに」の順で、矢印がちょうど3本、すべて右向きか。
- 10個の文字(ふだん/長く水につかったあと/角質層/血管/神経/水を吸ってふくらむ/神経の合図/血管が細くなる/中身が減る/表面がしわに)が崩れていないか(「角質層」「神経」「血管」「減」の字形に注意)、端で切れていないか。
- 数字・目盛り・寸法・英字・色コード・医療器具・人物が紛れ込んでいないか。

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
  ```bash
  python3 -c "from PIL import Image;print(Image.open('covers/yubi-no-shiwa.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/yubi-no-shiwa-01.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/yubi-no-shiwa-02.png').size)"
  ```
- [ ] 日本語テキスト(タイトル・ラベル・注記・流れの帯とも)が崩れていないか拡大して確認
- [ ] カバーのタイトルが確定タイトルと一字一句一致しているか確認(「お風呂で指がしわしわになるのはなぜ? 水を吸っただけじゃない、神経が血管を細くしてつくるしわ」・46字)
- [ ] カバーのタイトルが指定の5行で、上端・左端・右の丸い窓に接していないか確認
- [ ] プロンプトの指示文(英語の文・見出し語・色コード等)が画像に描き込まれていないか確認(前回「STAGE 1/2/3」の描き込みがあったため)
- [ ] 全画像共通: 指が1本だけで、手のひら・手首・ほかの指・爪が描かれていないか確認(指の本数の誤りを避ける構図)
- [ ] 全画像共通: 指が写実的でなく絵本調か、肌の色がパレット内(クリーム)で特定の肌色になっていないか確認
- [ ] 全画像共通: 顔・頭・全身・人物、病院・医師・注射・検査器具・包帯など医療やけが・病気を連想させるものが描かれていないか確認
- [ ] イラスト1: 左右(なめらか/しわしわ)とラベルの対応が正しいか、しわが指先の腹にあるか確認(最重要)
- [ ] イラスト1: 「腕は、指先のようなしわにはならない」のメモが右下にあり、丸い窓と重なっていないか、腕の絵が描き足されていないか確認
- [ ] イラスト2: 左右(ふだん/長く水につかったあと)とラベルの対応が正しいか、血管が左右で同じ位置で右だけ細いか確認(最重要)
- [ ] イラスト2: 右の表面のくぼみが内側(下)向きか、神経→血管の矢印が右側だけにあるか、下の帯の順序と矢印3本が正しいか確認
- [ ] イラスト2: 寸法の数値・目盛りが一切無いか、角質層が右だけ極端に厚くなっていないか確認
- [ ] 全画像共通: 配色がブランドパレット6色(クリーム・テラコッタ・テラコッタ陰影・ディープティール・淡ティール・ダークブラウン)の範囲内に収まっているか確認
- [ ] 本文にない具体的な数値・固有名詞(年・研究者名・大学名・雑誌名・温度・時間・%等)が画像内に紛れ込んでいないか確認
- [ ] プロフィールアイコンは既存の `profile/icon.png` をそのまま使い、作り直していないか確認

保存先の目安: `covers/yubi-no-shiwa.png` /
`illustrations/yubi-no-shiwa-01.png`(ふつうの指先/お湯につかったあとの指先の比較)/
`illustrations/yubi-no-shiwa-02.png`(指先の皮ふの断面の左右比較と、しわができる流れ)

生成後、本文中の📎マーカーに対応するファイルパスが一致していることを確認してください(マーカー自体を
実画像への記法に差し替えるのは `note-formatter` の担当です):
- `illustrations/yubi-no-shiwa-01.png` … `articles/yubi-no-shiwa.md` 34行目の📎(「しわになる場所と、ならない場所」節の末尾)
- `illustrations/yubi-no-shiwa-02.png` … `articles/yubi-no-shiwa.md` 64行目の📎(「中身がへると、外側があまってしわになる」節の末尾)
