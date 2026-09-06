# Gemini用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「氷はなぜ水に浮くのか」用イラスト一式
**確定タイトル**: 「氷はなぜ水に浮くのか? 「固体は液体より重い」が通じない、水だけの例外」(35字)
**用途**: Gemini(画像生成)にそのまま貼り付けて使うプロンプト
**方針**: 過去記事(バーナム効果・猫は液体か・コリオリの力・モスキート音・フェルミのパラドックス)と同様、
**文字入り版のみ**を用意する。

---

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | ✅ 既存の `profile/icon.png`(500×500・正方形、確認済み)をそのまま流用。作り直さない |
| 記事カバー | 🔲 プロンプト作成済み・Gemini での生成待ち(`covers/kori-ukabu.png` として保存予定) |
| 解説イラスト1(液体の水 vs 氷、分子の並び方の対比) | 🔲 プロンプト作成済み・生成待ち(`illustrations/kori-ukabu-01.png`) |
| 解説イラスト2(湖の断面図: 表面の氷・4℃の水・魚) | 🔲 プロンプト作成済み・生成待ち(`illustrations/kori-ukabu-02.png`) |

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

本文の核となるフック(たいていの物質は固体になると液体より重くなるのに、水だけは逆で、固体の氷が
液体の水に浮く。冬の湖の生き物はこの性質のおかげで命拾いしているかもしれない)を絵にする。
タイトルは確定済みなので、そのまま画像内に焼き込む。

**注意(事実の取り扱い)**: このイラストは分子や科学現象を扱うが、密度の具体的な数値(0.92g/cm³・
1.00g/cm³など)や「9%」「4℃」といった数値をカバーに書き込む必要はない(数値は解説イラスト側で扱う)。
カバーは「コップの中で氷が水に浮いている、見慣れた光景」を印象的に見せることを優先する。

```
A wide horizontal illustration (aspect ratio approximately 16:8.4), flat warm children's book style.
In the main foreground, a simple, friendly glass cup filled with clear water, with two or three
simple ice cubes clearly floating at the TOP of the water inside the cup (not sinking, not in the
middle — unambiguously floating at the surface). Add a few small simple bubble or sparkle details on
the ice cubes to suggest coldness (NOT realistic ice texture, just a simple flat iconic ice-cube shape
with soft rounded corners). Behind or beside the cup, add a small simple thought-bubble or curious
character silhouette (no realistic face, just a simple round head shape with a small "?" mark) looking
at the floating ice with a curious expression, to evoke "why does it float?" — keep this element small
and secondary to the cup, which is the main visual focus.
Optionally, in the soft background, include a small, simple, calm frozen lake or pond scene (a flat
blue-teal shape with a thin ice layer on top) as a subtle secondary motif hinting at the "lake in
winter" theme from the article — keep it small, soft-focus, and clearly in the background, not
competing with the main cup-and-ice-cube illustration.
[共通スタイル指定を貼り付け]
Include a title at the top of the image in bold, clearly legible Japanese text: 「氷はなぜ水に浮くのか? 「固体は液体より重い」が通じない、水だけの例外」.
This title is 35 characters — moderate length, shorter than a very long headline but still too long for
a single line. Lay it out across 3 LINES with a font size large enough to read comfortably but small
enough to avoid crowding or overlapping the illustration below. Suggested natural phrase breaks (3
lines):
line 1: 「氷はなぜ水に浮くのか?」
line 2: 「「固体は液体より重い」が通じない、」
line 3: 「水だけの例外」
If 3 lines still feel crowded given the font size, 4 lines with similarly natural phrase breaks is also
acceptable — do not force it onto 1–2 lines, as the font would become too large or the text would
overflow. The title text must be crisp, correctly formed Japanese characters (not garbled), in the dark
brown color (#483628), positioned in the upper area with calm, uncluttered space behind it so it does
not overlap the cup-and-ice-cube illustration below.
```

**生成後の確認ポイント**: タイトルが3〜4行に収まり、文字が窮屈になっていないか。氷が明確に「水面に浮いている」ように見えるか(水中に沈んでいたり、氷が水の外に置かれているだけに見えると本文の趣旨とずれるため要確認)。背景の凍った湖のモチーフが小さく副次的な扱いになっており、コップの氷が主役として視認できるか確認。

---

## 2. 解説イラスト1: 液体の水 と 氷、分子の並び方の対比

