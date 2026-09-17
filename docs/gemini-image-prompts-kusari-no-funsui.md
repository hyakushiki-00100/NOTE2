# Gemini用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「鎖の噴水現象」用イラスト一式
**確定タイトル**: 「カップから鎖を落とすと、なぜか一瞬「噴水」になる? 「鎖の噴水現象」を見つけたのは、物理学者ではなくユーチューバーだった」(60字・コードで確認済み)
**用途**: Gemini(画像生成)にそのまま貼り付けて使うプロンプト。実際の生成・保存・ピクセル計測はこの後オーナーが行う。
**方針**: 過去記事(誕生日のパラドックス・月の錯視 等)と同様、**文字入り版のみ**を用意する。

---

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | ✅ 既存の `profile/icon.png` をそのまま流用。作り直さない |
| 記事カバー | ❌ 2回のOpus精査で不合格(旧タイトル文字列・YouTube風アイコン・縁付近の描画崩れ・カップ中身が
  飲み物に見える)に加え、3回目はGemini側で連続生成が不安定になり画像を確保できず。プロンプトを
  必須条件だけに絞った簡略版に書き直し済み。再生成待ち(`covers/kusari-no-funsui.png`) |
| 解説イラスト1(カップから鎖が噴水のように盛り上がる図) | ❌ 保存済みだった版は「カップ中身が空」の
  古い版と判明(要再確認)。新たに送られた再生成版は中身のビーズ山盛りは改善されたが、(a) ビーズの隙間から
  カップ内側がティール色で覗き液体のように見える、(b) 鎖が二重ループで交差し歪んで見える、の2点が新たに
  見つかった。プロンプトを修正済み。再生成待ち(`illustrations/kusari-no-funsui-01.png`) |
| 解説イラスト2(山積みのリンクが押し返す力の図解) | ❌ Opus精査で不合格(矢印修正の消し跡が残っていた、持ち上がる部分が
  粒感の無い滑らかな線でイラスト1との統一性が無かった)。プロンプトを修正済み。再生成待ち
  (`illustrations/kusari-no-funsui-02.png`) |

生成後、下記「生成後のチェックリスト」に沿って検証し、Opus QA(`note-qa`)にかけること。

---

## 共通スタイル指定(毎回のプロンプト冒頭に付けると絵柄が揃います)

```
Flat, warm, friendly children's educational illustration style (like a Japanese picture book for
elementary schoolers). Simple flat shapes, soft rounded corners, no photorealism, no realistic
human faces. Clean vector-like line art with a warm brown outline (#483628). Color palette limited
to: cream background (#FBF3E4), terracotta orange (#E08454, shadow #BF673C), deep teal
(#3A6960, light teal #92B5AB). Cheerful and gentle mood, appropriate for children.
The ball chain (the toy/lamp-pull style chain made of small round beads) must be drawn as a cute,
flat, cartoon row of simple connected circles (like a string of round candy beads) — NOT a
photorealistic or metallic-looking chain. No chrome/silver shading, no photo texture on the beads.
```

---

## タイトル文字数の確認(コードで検証)

```bash
python3 -c "
t = 'カップから鎖を落とすと、なぜか一瞬「噴水」になる? 「鎖の噴水現象」を見つけたのは、物理学者ではなくユーチューバーだった'
print(len(t))
"
# => 60
```

60字は、過去記事の「誕生日のパラドックス」回(58字・5〜6行)とほぼ同じ長さで、「氷はなぜ水に浮くのか」回
(35字・3行)よりも明確に長い。**行数に余裕を持たせ、6行を基本とする(窮屈なら7行まで許容)。**
1〜4行に無理に詰め込むと文字が小さくなりすぎるか、はみ出す恐れがあるため避ける。

想定の行分割(6行・自然な区切り):
- line 1: 「カップから鎖を落とすと、」
- line 2: 「なぜか一瞬「噴水」になる?」
- line 3: 「「鎖の噴水現象」を」
- line 4: 「見つけたのは、」
- line 5: 「物理学者ではなく」
- line 6: 「ユーチューバーだった」

