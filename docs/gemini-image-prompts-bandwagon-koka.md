# Gemini用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「バンドワゴン効果」用イラスト一式
**確定タイトル**: 「行列に並びたくなるのはなぜ? 「バンドワゴン効果」には、正反対の心理にも名前がついている」(44字)
**用途**: Gemini(画像生成)にそのまま貼り付けて使うプロンプト。画像生成そのものはこの文書の作成者ではなく、
オーナーが Gemini に貼り付けて行う。
**方針**: 過去記事(バーナム効果・氷はなぜ水に浮くのか 等)と同様、**文字入り版のみ**を用意する。

---

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | ✅ 既存の `profile/icon.png`(500×500・正方形)をそのまま流用。作り直さない |
| 記事カバー | 🔲 プロンプト作成済み・Gemini での生成待ち(`covers/bandwagon-koka.png` として保存予定) |
| 解説イラスト1(行列に人が次々と加わっていく様子) | 🔲 プロンプト作成済み・生成待ち(`illustrations/bandwagon-01.png`) |
| 解説イラスト2(バンドワゴン効果・スノッブ効果・アンダードッグ効果の3心理対比) | 🔲 プロンプト作成済み・生成待ち(`illustrations/bandwagon-02.png`) |

すべて未生成。生成後、下記「生成後のチェックリスト」に沿ってサイズ・内容をコードと目視で検証し、
Opus QA(`note-qa`)にかけること。

---

## 共通スタイル指定(毎回のプロンプト冒頭に付けると絵柄が揃います)

```
Flat, warm, friendly children's educational illustration style (like a Japanese picture book for
elementary schoolers). Simple flat shapes, soft rounded corners, no photorealism, no realistic
human faces. Clean vector-like line art with a warm brown outline (#483628). Color palette strictly
limited to these six tones only: cream background (#FBF3E4), terracotta orange (#E08454, shadow
#BF673C), deep teal (#3A6960, light teal #92B5AB), and dark brown outline/text (#483628). Do not
introduce any other colors. Cheerful and gentle mood, appropriate for children. All people are drawn
as simple, abstract, flat silhouette or icon-style figures (a rounded head shape + simple body shape),
with NO realistic facial features, NO specific skin tone rendering, NO clothing details that would
suggest a specific real culture, ethnicity, or real individual — these are generic, universal,
picture-book-style human icons, interchangeable and simple like pictogram figures.
```

---

## 1. 記事カバー(`covers/bandwagon-koka.png`, 1280×670)

本文の核となるフック(行列ができているお店を見ると、中身を知らなくても「並んでいる人が多いなら良い
ものだろう」と思って自分もつい列に加わってしまう。この心の動きに「バンドワゴン効果」という名前が
ついている)を絵にする。タイトルは確定済みなので、そのまま画像内に焼き込む。

**注意(事実の取り扱い)**: 本文にある具体的な数値・固有名詞(19世紀・1950年・ハーヴェイ・
ライベンシュタイン等)はカバーには不要。カバーは「行列に並びたくなる」という身近な光景を印象的に
見せることを優先し、新しい事実を描き込まない。店は特定の実在ブランド・読み取れる看板文字を持たない
**汎用的な店構え**(ドアと窓だけの簡単な建物)にとどめる。