本文該当箇所(「氷の中身は、すきまだらけ」節)の要旨: 液体の水の中では、分子同士が水素結合で
くっついたり離れたりしながら絶えず動き回り、くっつく相手も向きも決まっていないので、わりと自由に
すきまを埋め合うように詰まっている。ところが氷になると、分子が自由に動けなくなり、水素結合が
四方八方に決まった向きで固定される。この結びつき方には向きの決まりがあって分子同士がまっすぐ
くっつけないため、すきまの多い規則正しい形(上から見ると六角形に近い形)に組み上がる。すきまが
多い分、同じ数の分子でも全体の体積が大きくなり、その分軽くなる。

**重要(本文にない事実を追加しない)**:
- 画像内に含めてよい数字は密度の**1.00 g/cm³(水)と0.92 g/cm³(氷)のみ**。本文にある2つの
  数値以外(分子数・温度・パーセンテージなど)を新たに書き加えない。
- 液体側は「分子が自由に、ランダムな向きでくっつき、すきまなく詰まっている」、氷側は「分子が
  水素結合で規則正しく(六角形の網目状に)並び、すきまが多い」という本文の説明から絵の内容が
  逸脱しないこと。氷の結合の線は全て同じ向き・同じ角度で規則正しく描き(ランダムに描かない)、
  液体側の結合の線はバラバラな向き・不規則な感じで描く(規則正しく描かない)ことで、両者の違いが
  一目で分かるようにする。

```
A single illustration, flat warm children's book style, split into two clearly separated side-by-side
panels of EQUAL size, with a simple vertical divider line down the middle.

LEFT panel, labeled at the top in bold Japanese "液体の水": many small, simple round "water molecule"
blobs (identical simple circle shapes, no realistic chemistry diagrams, no atoms/letters like H or O)
packed CLOSELY together with almost NO visible empty space between them — the blobs should look tightly
and randomly packed, touching each other on many sides, like a jar tightly filled with marbles. Connect
neighboring blobs with short, thin, slightly wavy or squiggly connecting lines pointing in many
DIFFERENT, RANDOM directions and angles (no repeating pattern), to suggest the molecules are loosely
and randomly bonding and constantly moving — a few small motion-squiggle or arrow marks near some blobs
can reinforce "always moving, no fixed arrangement." Below this panel, add a small label tag in
Japanese: "1.00 g/cm³".

RIGHT panel, labeled at the top in bold Japanese "氷": the same style of small round "molecule" blobs,
but arranged in a clearly REGULAR, REPEATING honeycomb/hexagonal net pattern — every blob connects to
its neighbors with straight lines at the SAME fixed angles everywhere in the pattern (unlike the random
left panel), forming a repeating grid of open hexagon shapes. Inside each hexagon opening, leave
visible empty cream-background space to make the "many gaps" clearly visible — the overall density of
blobs per unit area in this panel should look noticeably LOWER (more spread out, more open space) than
in the left panel, even though the blobs themselves are the same size. Below this panel, add a small
label tag in Japanese: "0.92 g/cm³".

At the very top of the whole image (above both panels), include a short Japanese caption:
"液体の水はすきまなく、氷はすきまだらけ".
Do not add any other numbers, temperatures, or percentages anywhere in the image — only the two density
labels "1.00 g/cm³" and "0.92 g/cm³" are allowed.
[共通スタイル指定を貼り付け]
All Japanese text and numerals must be crisp, correctly formed characters and digits (not garbled),
large and easy to read for children, in the dark brown color (#483628).
```

**生成後の確認ポイント**: 左右どちらが「液体の水」でどちらが「氷」か、ラベルを見なくても一目で分かるか(すきまの量の違いが視覚的に明確か)。氷側の結合線が全て同じ向き・規則正しいパターンになっているか(ランダムに見えると本文の「決まった向きで固定される」という説明と矛盾する)。液体側の結合線が不規則でバラバラな向きになっているか(規則正しく見えると本文の「向きが決まっていない」という説明と矛盾する)。氷側のすきま(空白部分)が液体側より明らかに多く見えるか。画像内の数字が「1.00 g/cm³」「0.92 g/cm³」の2つ以外に増えていないか確認。

---

## 3. 解説イラスト2: 湖の断面図(表面の氷・4℃の水・魚)

本文該当箇所(「もし氷が沈んでしまったら」節)の要旨: 冬、湖の水面から冷やされていく。もし氷が
水より重ければ湖は底から凍ってしまうが、実際には密度がいちばん高いのは4℃の水で、冷えて4℃に
なった水は沈んで底にたまる。さらに冷えた水や氷は軽いので水面付近にとどまり、結果として湖は表面
からしか凍らない。水面に張った氷がふたのような役割をして、その下の水を守る。底のほうの水は4℃
前後のまま保たれやすく、魚や水中の生き物はその中で冬を過ごせる、と考えられている。