---

## 1. 記事カバー

**改訂履歴**:
- 1回目のOpus精査で、(a) タイトルの「見つけたのは」が発見の先取権を断定しすぎており本文の
  「広めたのは」に統一することになった(本文修正済み)ため、カバーのタイトル文字列も更新が必要、
  (b) 「再生ボタン」風アイコンが角丸長方形+中央の白三角というYouTubeの再生ボタンのシルエットに
  近すぎる、との指摘を受けた。タイトルを更新し、アイコン形状も単純な円に変更した(この修正は合格)。
- 2回目のOpus精査で新たに2点の不合格が見つかった: (c) カップの縁付近に、本流から枝分かれした
  行き止まりの鎖や、丸ビーズではなく潰れたカプセル状の塊など、描画が崩れた部分があった。
  (d) カップの中身が、ビーズの質感のない一様なオレンジの塗りつぶしになっており、コーヒーなどの
  飲み物にしか見えず、本文6行目の「このくさりをカップに山盛りに入れて」という設定と食い違っていた。
  今回はカップの中身を明確に「積み重なったビーズの山」として描くよう指示を追加し、鎖は枝分かれの
  無い一本の連続した線であることを明記した。

本文冒頭の核となるフック(カップに山盛りにした鎖を垂らすと、カップの縁のところで一瞬「噴水」のように
盛り上がる。この現象を広めたのは物理学者ではなく、イギリスの科学系ユーチューバーだった)を絵にする。
タイトルは確定済みなので、そのまま画像内に焼き込む。

**注意(事実の取り扱い)**:
- カバーには「鎖が縁の上で盛り上がる」という現象そのものと、「広めたのはユーチューバー」という
  事実のヒントだけを描く。押し返す力の仕組み(解説イラスト2の内容)はカバーに描き込まない。
- 「ユーチューバーが広めた」ことを示すヒントは、**実在の人物・チャンネル名・実在プラットフォームの
  ロゴを想起させない、一般的な記号**に留める。角丸長方形(ピル型)の枠に白い三角形、という組み合わせは
  実在の動画プラットフォームのロゴに酷似するため使わない。代わりに**単純な円形**の中に三角形を置く形にし、
  色は本文パレット内(ディープティール)にする。実在の動画共有サービスのロゴの配色(赤・白など)や
  形(角丸長方形)を模倣しない。
- 具体的な高さ・角度・力の大きさの数値は本文に無いため、画像内に一切書き込まない(数値ラベル無し)。

**(3回目・簡略版プロンプト)**: 前回までの版は指示が細かすぎて生成が不安定になっていた可能性があるため、
絶対に外せない条件だけに絞った短い版に書き直した。削った指示: 「噴水」の見た目の詳細な奥行き描写、
アイコンの説明の重複、数値を書くなという念押しの重複など。残した条件: ①ビーズの山盛り(飲み物に見えない)、
②鎖は一本(枝分かれ禁止)、③縁より明確に高いアーチ、④右下へ落ちていく、⑤丸いアイコン(YouTube風禁止)、
⑥タイトル文言・6行の行分け。