```
A wide horizontal illustration (aspect ratio approximately 16:8.4, matching a 1280x670 pixel canvas),
flat warm children's book style.

In the main foreground (right two-thirds of the image, below the title area), draw a simple, generic
friendly storefront (a small flat building shape with a door and one window, no readable text, no
logo, no brand name) with a line of simple flat silhouette people standing single-file, waiting,
facing the store — at least 6 to 7 identical simple person-icon figures in the line, all drawn at the
SAME size and in the SAME simple style (only their position in line differs). Add one or two more
simple person-icon figures shown walking IN from the right edge of the image toward the back of the
line, with a couple of small motion-lines behind their feet to show they are just now joining. Above
one of these newly-joining figures, add a small simple thought-bubble containing a tiny "!" mark (no
readable sentence, just the symbol) to suggest "oh, so many people — I want to join too."

In a small, clearly SECONDARY area of the image (for example the lower-left corner, noticeably smaller
and less prominent than the main queue scene), add ONE additional simple person-icon figure who is
walking AWAY from the line, in the opposite direction, with a small arrow beside them pointing away
from the queue — a small, quiet visual hint that not everyone reacts to a crowd the same way. Keep
this figure and its arrow small and subordinate; the queue in front of the store must remain the
single main visual focus of the illustration.

[共通スタイル指定を貼り付け]

Include a title at the top of the image in bold, clearly legible Japanese text:
「行列に並びたくなるのはなぜ? 「バンドワゴン効果」には、正反対の心理にも名前がついている」.
This title is 44 characters — moderately long, similar in length to a typical multi-line headline for
this series. Lay it out across 4 LINES with a font size large enough to read comfortably on a
1280x670px image but small enough to avoid crowding or overlapping the illustration below. Use these
exact natural phrase breaks (4 lines, longest line 14 characters):
line 1: 「行列に並びたくなるのはなぜ?」(14文字)
line 2: 「「バンドワゴン効果」には、」(13文字)
line 3: 「正反対の心理にも」(8文字)
line 4: 「名前がついている」(8文字)
If 4 lines still feel crowded given the font size, 5 lines with similarly natural phrase breaks is
also acceptable — do not force it onto 1–3 lines, as the font would become too large or the text
would overflow or touch the illustration below. CRITICAL: leave a clear, generous empty margin
between the very top edge of the image and the top of line 1's characters (at least 8% of the image
height) — no part of any character may touch or be cropped by the top edge. The title text must be
crisp, correctly formed Japanese characters (not garbled), in the dark brown color (#483628),
positioned in the upper area with calm, uncluttered space behind it so it does not overlap the queue
illustration below. Reserve roughly the top 40–45% of the image height for the title block and the
remaining lower portion for the storefront-and-queue illustration, so the two do not overlap.
```

**生成後の確認ポイント**:
- タイトルが4〜5行に収まり、文字が窮屈になっていないか(1〜3行に詰め込まれて文字が巨大化していないか)。
- タイトル1行目の文字上端が画像の一番上で切れていないか(拡大して確認)。
- タイトルの文言が確定タイトル「行列に並びたくなるのはなぜ? 「バンドワゴン効果」には、正反対の心理にも名前がついている」と一字一句違わず一致しているか。
- 行列に並ぶ人物が6〜7人以上、同じ大きさ・同じ簡易シルエットスタイルで描かれているか(一部だけ極端に大きい/小さいと違和感が出る)。
- 行列に新しく加わろうとしている人物がいて、「これから加わる」動きが見て取れるか。
- 左下などの副次的な位置にいる「列から離れていく人物」が、あくまで小さく控えめな扱いで、行列そのものより目立っていないか。
- 店の外観に実在ブランドを想起させる看板・ロゴ・読める文字が紛れ込んでいないか。
- 本文にない具体的な数字・固有名詞(年号・人名等)が画像内に書き込まれていないか。

---

## 2. 解説イラスト1: 行列に人が次々と加わっていく様子(`illustrations/bandwagon-01.png`)

本文該当箇所(L34、「なぜ『みんなと同じ』を選びたくなるのか」節末)の要旨: 「みんなが選んでいる
なら、きっと良いものだろう」という判断(社会的証明)と、「みんなと違う選択をして浮いてしまいたく
ない」という気持ちが重なると、「多くの人が選んでいるもの」がますます選ばれやすくなっていく。行列は
それ自体が新しい行列参加者を呼び込む、という自己強化的な流れを図解する。

**重要(本文にない事実を追加しない)**: 描いてよいのは「行列に並ぶ人の数がだんだん増えていく」という
流れそのものだけ。具体的な人数の統計・時間経過の数値・特定の店名/商品名などは一切描き込まない。