**重要(本文にない事実を追加しない)**:
- 描いてよい要素は「表面の氷の層」「その下にたまる4℃の水」「その中を泳ぐ魚」の3つのみ。
  画像内に含めてよい数字は**「4℃」のみ**。深さごとの水温の詳細な数値・目盛り・温度計のような
  グラフ的表現は追加しない(小学生が見て分かる絵的な図にする)。
- 湖の底に泥や岩・水草などの一般的な自然物を軽く添えるのは構わないが、それらに新たな事実主張
  (水温・生態など)を持たせない。あくまで背景の添え物とする。

```
A single illustration, flat warm children's book style: a simple cross-section (side view, like a
"cut open" cake) of a winter lake. At the very top, a thin, flat, clearly icy-blue layer represents the
frozen surface (a simple ice-cap shape with a soft rounded top, sitting like a lid on top of the water)
— optionally show a little snow or a cold winter sky with a small cloud above the ice to set the
season, but keep this background detail small and secondary.
Below the ice layer, fill the rest of the cross-section with a calm teal-blue body of water. Add ONE
clear label inside this water area, in Japanese, reading "4℃" with a small tag or bubble around it, to
show that the water below the ice is calm and around 4℃ — do not add any other numbers or a
temperature scale/gradient/gauge anywhere in the image.
Inside this water area, draw 2 to 3 simple, cheerful, cartoon fish swimming calmly (simple rounded fish
shapes, no realistic anatomy, friendly simple dot eyes), positioned in the lower-middle area of the
water, to show they are living comfortably below the ice.
Near the bottom of the cross-section, a simple lake-bed line with a few soft rounded pebble or plant
shapes is fine as a small decorative background detail (no added facts, no labels on these).
At the top of the whole image, include a short Japanese caption: "氷が『ふた』になって、下の水と魚を守っている".
[共通スタイル指定を貼り付け]
All Japanese text and numerals must be crisp, correctly formed characters and digits (not garbled),
large and easy to read for children, in the dark brown color (#483628).
```

**生成後の確認ポイント**: 断面図として「上から氷 → その下に水 → 魚が泳いでいる」という重なり順になっているか(氷が水の中に埋もれていたり、魚が氷の上にいるように見えると本文と矛盾する)。「4℃」以外の数値・目盛り・グラフ的な温度表現が紛れ込んでいないか確認。魚の描写が本文にない生態情報(種類・数の主張など)を新たに示唆していないか確認(装飾的なイラストとして違和感のない範囲に留める)。

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
  ```bash
  python3 -c "from PIL import Image;print(Image.open('covers/kori-ukabu.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/kori-ukabu-01.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/kori-ukabu-02.png').size)"
  ```
- [ ] 日本語テキスト(タイトル・ラベル・キャプションとも)が崩れていないか拡大して確認
- [ ] カバーのタイトルが3〜4行に収まり、窮屈になっていないか確認(35字なのでバーナム効果回の50字よりは短いが、1〜2行に詰め込まれていないか要確認)
- [ ] カバー: 氷が水面にはっきり「浮いている」ように見えるか(沈んでいる・水の外にあるように見えないか)確認
- [ ] イラスト1: 左(液体の水)と右(氷)の見分けが、ラベルなしでも一目で分かるか(すきまの量の差が明確か)確認
- [ ] イラスト1: 氷側の結合線が規則正しい同じ向き、液体側の結合線がランダムな向きになっているか確認(本文の水素結合の説明と矛盾していないか)
- [ ] イラスト1: 画像内の数字が「1.00 g/cm³」「0.92 g/cm³」の2つ以外に増えていないか確認
- [ ] イラスト2: 断面図の重なり順が「氷(表面)→ 4℃の水 → 魚」になっているか確認(氷が水中に沈んで見えたり魚が氷の上に見えたりしていないか)
- [ ] イラスト2: 「4℃」以外の数値・温度スケール・グラフ的表現が追加されていないか確認
- [ ] プロフィールアイコンは既存の `profile/icon.png` をそのまま使い、作り直していないか確認

保存先の目安: `covers/kori-ukabu.png` /
`illustrations/kori-ukabu-01.png`(液体の水と氷、分子の並び方の対比)/
`illustrations/kori-ukabu-02.png`(湖の断面図: 表面の氷・4℃の水・魚)

生成後、本文中の📎マーカーに対応するファイルパスが一致していることを確認してください(マーカー自体を
実画像への記法に差し替えるのは `note-formatter` の担当です):
- `illustrations/kori-ukabu-01.png` … 本文「氷の中身は、すきまだらけ」節末の📎マーカーと一致
- `illustrations/kori-ukabu-02.png` … 本文「もし氷が沈んでしまったら」節末の📎マーカーと一致
