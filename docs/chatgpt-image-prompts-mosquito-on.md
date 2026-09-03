# ChatGPT用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「モスキート音」用イラスト一式
**確定タイトル**: 「おとなには聞こえない音がある? 「モスキート音」は、若者を追い払う発明にもなった」(40字)
**用途**: ChatGPT(画像生成)にそのまま貼り付けて使うプロンプト
**方針**: 過去2記事と同様、**文字入り版のみ**を用意する。

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | 既存の `profile/icon.png`(500×500)をそのまま流用。作り直さない |
| 記事カバー | 未生成。下記プロンプトで生成待ち |
| 解説イラスト1(可聴範囲とモスキート音の位置) | 未生成。下記プロンプトで生成待ち |
| 解説イラスト2(蝸牛断面図・入り口=高音/奥=低音) | 未生成。下記プロンプトで生成待ち |
| 解説イラスト3(公園の装置と若者/大人の対比) | 未生成。下記プロンプトで生成待ち |

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

本文の核となるフック(同じ音なのに、子どもには聞こえて大人には聞こえない)を絵にする。
タイトルは確定済みなので、そのまま画像内に焼き込む。

```
A wide horizontal illustration (aspect ratio approximately 16:8.4), flat warm children's book style.
On the left side, a cheerful simple child character (no realistic face, simple friendly cartoon
style) with one hand near their ear, surrounded by a few small warm-orange wavy sound-wave arcs near
their ear, showing they clearly hear a high-pitched sound. On the right side, a simple adult
character (e.g. a parent figure) with a puzzled expression, hand cupped behind their ear, but with
NO sound-wave arcs near their ear at all — instead a small "?" symbol near their head, showing they
hear nothing. Between the two characters, place a small simple smartphone or speaker icon at the
center, with sound waves radiating only toward the child's side, not the adult's side, making clear
the same source produces a sound only the child can hear. Optionally include one tiny, cute, non-
scary stylized flying mosquito silhouette near the sound waves as a small decorative nod to the
sound's nickname, clearly small and secondary, not the main subject.
[共通スタイル指定を貼り付け]
Include a title at the top of the image in bold, clearly legible Japanese text: 「おとなには聞こえない音がある? 「モスキート音」は、若者を追い払う発明にもなった」. This title is long (40 characters), so lay it out across 3 lines, with balanced line breaks, sized small enough to comfortably fit without crowding. The title text must be crisp, correctly formed Japanese characters (not garbled), in the dark brown color (#483628), positioned in the upper area with calm uncluttered space behind it so it does not overlap the character illustrations below.
```

**生成後の確認ポイント**: タイトルが3行に収まり文字が窮屈になっていないか。子ども側にだけ音波が描かれ、大人側には音波が無い(または「?」のみ)という左右非対称が明確か。

---

## 2. 解説イラスト1: 人の可聴範囲とモスキート音の位置関係

本文該当箇所(L16〜26)の要旨: 人が聞き取れる音の高さは、だいたい20ヘルツ〜20,000ヘルツ(20キロヘルツ)。
モスキート音は、その範囲の中でもかなり上の方、17,000ヘルツ(17キロヘルツ)前後の高い音。
**注意**: モスキート音は可聴範囲の「外」ではなく、範囲の中の「かなり上のほう」に位置する(本文に忠実に)。

```
A single simple illustration, flat warm children's book style: a horizontal rounded bar/ruler shape
(like a thermometer or ruler lying on its side), representing the range of sounds a person can hear,
running from left to right. The LEFT end of the bar is clearly labeled in Japanese "ひくい音
20ヘルツ" and the RIGHT end of the bar is clearly labeled in Japanese "たかい音 20,000ヘルツ". The
entire bar (from left end to right end) should be filled with the light teal color (#92B5AB),
representing the whole range a person can hear.
CRITICAL for placement: mark ONE clear point/star icon ON the bar, positioned close to the RIGHT
(high) end but with a small visible gap before the very right edge — roughly in the last one-fifth
of the bar's length, clearly still inside the teal bar, not outside it and not at the exact right
tip. Draw a short leader line from this point up to a small label box above the bar reading in
Japanese "モスキート音 17,000ヘルツくらい". Do not place this marker at the far left, at the middle,
or outside/beyond the right end of the bar — it must read as "high, near the top of the range, but
still within the range".
[共通スタイル指定を貼り付け]
All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read
for children, in the dark brown color (#483628).
```

**生成後の確認ポイント**: 帯全体が「聞こえる範囲」であり、モスキート音の印が帯の**外ではなく内側**にあるか。印が右端(高い側)に寄っているが、右端そのものではなく、範囲内であることが視覚的にわかるか。左端=低い・右端=高い、の対応がラベルと矛盾していないか。

---

## 3. 解説イラスト2: 蝸牛の断面図(入り口=高音担当/奥=低音担当)

本文該当箇所(L28〜44)の要旨: 蝸牛はかたつむりのように巻いた形。
**入り口に近い場所**の有毛細胞は**高い音**を、**奥の方(先端に近い場所)**の有毛細胞は**低い音**を担当する。

**重要(過去の事故を踏まえた注意)**: 本文にある「入り口=高音」「奥(先端)=低音」以外の情報(ピアノ鍵盤との厳密な対応、周波数の数値、担当範囲の細かい割合など)を絵の中に追加しない。ラベルの文言は本文の言葉に忠実にする。

