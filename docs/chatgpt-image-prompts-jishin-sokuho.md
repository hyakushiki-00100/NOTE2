# ChatGPT用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「緊急地震速報のひみつ」用イラスト一式
**確定タイトル**: 「地震は『弱い揺れ』から始まる? 緊急地震速報も、揺れより先に届くことがある理由」(39字。
※記事本文の実際のタイトル文字列は内側の鍵カッコが単一の「」であり、上記は引用のため外側に『』相当の
二重引用を付けて紹介しているだけです。画像に焼き込む文字列は下記「1. 記事カバー」に記載した
`地震は「弱い揺れ」から始まる? 緊急地震速報も、揺れより先に届くことがある理由` を使ってください)
**用途**: ChatGPT(画像生成)にそのまま貼り付けて使うプロンプト
**方針**: 過去記事と同様、**文字入り版のみ**を用意する。

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | 既存の `profile/icon.png`(500×500)をそのまま流用。**作り直さない** |
| 記事カバー | 未生成。下記プロンプトで生成する(`covers/jishin-sokuho.png`) |
| 解説イラスト1(P波・S波が震源から同時に広がる図) | 未生成(`illustrations/jishin-pwave-swave-douji.png`) |
| 解説イラスト2(地震計の検知→解析→警報配信と、警報がS波より先に届く様子の対比図) | 未生成(`illustrations/jishin-sokuho-shikumi.png`) |

---

## 共通スタイル指定(毎回のプロンプト冒頭に付けると絵柄が揃います)

```
Flat, warm, friendly children's educational illustration style (like a Japanese picture book for
elementary schoolers). Simple flat shapes, soft rounded corners, no photorealism, no realistic
human faces. Clean vector-like line art with a warm brown outline (#483628). Color palette limited
to: cream background (#FBF3E4), terracotta orange (#E08454, shadow #BF673C), deep teal
(#3A6960, light teal #92B5AB). Cheerful and gentle, calm and reassuring mood — this is a science
diagram about earthquakes and an early-warning system, NOT a disaster or danger scene. No cracked
ground, no collapsing or damaged buildings, no rubble, no scared or crying facial expressions, no
red emergency-siren imagery. Keep the tone matter-of-fact and educational, like explaining how a
clock works.
```