```
A wide horizontal illustration (16:8.4 ratio), flat warm children's picture-book style.

A simple cream-colored cup sits in the lower-center. Its inside is filled right up to the rim with a
pile of many small round terracotta-orange (#E08454) beads — it must read as "a cup full of small
beads," never a smooth solid fill and never liquid.

One single continuous chain of the same small round beads rises from this pile and goes over the rim.
It is ONE unbroken strand only — no side-branches, no separate stray bead shapes anywhere near the rim
or handle. Just above the rim it forms one smooth rounded arch that rises clearly higher than the rim
itself (like a small fountain bump), then curves back down and trails off toward the lower-right edge
of the image (not resting on the table — it keeps falling out of frame).

In one small upper corner, away from the cup and title, add one small plain teal (#3A6960) circle with
a small triangle inside it — a generic "something is being watched/played" hint. Keep it a plain circle
only (never a rounded rectangle or pill shape, to avoid resembling any real video app logo).

[共通スタイル指定を貼り付け]

Title at the top, bold dark brown (#483628) Japanese text, laid out on exactly 6 lines:
line 1: 「カップから鎖を落とすと、」
line 2: 「なぜか一瞬「噴水」になる?」
line 3: 「「鎖の噴水現象」を」
line 4: 「広めたのは、」
line 5: 「物理学者ではなく」
line 6: 「ユーチューバーだった」
Leave at least 6% empty margin above line 1. Keep the title area calm and uncluttered, not overlapping
the cup illustration below.
```

**生成後の確認ポイント**: タイトルが「広めたのは」の文言で6〜7行に収まり、文字が窮屈になっていないか
(1〜4行に詰め込まれて文字が小さすぎたり、はみ出したりしていないか)。2箇所ある鉤括弧「「噴水」」
「「鎖の噴水現象」」がそれぞれ正しく対になって描画されているか、「?」が正しく描かれているか拡大して確認。
鎖の盛り上がりが**カップの縁より明確に高い位置**に描かれているか(縁と同じ高さ・縁より低い位置で終わって
いたら「噴水」に見えないため失敗)。チェーンが写実的な金属チェーンの質感になっておらず、可愛いフラットな
粒の連なりになっているか確認。**アイコンの外形が単純な円になっており、角丸長方形(ピル型)になっていないか
特に厳重に確認**する(1回目の生成でYouTubeの再生ボタンに酷似していると指摘された経緯があるため)。実在の
チャンネル名・人物の顔が描き込まれていないか確認。押し返す力の矢印など解説イラスト2の内容がカバーに
紛れ込んでいないか確認。**カップの中身が、粒の見える「ビーズの山」になっているか(一様な塗りつぶしで
コーヒー等の飲み物に見えていたら失敗)確認する**。**鎖が枝分かれ無く一本につながっており、縁や取っ手の
近くに、丸ビーズではない潰れた塊・行き止まりの突起が無いか拡大して確認する**(2回目の生成でこの種の
描画崩れが見つかった経緯があるため)。落ちていく鎖が、カップと同じ高さの床の上で終わっておらず、
画面右下の端に向かって消えていく(まだ落下が続いていることを示唆する)構図になっているか確認する。

---

## 2. 解説イラスト1: カップから鎖が噴水のように盛り上がる図(本文L12の📎マーカー該当)

本文該当箇所(「くさりがカップの縁のところで、一瞬ふわっと持ち上がるんです。まるで縁のすぐ上に、目に
見えない噴水があるみたいに。」)の要旨: カップに入った鎖が縁のところで一瞬持ち上がり、噴水のように
盛り上がって見える。その後、鎖は外側へ落ちていく。

**重要(本文にない事実を追加しない)**:
- この段階ではまだ「なぜ持ち上がるのか」という仕組み(押し返す力)は説明されていない(それは
  解説イラスト2で扱う)。このイラストには矢印・力の図解・数値ラベルを入れず、**現象そのものの見た目**
  だけを描く。
- 高さ・角度の具体的な数値は本文に無いため書き込まない。

**改訂履歴**:
- 1回目の生成でカップの中身が空(何も入っていない)に見え、本文6行目の「カップに山盛りに
  入れて」という設定と食い違っていた。ビーズが山盛りになっている様子を明示的に描くよう指示を追加した。
- 2回目の生成で、(a) ビーズの隙間からカップ内側の縁がディープティール色で覗き、「ティール色の
  液体にビーズが浮いている」ように見えた、(b) 鎖が自分自身と交差する二重ループになっており、
  交差点でビーズが不自然に重なって歪んで見えた。今回は①カップ内側の見える面もクリーム系の色にする
  ②アーチは交差の無い単純な1回だけの弧にする、という指示を追加した。