```
A single wide illustration, flat warm children's book style, showing the SAME queue scene at three
horizontal stages from left to right within one continuous image (like a simple flow, connected by a
single large arrow along the bottom running from left to right, labeled nowhere with numbers — just a
plain arrow shape), to show a queue growing over time.

STAGE 1 (left third of the image): a short line of exactly 3 simple flat person-icon silhouettes
standing together, all the SAME size and SAME simple style.

STAGE 2 (middle third of the image): a longer line of exactly 6 simple flat person-icon silhouettes —
the SAME simple style and SAME size as Stage 1's people (do not make them bigger or smaller) — with 1
or 2 of them drawn slightly separated from the line with small motion-lines behind their feet, walking
toward the back of the line, to show people actively joining.

STAGE 3 (right third of the image): a long line of exactly 10 simple flat person-icon silhouettes,
again the SAME size and SAME simple style as the previous two stages, with 2 more figures shown
walking in from outside the line toward the back with motion-lines, still joining. Above this longest
line, add a small simple thought-bubble (attached to one of the newly-arriving figures) containing a
small icon combination of an eye shape and a "!" mark (no readable sentence — just these two simple
symbols) to suggest "look how many people are already here!"

Draw a single large, simple arrow shape along the bottom of the whole image, pointing from left
(Stage 1) to right (Stage 3), to make the growth direction unmistakable. Use the terracotta orange
color (#E08454) for the arrow.

At the top of the whole image, include a short Japanese caption in bold: "並んでいる人が多いほど、新しく並ぶ人も増えていく".
Do not add any other numbers, statistics, dates, or store/brand names anywhere in the image — the
only quantities in this illustration are the person-icon counts described above (3, then 6, then 10),
and no numeral text should be written on the image itself (the growing count should be shown purely by
drawing more or fewer simple person-icon figures, not by writing digits).

[共通スタイル指定を貼り付け]

All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read for
children, in the dark brown color (#483628). Leave a generous margin (at least 8% of the image
height/width) around all four edges so nothing touches the border.
```

**生成後の確認ポイント**:
- 3つの段階(3人→6人→10人)が左から右へ並んでおり、人数が明確に増えていくのが一目で分かるか。
- 各段階の人物シルエットが、すべて同じ大きさ・同じ簡易スタイルで描かれているか(段階によって人物の大きさが変わっていないか)。
- 各段階に「新しく列に加わろうとしている人物」が描かれ、動きの線(モーションライン)で「加わりつつある」ことが伝わるか。
- 下部の矢印が左から右へ、3段階を貫いて成長の方向をはっきり示しているか。
- 画像内に本文にない具体的な数字(統計・日付等)や店名・商品名が書き込まれていないか。
- キャプション「並んでいる人が多いほど、新しく並ぶ人も増えていく」の文字が崩れていないか、上端で切れていないか。

---

## 3. 解説イラスト2: バンドワゴン効果・スノッブ効果・アンダードッグ効果の対比(`illustrations/bandwagon-02.png`)

本文該当箇所(L58、記事末尾の📎マーカー)の要旨:
- **バンドワゴン効果**〈みんなに合わせる〉: 多くの人が支持しているものを見ると、自分もそれを支持したくなる。
- **スノッブ効果**〈みんなと違うものを選ぶ〉: みんなが持っているものだからこそ、ほしくなくなる。人と違う、めずらしいものがほしくなる。
- **アンダードッグ効果**〈劣勢を応援する〉: 劣勢だと報じられている側を、思わず応援したくなる(判官びいき)。

**重要(取り違え厳禁・本文にない事実を追加しない)**:
- 3つのパネルは必ず「①バンドワゴン効果(左)→②スノッブ効果(中央)→③アンダードッグ効果(右)」の
  順で並べ、各パネルの見出しラベルと図解内容が一致していることを、プロンプト内で明示的に固定する
  (Gemini が生成後、ラベルと絵が入れ替わっていないか目視で必ず再確認すること)。