**このテーマ特有の色の割り当て(3枚すべてで統一して使ってください)**:
- **P波(先に届く・弱い揺れ)= ディープティール系(#3A6960 / 淡色 #92B5AB)**
- **S波(あとから届く・強い揺れ)= テラコッタオレンジ系(#E08454 / 陰影 #BF673C)**
- 解説イラスト2の「警報(電波)」は、P波の検知から生まれる情報なのでティール系を使い、S波(オレンジ)と
  はっきり区別できるようにする。

---

## 1. 記事カバー

本文の核となるフック(地震の揺れには「弱いのが先・強いのが後」という順番があり、警報はその順番を
利用して揺れそのものより先に届くことがある)を絵にする。タイトルは確定済みなので、そのまま画像内に
焼き込む。

**タイトルの文字数(コードで確認済み)**: 全39字。
```
python3 -c "t='地震は「弱い揺れ」から始まる? 緊急地震速報も、揺れより先に届くことがある理由';print(len(t))"
# => 39
```
3行に分けると次の通り自然な区切りになる(疑問符・読点の直後で改行、単語の途中では改行しない):
- 1行目(15字): `地震は「弱い揺れ」から始まる?`
- 2行目(8字): `緊急地震速報も、`
- 3行目(15字): `揺れより先に届くことがある理由`

```
A wide horizontal illustration (aspect ratio approximately 16:8.4), flat warm children's book style,
calm educational science-diagram mood (not a disaster scene).

Center-left: a simple cross-section view of the ground, like a gentle rounded hill or a slice of
earth with a flat top (where a small simple house sits calmly, no damage, no cracks). Below the
ground's surface, mark ONE small point as the epicenter (震源) with a small star or dot icon.
From this point, draw two clearly different concentric circles/ripples expanding outward and
upward toward the surface, like ripples in a pond seen from the side, both sharing the exact same
center point (the epicenter), to show they started at the same moment:
1) An OUTER, LARGER ripple ring, drawn in deep teal (#3A6960), representing P波 — this ring must
   be the one that has already spread FARTHER from the epicenter, because P波 travels faster and
   arrives first.
2) An INNER, SMALLER ripple ring, drawn in terracotta orange (#E08454), representing S波 — this
   ring stays closer to the epicenter, because S波 travels slower and has not spread as far yet.
Do not swap these two: the larger/farther-spreading ring is always teal/P波, and the smaller/
closer-to-center ring is always orange/S波.

On the right side of the image, draw a simple smartphone or small alert-device icon with a small
bell/notification symbol on its screen, and a few short teal radio-wave arcs traveling from the
ground area toward the smartphone, arriving at the phone while the orange (S波) ripple is still
small/close to the epicenter — visually showing the alert reaches the phone before the strong
shaking (S波) has spread far. Keep this device icon calm and small, not alarming (a simple bell
outline, not a red flashing siren).

[共通スタイル指定を貼り付け]

Include a title at the top of the image in bold, clearly legible Japanese text, broken into exactly
3 lines with these natural phrase breaks (do not break mid-word, do not merge or reorder the lines):
Line 1: 地震は「弱い揺れ」から始まる?
Line 2: 緊急地震速報も、
Line 3: 揺れより先に届くことがある理由
This title is 39 characters total across 3 lines (15 / 8 / 15 characters). Size the font small
enough that all 3 lines comfortably fit within the image width without touching the edges or
overlapping the illustration below. CRITICAL: leave a generous empty margin (at least 8% of the
image height) between the very top edge of the image and the top of line 1's characters — no part
of any character (including small marks like "゛" or "」") may be cropped or touch the top border.
Position the whole 3-line title block starting noticeably below the top edge, with calm,
uncluttered plain background directly behind it so it stays crisp and readable. The title text must
be crisp, correctly formed Japanese characters (not garbled), in the dark brown color (#483628).
```

**生成後の確認ポイント**:
- タイトルが3行(15/8/15字)に収まり、上端で文字が切れていないか(必ず拡大して確認)。
- 震源から広がる2つの輪のうち、**外側(半径が大きい方)がティール=P波**、**内側(半径が小さい方)が
  オレンジ=S波**になっているか(逆になっていたら失敗。P波が先に遠くまで届いている、という本文の
  事実と矛盾する)。
- スマートフォン(警報)に届いている波がティール(P波由来の警報)であり、オレンジのS波の輪はまだ
  震源近くにとどまっているか(警報が先、強い揺れがまだ届いていない、という対比)。
- 家や地面が壊れている・ひび割れている・怖がっている人物などの表現が無いか(防災テーマにつき
  恐怖を煽らないトーンを維持)。

---

## 2. 解説イラスト1: 震源からP波とS波が同時に丸く広がる図

本文該当箇所(「地震の揺れには『先発』と『後発』がある」節、L12〜24)の要旨: 地震が起きると、震源から
性質の違う2種類の波(P波・S波)が**同時に**発生する。P波は弱い揺れ(初期微動)で先に届き、S波は強い
揺れ(主要動)で少し遅れて届く。

**重要(本文にない数値を追加しない)**: この図に数値ラベルを入れる場合、使ってよいのは本文L30にある
「P波はおおよそ秒速7キロメートル前後、S波はおおよそ秒速4キロメートル前後」という目安の2つの数値のみ。
それ以外の数値(震源からの距離、到達までの秒数など)を新たに書き加えない。
**位置関係は一義的に指定する**: P波の輪は必ずS波の輪より外側(半径が大きい・先に遠くまで届いている)
にする。逆にしない。

```
A single simple illustration, flat warm children's book style, top-down bird's-eye view (like
looking down at a pond after dropping a stone into it). At the exact center of the image, draw one
small star/burst icon representing the epicenter (震源), with a small label below it in Japanese:
"震源(ここで岩盤がずれる)".

From this single center point, draw exactly two concentric perfect circles (rings), both centered
on the very same point, like two ripples spreading from the same stone-drop:
1) An OUTER ring (LARGER radius, farther from the center) drawn as a deep teal (#3A6960) circle
   outline with a few small motion-arrows pointing outward along it, representing P波. Attach a
   leader line from this outer ring to a label box in Japanese reading:
   "P波(先に届く・弱い揺れ) 秒速7kmくらい".
2) An INNER ring (SMALLER radius, closer to the center, clearly and visibly smaller than the P波
   ring) drawn as a terracotta orange (#E08454) circle outline with a few small motion-arrows
   pointing outward along it, representing S波. Attach a leader line from this inner ring to a
   label box in Japanese reading:
   "S波(あとから届く・強い揺れ) 秒速4kmくらい".

CRITICAL for placement: the teal P波 ring's radius must be clearly and visibly LARGER than the
orange S波 ring's radius (roughly 1.5–1.8 times larger), so it is immediately obvious the teal ring
has traveled farther from the same center point in the same amount of time. Do NOT make the two
rings the same size, and do NOT make the orange ring larger than the teal ring. Both rings must
share exactly the same center point (the epicenter star icon), to show they started at the same
moment — do not offset the two circles from each other.

Add one small shared caption near the top of the image, in Japanese: "同じ場所から、同時に生まれる
2つの波". Do not add any other numeric labels besides the two speed labels given above (no
distances in kilometers, no time in seconds, no station counts).

[共通スタイル指定を貼り付け]
All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read
for children, in the dark brown color (#483628).
```

**生成後の確認ポイント**: 2つの輪が同じ中心点(震源)から出ているか(中心がずれていないか)。**外側=
ティール=P波の輪の方が、内側=オレンジ=S波の輪よりも明確に大きい(遠くまで届いている)**か(逆に
なっていたら失敗、作り直す)。ラベルの数値が本文と同じ「P波:秒速7kmくらい」「S波:秒速4kmくらい」
のみで、本文に無い数値(距離・秒数など)が追加されていないか。

---

## 3. 解説イラスト2: 地震計の検知→解析→警報配信と、警報がS波より先に届く様子の対比図

本文該当箇所(「この速度差を利用したのが緊急地震速報」節、L38〜48)の要旨: 震源に近い地震計がまず
P波を捉える → そのデータから震源やコンピューターが素早く解析する → 強いS波(主要動)が届く前に警報を
送り出す。情報が電波で伝わる速さは、地面を伝わるS波の速さよりずっと速いので、揺れが来る前に知らせる
ことができる。

**重要(本文にない数値・要素を追加しない)**: この図には「震源近くの地震計がP波を検知」「データ解析」
「警報配信」という3ステップの流れと、「警報(電波)がS波(地面を伝う揺れ)より先に遠くの地域に届く」
という対比の**2点のみ**を描く。具体的な秒数、観測点(地震計)の数、震度の数値などは本文に無いので
追加しない。壊れる建物や怖がる表情など、恐怖を煽る表現も避ける(防災テーマのトーン方針)。

```
A single wide illustration, flat warm children's book style, calm educational diagram mood (not a
disaster scene), divided into two clearly connected parts: a PROCESS FLOW across the top, and a
MAP-LIKE COMPARISON SCENE across the bottom.

TOP PART — process flow, left to right, 3 simple icons connected by 2 rightward arrows:
1) A small simple seismometer icon (a round device with a needle/wave-drawing pen on a paper roll),
   placed near a small ground-cross-section bump labeled in Japanese "震源に近い地震計". A small
   teal wavy line icon (P波) touches this seismometer first. Caption below: "①P波をキャッチ".
2) A small simple computer/gear icon with a tiny wave-graph on its screen. Caption below:
   "②コンピューターがすぐに計算".
3) A small simple radio-tower or broadcast icon with a small speech-bubble/bell shape reading
   "警報!" in Japanese inside or beside it (calm bell outline, not a red flashing siren). Caption
   below: "③警報を送る".
Use small rightward arrows between icon 1→2 and 2→3 to show the order clearly. Do not reverse this
order.

BOTTOM PART — comparison scene, a simple horizontal calm landscape strip: on the LEFT, mark the
epicenter with a small star icon (震源) at ground level, with NO houses drawn damaged or cracked
anywhere in the scene. On the RIGHT side of the same strip, draw one small simple town — a few
plain, undamaged house icons and one simple smartphone/alert-device icon with a small bell symbol.

From the epicenter, draw TWO separate paths traveling rightward toward the town, that must look
visually DIFFERENT in both color and shape, and one must be clearly ahead of the other:
(a) A fast, straight, deep-teal (#3A6960) dashed line or small lightning-bolt/radio-wave icon,
    already reaching the smartphone at the town, with a small label "警報(電波)". This path must be
    drawn as having ALREADY ARRIVED at the town (touching the smartphone icon).
(b) A slower, wavy, terracotta-orange (#E08454) squiggly line representing S波 traveling along the
    ground, drawn as NOT YET having reached the town — its wavy line should visibly stop short,
    somewhere in the middle of the strip between the epicenter and the town, clearly behind/short of
    where the teal path has reached. Label this squiggly line "S波(地面を伝わる強い揺れ)".

CRITICAL for placement: the teal "警報" path must reach all the way to the town/smartphone icon,
while the orange "S波" squiggle must stop clearly before reaching the town, visibly shorter than the
teal path. Do not make the two paths the same length. Do not make the orange S波 reach the town
first or at the same time as the teal 警報.

Add one shared caption above the bottom part, in Japanese: "警報(電波)は、S波(地面を伝わる揺れ)
より先に届く". Do not add any specific numbers of seconds, distances, or station counts anywhere in
the image — only the Japanese captions given above.

[共通スタイル指定を貼り付け]
All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read
for children, in the dark brown color (#483628). Keep the whole scene calm, bright daytime or soft
dusk lighting, with no cracked ground, no collapsed or tilted buildings, no rubble, and no scared or
distressed facial expressions anywhere.
```

**生成後の確認ポイント**: 上段の3ステップが「①P波をキャッチ→②解析→③警報を送る」の順番になっているか
(順番が入れ替わっていないか)。下段で、**ティールの「警報(電波)」の線が町(スマホ)まで届いていて、
オレンジの「S波」の線がまだ町の手前で止まっている**か(警報の方が先に届く、という対比が逆になって
いたら失敗)。具体的な秒数・観測点の数・震度などの本文に無い数値が描き加えられていないか。建物の破損・
ひび割れ・怖がる表情・赤い点滅サイレンなど、恐怖を煽る表現が無いか(このテーマは防災上のトーン配慮が
特に必要)。

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
  ```bash
  python3 -c "from PIL import Image;print(Image.open('covers/jishin-sokuho.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/jishin-pwave-swave-douji.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/jishin-sokuho-shikumi.png').size)"
  ```
- [ ] 日本語テキスト(タイトル・ラベルとも)が崩れていないか拡大して確認
- [ ] カバー: タイトルが3行(15/8/15字、計39字)に収まり、上端で文字が切れていないか確認
- [ ] カバー: 震源から広がる2つの輪で、外側(大きい方)=ティール=P波、内側(小さい方)=オレンジ=S波に
      なっているか確認(逆なら失敗)
- [ ] カバー: 建物・地面が壊れている表現、怖がる人物、赤い点滅サイレン等が無いか確認
- [ ] イラスト1: 2つの輪が同じ中心点(震源)から出ており、P波(ティール・外側)がS波(オレンジ・内側)
      より明確に大きい(遠くまで届いている)か確認(過去記事で図の位置関係の取り違えが繰り返し
      指摘された経緯があるため特に厳重に確認する)
- [ ] イラスト1: ラベルの数値が本文にある「P波:秒速7kmくらい」「S波:秒速4kmくらい」のみで、
      本文に無い距離・秒数などの数値が追加されていないか確認
- [ ] イラスト2: 上段の3ステップが「①P波をキャッチ→②解析→③警報を送る」の順で描かれているか確認
- [ ] イラスト2: 下段で、ティールの「警報(電波)」が町まで届き、オレンジの「S波」がまだ手前で止まって
      いる(警報が先に届く)対比になっているか確認(逆なら失敗)
- [ ] イラスト2: 本文に無い秒数・観測点数・震度等の数値が追加されていないか確認
- [ ] イラスト2: 建物の破損、怖がる表情、赤い点滅サイレンなど恐怖を煽る表現が無いか確認
- [ ] プロフィールアイコンは既存の `profile/icon.png` をそのまま使い、作り直していないか確認

保存先の目安: `covers/jishin-sokuho.png` /
`illustrations/jishin-pwave-swave-douji.png`(震源からP波・S波が同時に広がる図)/
`illustrations/jishin-sokuho-shikumi.png`(地震計の検知→解析→警報配信と、警報がS波より先に届く対比図)

生成後、本文中の📎マーカーを画像貼り付け手順に反映してください(マーカー自体は `note-formatter` が
実画像への差し替えを行う担当のため、ここでは生成物のファイルパスが本文の📎マーカーの指定と
一致していることのみ確認する):
- `illustrations/jishin-pwave-swave-douji.png` … 本文L24のマーカーと一致
- `illustrations/jishin-sokuho-shikumi.png` … 本文L50のマーカーと一致

## 注記(このドキュメントの位置づけ)

このドキュメントは ChatGPT(画像生成)に貼り付けるプロンプトの作成のみを行ったものであり、
実際の画像ファイル(`covers/jishin-sokuho.png` 等)はまだ生成・保存されていない。
プロンプトをChatGPTに貼り付けて画像を生成したのち、上記チェックリストに沿って検証し、
サイズ調整(PIL等での1280×670・横1200pxへのリサイズ)を行うこと。