```
A single illustration, flat warm children's book style, on a cream background (#FBF3E4).
Composition (front-to-back): in the FOREGROUND (lower-center of the image), a simple, friendly
cream-colored cup (plain round cup or mug, no brand marks) sits on a simple flat tabletop surface.
The visible inner rim/wall of the cup (any part of the cup's inside surface that might peek between or
behind the beads) must be the SAME cream/tan color family as the cup's outside (#FBF3E4 or a slightly
darker warm tan) — NEVER deep teal or any other color, so nothing behind the beads could be mistaken
for colored liquid. Fill the inside of the cup, right up to the rim, with a small mound of the same
small round terracotta-orange (#E08454) beads used in the chain — many individual bead circles piled
up together, clearly readable as "a cup filled with a pile of small beads," not empty, not a smooth
solid color, and with no other color visible peeking through the gaps between beads.

Rising from this pile of beads inside the cup and spilling over its rim, draw a single continuous,
cute, flat cartoon ball chain — a row of small connected round beads, terracotta orange (#E08454) with
a warm brown (#483628) outline, all beads the same small size as each other. This must be a single
unbroken strand with no side-branches or disconnected bead shapes anywhere near the rim, and the chain
must NOT cross over or loop back through itself anywhere (no self-intersections, no figure-eight or
double-loop shapes) — keep its path simple so no beads overlap each other at a crossing point.

Just above the rim of the cup, the chain must form ONE single clear, smooth, rounded ARCH shape (like a
small dome or fountain-plume, a simple single hump — not a double hump, not a loop) that rises
noticeably higher than the rim itself — make the height of this arch, from the rim up to the top of the
arch, roughly 2 to 3 times the diameter of a single bead, so it reads as a distinct "popping up" bump
rather than the chain merely resting flat on the rim.

From the top of this single arch, the chain then curves downward and outward on the far side of the
cup, and continues down and slightly further back in the scene (smaller and slightly higher up in the
frame, to suggest it is further away / already falling), trailing off toward the lower-back area of the
image — this represents "手前にカップ、盛り上がった弧、奥に落ちていく鎖" (foreground: cup, middle: the
raised arch, background: the falling chain continuing down and away). The path from pile → arch → falling
tail must be ONE smooth continuous curve with no crossings.

Do not draw any arrows, force diagrams, numbers, or angle marks in this image — it is a plain, charming
depiction of the moment the chain "fountains" above the rim, nothing more.
[共通スタイル指定を貼り付け]
If any text is included, it must be limited to a short caption below the illustration, in Japanese, in
the dark brown color (#483628): "カップの縁の上で、鎖がふわっと持ち上がる". Do not add any other text,
numbers, or labels.
```

**生成後の確認ポイント**: 鎖の盛り上がり(アーチ)が**カップの縁より明確に高い位置**にあるか(縁と同じ
高さや、縁より低い位置に見えたら「噴水」に見えないため失敗)。手前にカップ、盛り上がった弧、奥に落ちていく
鎖、という奥行きのある構図になっているか(全部が同じ平面上に並んでいて奥行きが感じられない場合は再構成を
検討)。矢印・力の図解・数値ラベルなど、まだ本文で説明していない仕組み(押し返す力)の要素が誤って
紛れ込んでいないか確認。チェーンの粒が写実的な金属質感になっておらず、子ども向けの可愛いフラットな丸に
なっているか確認。**カップの中身が「ビーズの山盛り」になっているか(空に見えたら失敗)確認する**
(1回目の生成でカップが空に見えた経緯があるため)。**ビーズの隙間からカップ内側がティール等ビーズ以外の
色で覗いていないか(液体のように見えたら失敗)確認する**。**アーチが二重ループ・自己交差になっておらず、
単純な1つの弧になっているか(交差点でビーズが不自然に重なっていたら失敗)確認する**(2回目の生成でこの
2点が見つかった経緯があるため)。