- 3パネルとも「多数派グループ」を描く場合は、**必ず同じ人数(8人)・同じ大きさ・同じ簡易シルエット
  スタイル**で統一する(パネルによって多数派グループの人数や大きさが変わると、同じ「多数派」だと
  伝わらなくなるため)。人物1体1体の大きさも、多数派グループ・少数派グループ・注目人物のどれであっても
  全て同一サイズにする(大きさの違いで「多い/少ない」を表現せず、必ず「人数(個数)の違い」だけで表現する)。
- 本文にない具体的な人数統計・年代・実在の選挙結果などは描き込まない。

```
A single illustration, flat warm children's book style, divided into THREE clearly separated
side-by-side panels of EQUAL size, separated by two simple vertical divider lines. Leave a generous
margin (at least 8% of the image height/width) around all four edges of the entire image so nothing
touches the border. In every panel, the "highlighted individual" figure (described below) must be
drawn in the SAME terracotta orange fill color (#E08454) in all three panels, so the viewer recognizes
it as "the same undecided person" facing three different situations. All groups of people in all
panels must use simple, identical, same-sized person-icon silhouettes (only the OUTLINE-only figures
represent "the crowd," in dark brown outline with light teal #92B5AB fill) — do not vary the size of
any individual person-icon anywhere in the image; only the COUNT of people should differ between
groups.

PANEL 1 (LEFT, labeled at the top in bold Japanese "バンドワゴン効果" with a smaller subtitle below it
"(みんなに合わせる)"): Draw a large group of exactly 8 identical person-icon silhouettes standing
close together (the "majority group"), on the right side of this panel. On the left side of this
panel, draw the ONE highlighted orange individual, with a solid terracotta-orange arrow pointing FROM
the individual INTO/TOWARD the group of 8, showing the individual walking toward and joining the
majority. Add a small checkmark icon (✓-like simple shape, dark brown) near the individual to
symbolize "choosing the same as everyone."

PANEL 2 (MIDDLE, labeled at the top in bold Japanese "スノッブ効果" with a smaller subtitle below it
"(みんなと違うものを選ぶ)"): Draw the SAME large group of exactly 8 identical person-icon
silhouettes (same size, same style, same count as Panel 1's majority group) on the LEFT side of this
panel. On the right side of this panel, draw the ONE highlighted orange individual standing apart, next
to a single small distinctive star-shaped icon (deep teal #3A6960) representing "a different, unique
choice" — NOT another person, just one small star shape. Draw a solid deep-teal arrow pointing FROM the
individual AWAY from the group of 8 and TOWARD the star shape, showing the individual deliberately
moving away from the majority toward something different.

PANEL 3 (RIGHT, labeled at the top in bold Japanese "アンダードッグ効果" with a smaller subtitle below
it "(劣勢を応援する)"): Draw the SAME large group of exactly 8 identical person-icon silhouettes (same
size, same style, same count as in Panels 1 and 2) positioned in the upper area of this panel, AND
separately, a small group of exactly 2 identical person-icon silhouettes (same individual size/style as
all other person-icons, just fewer of them) positioned in the lower area of this panel, clearly and
visibly a much smaller group than the 8-person group above it. Draw the ONE highlighted orange
individual near the small group of 2, with both of the highlighted individual's arms raised in a
simple cheering gesture, and a small heart-shaped icon (terracotta orange) above the individual's head.
Draw a dark-brown dashed arrow from the individual pointing toward the small group of 2 (NOT toward the
large group of 8), to clearly show the individual is cheering for and supporting the smaller, weaker
group despite the larger group being bigger.

At the top of the whole image (above all three panels, with clear space below the very top edge — not
touching it), include a short Japanese caption: "同じ「みんなの選択」を見ても、心の動きは人それぞれ".

[共通スタイル指定を貼り付け]

All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read for
children, in the dark brown color (#483628). Double-check before finalizing: Panel 1's label must say
"バンドワゴン効果" and show the individual joining the big group; Panel 2's label must say "スノッブ効果"
and show the individual moving away from the big group toward a unique star icon; Panel 3's label must
say "アンダードッグ効果" and show the individual cheering for the small group of 2, not the big group of 8.
```