```
A single illustration, flat warm children's book style: a simplified cross-section of a cochlea,
drawn as a coiled spiral tube (like a cross-section of a snail shell, or a cinnamon roll cut in
half), showing 2 to 3 visible coiled loops winding inward from a wider outer opening to a tightly
wound center.
CRITICAL for labeling — there are exactly two labeled points, and they must NOT be swapped:
1) The OUTER, WIDEST opening of the spiral (the starting point of the coil, where a small tube
   leading in from the ear would connect) must be labeled with a leader line to a text box reading
   in Japanese "入り口:高い音を担当". Draw a tiny simple sound-wave icon or a small arrow entering
   from outside into this opening, to show this is where sound first enters the cochlea from the ear.
2) The INNERMOST, TIGHTLY WOUND CENTER of the spiral (the tip/end of the coil, farthest from the
   opening) must be labeled with a leader line to a text box reading in Japanese
   "奥(先たん):低い音を担当".
Do not label the middle of the spiral. Do not reverse which end is "入り口" and which is "奥" — the
wide outer opening is always "入り口/高い音", the tightly wound inner tip is always "奥/低い音". Keep
the diagram simple and cute, not medically graphic (no blood, no realistic tissue texture) — think
picture-book style cutaway diagram.
[共通スタイル指定を貼り付け]
All Japanese text must be crisp, correctly formed characters (not garbled), large and easy to read
for children, in the dark brown color (#483628).
```

**生成後の確認ポイント**: 渦の**外側の開口部(入り口)**に「高い音」、**内側の巻き終わり(奥/先端)**に「低い音」のラベルが付いているか(逆になっていたら失敗、作り直す)。ラベルの文言が本文と一致しているか(本文にない周波数数値やピアノとの厳密対応などを勝手に追加していないか)。

---

## 4. 解説イラスト3: 公園の装置と、反応する若者/反応しない大人の対比

本文該当箇所(L58〜74)の要旨: イギリス発の「モスキート」装置。若い人にだけ聞こえる高い音を出し、夜遅く
たむろする若者を音で追い払う目的で作られた。日本でも足立区が公園に試験導入した例がある。
**注意**: 実在の暴力的・威圧的な装置に見せない。怖がらせる表現は避ける(CLAUDE.mdのトーン方針)。

```
A single illustration, flat warm children's book style: a simple park scene at dusk (soft warm
lighting, not scary or dark). A small speaker device is mounted on a park pole or wall, with a few
small orange wavy sound-wave arcs radiating from it toward one side of the image only.
On the side the sound waves reach: 2–3 simple teenager characters (slightly taller/older-looking
than young children, but still simple friendly cartoon style, no realistic faces) shown reacting —
hands near their ears, mildly surprised or bothered expression, perhaps starting to walk away.
On the other side, clearly outside the reach of the sound-wave arcs (no wavy lines drawn near them
at all): a simple adult character standing calmly nearby, relaxed expression, going about their
business (e.g. reading a paper or walking a small dog), completely unaffected, with a small "?" or
"..." near them to show they notice nothing.
Keep the mood gentle and a little funny/curious, not threatening — this is a playful illustration of
an interesting invention, not an unsettling scene. No realistic weapons, no aggressive imagery.
[共通スタイル指定を貼り付け]
Include short Japanese captions rendered clearly and legibly: near the teenagers "若者には聞こえる",
near the adult "おとなには聞こえない". Text must be crisp, correctly formed Japanese characters (not
garbled), large and easy to read for children, in the dark brown color (#483628).
```

**生成後の確認ポイント**: 音波の線が若者側にだけ描かれ、大人側には描かれていない(左右非対称)か。威圧的・怖い印象になっていないか(トーン方針に反しないか)。

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
  ```bash
  python3 -c "from PIL import Image;print(Image.open('covers/mosquito-on.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/mosquito-01-hearing-range.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/mosquito-02-cochlea.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/mosquito-03-device.png').size)"
  ```
- [ ] 日本語テキスト(タイトル・ラベルとも)が崩れていないか拡大して確認
- [ ] カバーのタイトルが3行に収まり、窮屈になっていないか確認
- [ ] イラスト1: 帯全体が「聞こえる範囲」を表し、モスキート音の印が帯の**内側**(右寄り、右端そのものではない)にあるか確認。左=低い/右=高いの対応が正しいか
- [ ] イラスト2: 渦の**外側(入り口)**=高い音、**内側(奥/先端)**=低い音、というラベルが逆になっていないか確認(過去に別記事で矢印取り違えの事故があったため特に厳重に確認する)
- [ ] イラスト2: ラベルの文言が本文(L40「蝸牛の入り口に近い場所にある有毛細胞は高い音を、奥の方(先端に近い場所)にある有毛細胞は低い音を担当しています」)と一致しているか。本文にない数値・対応関係を勝手に追加していないか
- [ ] イラスト3: 音波が若者側にだけ描かれ、大人側には無いという対比が明確か。怖い・威圧的な印象になっていないか
- [ ] プロフィールアイコンは既存の `profile/icon.png` をそのまま使い、作り直していないか確認

保存先の目安: `covers/mosquito-on.png` /
`illustrations/mosquito-01-hearing-range.png`(可聴範囲とモスキート音)/
`illustrations/mosquito-02-cochlea.png`(蝸牛断面図)/
`illustrations/mosquito-03-device.png`(公園の装置と若者/大人の対比)

生成後、本文中の📎マーカーを画像貼り付け手順に反映してください(マーカー自体は `note-formatter` が
実画像への差し替えを行う担当のため、ここでは生成物のファイルパスが本文の📎マーカーの指定と
一致していることのみ確認する):
- `illustrations/mosquito-01-hearing-range.png` … 本文L26のマーカーと一致
- `illustrations/mosquito-02-cochlea.png` … 本文L44のマーカーと一致
- `illustrations/mosquito-03-device.png` … 本文L74のマーカーと一致