---

## 3. 解説イラスト2: 山積みのリンクが押し返す力の図解(本文L36の📎マーカー該当)

**改訂履歴**: 1回目の生成物は、(a) 矢印の向きが「リンク→山」に見える誤った向きだったため画像編集で
消去・再描画したが、消去跡がうっすら残っていた、(b) 持ち上げられているリンクが、粒感のない滑らかな
オレンジの線(チューブ状)として描かれており、解説イラスト1の「小さな丸いビーズが連なった鎖」という
統一デザインと矛盾し、山と同じ「くさり」であることが伝わらなかった、という2つの問題が見つかった。
今回はゼロから再生成し、矢印の向きと、くさりの見た目の統一(山も持ち上がる部分も、同じ丸いビーズが
つながった鎖であること)の両方を満たすようにする。

本文該当箇所(「カップの中のリンクは、山になって積み重なっています。そこから一粒が引っ張られると、その
リンクはまっすぐ上ではなく、カーブを描くように向きを変えながら持ち上がります。このとき、下にある山の
部分が邪魔になります。向きを変えようとするリンクが山に食い込まないよう、山のほうがリンクをぐいっと
押し返すんです。」)の要旨:

- カップの中でリンク(鎖の粒)は山になって積み重なっている。
- 山から一粒が引っ張られると、そのリンクはまっすぐ上ではなくカーブを描いて持ち上がる。
- カーブの途中でリンクが山に食い込みそうになる → **山のほうがリンクを押し返す。**
- (本文L38の例え、床に置いた棒の片方を持ち上げると、もう片方が床を押しつけて反発する、と矛盾しない
  向きにする: 押される側=リンク、押す側=山〈床に相当〉、力の向きは山からリンクへ、山から離れる方向。)

**重要(本文にない事実を追加しない)**:
- 押し返す力の**大きさ**の数値は本文に無いため書き込まない(矢印の長さで強さの数値を示唆しない。
  矢印は「向き」を示すためだけに使う)。
- 山とリンクの**相対的な大きさ**を明示する: 山(たくさんのリンクが積み重なったかたまり)は、動いている
  リンク1粒よりも十分に大きく見えるようにする。目安として、山全体の直径は、リンク1粒の直径の**6〜8倍
  程度**にする(山が「小さな粒がたくさん集まった、大きなかたまり」であることが一目で分かるように)。
- 引き上げられるリンクは**1つだけ**とし、他のリンクと違う色調(強調色)にして区別できるようにする。

**矢印の始点・終点(重要・向きを一意にする)**:
- 矢印の**始点**: 山の表面のうち、持ち上がりつつあるリンクが山に触れている(食い込みそうになっている)
  まさにその接触点。
- 矢印の**終点**: その接触点から、山の中心とは反対方向(山の外側・持ち上がっていくリンクの方向)へ、
  リンクの表面に向かって短く伸ばした先。
- つまり矢印は**「山の表面」→「持ち上がるリンク」の向き**(山からリンクを押し出す向き)で描き、
  逆向き(リンクから山へ向かう向き)には絶対に描かない。