**生成後の確認ポイント**:
- 左からバンドワゴン効果・スノッブ効果・アンダードッグ効果の順で並んでいるか。
- **各パネルのラベル文字と図解内容が一致しているか(取り違えが最も起きやすい箇所のため必ず確認)**:
  - 「バンドワゴン効果」パネル → 注目人物が多数派グループ(8人)に向かって矢印で合流しているか。
  - 「スノッブ効果」パネル → 注目人物が多数派グループ(8人)から離れ、星マークのほうへ矢印が向いているか(人ではなく星マーク=「めずらしいもの」であることを確認)。
  - 「アンダードッグ効果」パネル → 注目人物が、大きい方の8人グループではなく、小さい方の2人グループに向かって応援している(ハートマーク・矢印が2人グループを指している)か。
- 3パネルすべてで、多数派グループの人数が8人・同じ大きさ・同じスタイルで統一されているか(パネルごとに人数や大きさがぶれていないか数える)。
- アンダードッグ効果パネルの「少数派グループ(2人)」が、多数派グループ(8人)より明らかに少ない・小さく見えるか(人数の違いだけで表現されており、個々の人物の大きさ自体は変わっていないか)。
- 注目人物(オレンジ色)が3パネルとも同じ色・同じ大きさで描かれ、「同じ1人の心が3通りに動く」ことが視覚的に伝わるか。
- 本文にない具体的な人数統計・年代・実在の選挙結果などの新しい事実が描き込まれていないか。

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
  ```bash
  python3 -c "from PIL import Image;print(Image.open('covers/bandwagon-koka.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/bandwagon-01.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/bandwagon-02.png').size)"
  ```
- [ ] 日本語テキスト(タイトル・ラベル・キャプションとも)が崩れていないか拡大して確認
- [ ] カバーのタイトルが確定タイトルと一字一句一致しているか確認(「行列に並びたくなるのはなぜ? 「バンドワゴン効果」には、正反対の心理にも名前がついている」・44字)
- [ ] カバーのタイトルが4〜5行に収まり、窮屈になっていないか確認
- [ ] イラスト1: 3段階(3人→6人→10人)の人数増加が明確に見えるか、人物の大きさが段階間で統一されているか確認
- [ ] イラスト2: 3パネルの順序(バンドワゴン→スノッブ→アンダードッグ)とラベル・図解内容の対応が正しいか確認(最重要)
- [ ] イラスト2: 3パネルとも多数派グループが8人・同一サイズで統一されているか確認
- [ ] イラスト2: アンダードッグ効果パネルの少数派グループが2人で、多数派8人より明確に少ないか確認
- [ ] 全画像共通: 登場人物が実写風の顔・特定の人種/文化を想起させる描写になっていないか(抽象的なシルエット/アイコンのままか)確認
- [ ] 全画像共通: 配色がブランドパレット6色(クリーム・テラコッタ・テラコッタ陰影・ディープティール・淡ティール・ダークブラウン)の範囲内に収まっているか確認
- [ ] 本文にない具体的な数値・固有名詞(実在の店名・ブランド名・統計数値・年代等)が画像内に紛れ込んでいないか確認
- [ ] プロフィールアイコンは既存の `profile/icon.png` をそのまま使い、作り直していないか確認

保存先の目安: `covers/bandwagon-koka.png` /
`illustrations/bandwagon-01.png`(行列に人が次々と加わっていく様子)/
`illustrations/bandwagon-02.png`(バンドワゴン効果・スノッブ効果・アンダードッグ効果の3心理対比)

生成後、本文中の📎マーカーに対応するファイルパスが一致していることを確認してください(マーカー自体を
実画像への記法に差し替えるのは `note-formatter` の担当です):
- `illustrations/bandwagon-01.png` … 本文L34「なぜ『みんなと同じ』を選びたくなるのか」節末の📎マーカーと一致
- `illustrations/bandwagon-02.png` … 本文L58(記事末尾)の📎マーカーと一致