```
A single illustration, flat warm children's book style, on a cream background (#FBF3E4). Show a
simple cross-section / cutaway side view of a cup (a plain rounded container outline in dark brown
#483628, open at the top, no need to draw the far wall — a simple U-shaped cup outline is enough).

Inside the cup, draw a large mound (a pyramid/triangular pile shape) made up of MANY small round beads
(deep teal #3A6960 with dark brown #483628 outlines), each bead touching its neighbors, packed closely
together to clearly read as "a big pile made of lots of small connected beads" — this is the SAME ball
chain material as illustration 1, just piled up instead of hanging in a loop. Make the overall mound's
width and height roughly 6 to 8 times the diameter of a single bead, so the mound is obviously much
larger than any one bead — this size difference is essential and must be clearly visible.

Starting from near the top surface of this mound, draw ONE continuous chain of the SAME kind of small
round beads (a row of touching circles, exactly like illustration 1's ball chain — NOT a smooth tube,
NOT a solid curved line without visible bead segments), colored in a clearly different accent color
(terracotta orange #E08454 with dark brown #483628 outlines, to visually distinguish it from the teal
mound) that is in the middle of being pulled up and out of the pile. Draw this chain of beads following
a curved path (like a hook or a backwards "J" shape) — NOT a straight vertical line — starting from
within the mound, curving up and outward, then continuing straight upward and out of the top of the
cup (implying the rest of the chain is pulling it up and away, off the top edge of the image). Every
part of this orange chain, from where it leaves the mound to where it exits the top of the image, must
show individual round bead segments, just like the teal beads in the mound and like the chain in
illustration 1 — at no point should it become a smooth featureless line or tube.

At the exact point where this orange chain first leaves the surface of the teal mound (the very first
orange bead, closest to the mound, at the "elbow" of the curve where it changes direction), draw ONE
short, bold, clearly directional arrow in dark brown (#483628): the arrow's TAIL (starting point) must
be placed exactly ON the surface of the teal mound at that contact point, and the arrow's HEAD
(pointing end) must point in the SAME direction the orange chain is heading immediately after that
point (away from the mound's center, along the chain's outward curve), ending just short of touching
the first orange bead — i.e., the arrow visually originates from the pile and pushes the chain along
its own departing direction, and must NOT point back toward the peak of the mound or in any direction
other than the chain's own outward path. Label this arrow with small Japanese text next to it: "押し返す力".

Add a small Japanese label near the mound pointing to it: "山(たくさんのリンクが積み重なったところ)".
Add a small Japanese label near the orange bead: "持ち上げられるリンク".
Do not write any numbers (no force values, no angles, no lengths) anywhere in this image — only the
Japanese text labels listed above are allowed.
[共通スタイル指定を貼り付け]
All Japanese text and labels must be crisp, correctly formed characters (not garbled), large and easy
to read for children, in the dark brown color (#483628). Leave a generous margin (at least 8% of the
image height/width) around all four edges so nothing touches the border.
```

**生成後の確認ポイント**:
- 矢印が**「山の表面」から「持ち上がるリンク」へ向かう向き**になっているか(逆向き・曖昧な向きに見えたら
  失敗、作り直す)。矢印の始点が山の表面上、終点がリンクの近くになっているか具体的に確認する。
- 山の大きさが、動いているリンク1粒よりも**明らかに大きい**(目安6〜8倍程度)か確認する(山と粒が同じ
  くらいの大きさに見えたら「山になって積み重なっている」ことが伝わらないため失敗)。
- 引き上げられるリンクの軌跡が、まっすぐ上ではなく**カーブを描いている**か確認する(本文「まっすぐ上では
  なく、カーブを描くように向きを変えながら持ち上がります」との整合)。
- この図の力の向き(山がリンクを押し返す=山が押す側、リンクが押される側)が、本文L38の「床に置いた棒の
  片方を持ち上げると、もう片方が床を押しつけて反発する」という例え(床=押す側、棒の端=押される側)と
  **矛盾していない**か確認する(押す側と押される側が入れ替わっていたら失敗)。
- 力の大きさを示す数値(矢印の長さに数値ラベルを付ける等)が書き込まれていないか確認する。
- 動いているリンクが他の粒と異なる色(強調色)になっており、1粒だけであることが分かるか確認する。
- チェーンの粒が写実的な金属質感になっておらず、子ども向けの可愛いフラットな丸になっているか確認する。
- **持ち上がっていく部分が、山と同じ「丸いビーズが連なった鎖」に見えるか確認する**(滑らかな線・チューブ状に
  なっていて粒感が無い場合は失敗。イラスト1の鎖と同じ見た目の統一性が必要)。
- 矢印の周辺(特に元の矢印があった位置)に、消し跡・薄い影のような残留物が無いか、拡大して確認する。

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
  ```bash
  python3 -c "from PIL import Image;print(Image.open('covers/kusari-no-funsui.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/kusari-no-funsui-01.png').size)"
  python3 -c "from PIL import Image;print(Image.open('illustrations/kusari-no-funsui-02.png').size)"
  ```
- [ ] 日本語テキスト(タイトル・ラベル・キャプションとも)が崩れていないか拡大して確認
- [ ] カバーのタイトルが6〜7行に収まり、窮屈になっていないか確認(60字と長めのタイトルのため特に注意。
      1〜4行に詰め込まれていないか)
- [ ] カバー: 2箇所の鉤括弧「「噴水」」「「鎖の噴水現象」」と「?」が正しく描画されているか確認
- [ ] カバー: 鎖の盛り上がりがカップの縁より明確に高い位置に描かれているか確認
- [ ] カバー: 「再生ボタン」風アイコンが実在の動画プラットフォームのロゴを想起させる配色・形になっていないか、
      実在の人物・チャンネル名が描き込まれていないか確認
- [ ] カバー: 押し返す力の矢印など、解説イラスト2の内容が紛れ込んでいないか確認
- [ ] イラスト1: 鎖の盛り上がり(アーチ)がカップの縁より明確に高い位置にあるか確認(縁と同じ高さ・
      それ以下なら失敗)
- [ ] イラスト1: 手前にカップ、盛り上がった弧、奥に落ちていく鎖、という奥行きのある構図になっているか確認
- [ ] イラスト1: 矢印・力の図解・数値ラベルが紛れ込んでいないか確認(現象の見た目のみを描く図であること)
- [ ] イラスト1: ビーズの隙間からティール等の色が覗いて液体のように見えていないか確認
- [ ] イラスト1: 鎖が二重ループ・自己交差になっておらず単純な1つの弧になっているか確認
- [ ] イラスト2: 矢印が「山の表面 → 持ち上がるリンク」の向きになっているか確認(逆向き・曖昧なら失敗)
- [ ] イラスト2: 山の大きさがリンク1粒よりも明らかに大きい(目安6〜8倍程度)か確認
- [ ] イラスト2: 引き上げられるリンクの軌跡がまっすぐでなくカーブを描いているか確認
- [ ] イラスト2: 力の向き(山が押す側・リンクが押される側)が、本文L38の棒と床の例え(床が押す側・棒の端が
      押される側)と矛盾していないか確認
- [ ] イラスト2: 力の大きさを示す数値が書き込まれていないか確認
- [ ] 全画像共通: ボールチェーンの粒が写実的な金属チェーンの質感になっておらず、子ども向けの可愛いフラットな
      丸の連なりになっているか確認
- [ ] 全画像共通: 使用色がクリーム(#FBF3E4)・テラコッタオレンジ(#E08454/影#BF673C)・ディープティール
      (#3A6960/淡色#92B5AB)・ダークブラウン(#483628)の4色パレットに収まっているか確認
- [ ] プロフィールアイコンは既存の `profile/icon.png` をそのまま使い、作り直していないか確認

保存先の目安: `covers/kusari-no-funsui.png` /
`illustrations/kusari-no-funsui-01.png`(カップから鎖が噴水のように盛り上がる図)/
`illustrations/kusari-no-funsui-02.png`(山積みのリンクが押し返す力の図解)

生成後、本文中の📎マーカーに対応するファイルパスが一致していることを確認してください(マーカー自体を
実画像への記法に差し替えるのは `note-formatter` の担当です):
- `illustrations/kusari-no-funsui-01.png` … 本文L12の📎マーカー(「くさりがカップの縁のところで、一瞬
  ふわっと持ち上がるんです」の直後)と一致
- `illustrations/kusari-no-funsui-02.png` … 本文L36の📎マーカー(「山のほうがリンクをぐいっと押し返す
  んです」の直後)と一致
