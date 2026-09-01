# ChatGPT用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「台風の渦はなぜ「左回り」? コリオリの力と、お風呂の渦のウソ・ホント」用イラスト一式
**用途**: ChatGPT(画像生成)にそのまま貼り付けて使うプロンプト
**方針**: 1本目(猫記事)と同様、文字入り版のみ用意する。

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | ✅ 既存のものを流用(記事ごとに作り直さない) |
| 記事カバー | ✅ 生成済み(`covers/coriolis-no-chikara.png`)。回転矢印の向きがやや曖昧という指摘あり(FAILではないが余裕があれば修正推奨、下記参照) |
| 解説イラスト1(回転する台の上のボール) | ⚠️ 生成済みだが Opus QA で FAIL(曲がる向きが本文と逆)。下記の修正版プロンプトで**再生成が必要** |
| 解説イラスト2(台風の渦の図解) | ⚠️ 生成済みだが Opus QA で FAIL(矢印が両端矢じりで向き不定)。下記の修正版プロンプトで**再生成が必要** |
| 解説イラスト3(台風とお風呂のスケール比較) | ✅ 生成済み・QA PASS(`illustrations/coriolis-no-chikara-03.png`) |

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

タイトルは確定済み。画像内に焼き込んでください。

```
A wide horizontal illustration (aspect ratio approximately 16:8.4), flat warm children's book style.
A cheerful cartoon Earth globe (simple, friendly face optional) spinning, with a small swirling
typhoon cloud pattern near it (simple spiral shape, not photorealistic weather imagery), and a
small bathroom sink/tub icon with a tiny drain swirl on the other side, suggesting a playful
comparison between the two. Both swirls should be clearly readable as simple spiral icons, not
literal weather photography.
[共通スタイル指定を貼り付け]
Include a title at the top of the image in bold, clearly legible Japanese text: 「台風の渦はなぜ「左回り」? コリオリの力と、お風呂の渦のウソ・ホント」. The title text must be crisp, correctly formed Japanese characters (not garbled), sized to fit on 2–3 lines, in the dark brown color (#483628), positioned with calm uncluttered space behind it so it doesn't overlap the illustration below.
```

**注意**: タイトルがやや長い(34字)ため、2〜3行に収まるようレイアウトの調整が必要になる可能性があります。生成後、文字が窮屈になっていないか確認してください。

**任意の修正(FAILではないが余裕があれば)**: Opus QAで、地球の上下にある回転矢印が両方とも矢じりが左端を向いており、平面の記号として見ると上下で逆回転に見えかねないと指摘された。再生成する場合は、プロンプトに次の一文を足すとよい: `The rotation indicator should be a single continuous curved arrow wrapping around the globe with one arrowhead, not two separate arrows on the top and bottom.`

---

## 2. 解説イラスト1: 回転する台の上でボールを投げると 【要再生成・修正版】

本文該当箇所の要旨: 回転する台の上で友だちにボールを投げると、外から見ればまっすぐ・台の上にいる人から見ると曲がって見える。これが見かけの力(コリオリの力)の正体。

**修正理由(Opus QAで指摘)**: 旧版は台が反時計回りに描かれているのに、右パネルの軌道が上向きに膨らんでおり、本文L34「北半球では、動くものの進む向きに対して、右側に曲がって見えます」と逆(左に曲がって見える)になっていた。また軌道が受け手の手まで届いており、本文L22「ボールが届くころには、友だちの位置が少しずれています」(=受け手に届かない)と矛盾していた。

```
A two-panel comparison illustration, side by side, flat warm children's book style. Both panels
show the platform rotating counterclockwise (as viewed from above), with a small curved arrow
near the platform's edge indicating counterclockwise rotation, consistent in both panels.
Left panel (teal-tinted background), labeled as viewed "from outside": the rotating platform (like
a merry-go-round) seen from above, with two simple children characters facing each other across the
platform — one on the left, one on the right. A ball is drawn traveling in a perfectly straight
dotted line from the left child directly toward the right child's original position, and the line
reaches the right child.
Right panel (orange-tinted background), labeled as viewed "from on the platform": the same starting
position and throw, but now the ball's path is drawn as a curved dotted line that bends DOWNWARD
(toward the bottom of the panel, i.e. curving to the right of the ball's own direction of travel as
it moves from left to right) and the curved line ends BEFORE reaching the right child — clearly
missing the child's original position, passing below/short of them, to show the ball did not arrive
where the thrower aimed.
[共通スタイル指定を貼り付け]
Include short Japanese captions rendered clearly and legibly: title above "外から見ると まっすぐ / 台の上から見ると 曲がって見える", left panel bottom "そとから 見ると", right panel bottom "台の上から 見ると". Text must be crisp, correctly formed Japanese characters (not garbled), large and easy to read for children, in the dark brown color (#483628).
```

**生成後の確認ポイント**: 右パネルの曲線が「下向き」に曲がっているか(上向きに膨らんでいたら失敗、作り直す)。曲線がボールの進行方向に対して右側に曲がっているかを実際に指でなぞって確認する。

---

## 3. 解説イラスト2: 台風の渦の図解 【要再生成・修正版】

本文該当箇所の要旨: 地球を北極側から見た図。低気圧の中心に向かって四方から吹き込む風がコリオリの力で右に曲げられ、全体として反時計回りの渦になる。

**修正理由(Opus QAで指摘)**: 旧版は8本の矢印すべてが両端(中心側・外側の両方)に矢じりを持っており、風がどちら向きに流れているのか図として定義されていなかった。しかも「風が右に曲がる」の吹き出しが指す弧は外側の矢じりが中心から外向きに見え、本文L40「気圧が低いところには、まわりの空気がどんどん流れ込みます」と逆(吹き出しているよう)に読めた。

```
A single illustration, flat warm children's book style. A simplified top-down view of Earth seen
from above the North Pole (a circle representing the globe, simplified with a hint of a landmass
outline, not a realistic map). Exactly 8 curved arrows are shown, arranged spiraling around a
central point (representing the low-pressure typhoon center). CRITICAL: each arrow must have ONLY
ONE arrowhead, located at the END of the arrow closest to the center — the outer end (tail) of each
arrow must have NO arrowhead at all, just a plain line start. Each arrow represents wind blowing
INWARD toward the low-pressure center, curving to the right as it approaches (so that tracing every
arrow from its plain tail to its single arrowhead, the overall pattern reads as air flowing toward
the center while curving counterclockwise around it). Do not draw any arrow pointing away from the
center. This should look like a standard meteorological low-pressure inflow diagram, similar to
weather textbook illustrations of a Northern Hemisphere cyclone.
[共通スタイル指定を貼り付け]
Include short Japanese captions rendered clearly and legibly: title above "台風は反時計回り", near the arrows "風が右に曲がる", near the center "低気圧". Text must be crisp, correctly formed Japanese characters (not garbled), large and easy to read for children, in the dark brown color (#483628).
```

**生成後の確認ポイント**: 全ての矢印が「片方の端(中心側)にだけ」矢じりを持っているか(両端に矢じりが付いていたら失敗、作り直す)。矢印の矢じり側だけをたどったときに、全体が中心に向かって反時計回りに巻き込む形になっているか確認する。

---

## 4. 解説イラスト3: 台風とお風呂のスケール比較

本文該当箇所の要旨: 台風は直径数百km・数日がかりでゆっくり渦を巻く。お風呂の渦は直径数十cm・数十秒。この大きさと時間のケタ違いが、コリオリの力が効くかどうかを分ける。

```
A two-panel size/scale comparison illustration, side by side, flat warm children's book style.
Left panel (teal-tinted background): a large simple typhoon spiral icon filling most of the panel,
suggesting something huge and slow. Right panel (orange-tinted background): a small bathroom
sink or round tub with a tiny drain swirl icon, much smaller in visual scale within its panel,
suggesting something small and quick. A small clock icon near the typhoon panel suggesting "days"
and a small clock icon near the sink panel suggesting "seconds", to contrast the timescales.
[共通スタイル指定を貼り付け]
Include short Japanese captions rendered clearly and legibly: title above "大きさと時間が ぜんぜん違う", left panel bottom "台風: 直径 数百km / 数日がかり", right panel bottom "お風呂の渦: 直径 数十cm / 数十秒". Text must be crisp, correctly formed Japanese characters (not garbled), large and easy to read for children, in the dark brown color (#483628).
```

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
- [ ] 日本語テキスト(タイトル・ラベルとも)が崩れていないか拡大して確認
- [ ] カバーのタイトルが2〜3行に収まり、窮屈になっていないか確認
- [ ] イラスト2(台風の渦)の矢印の向きが「反時計回り」になっているか確認(向きの取り違えに注意)
- [ ] 解説イラストのラベルが本文の記述と一致しているか確認(本文にない説明を勝手に加えていないか)

保存先の目安: `covers/coriolis-no-chikara.png` /
`illustrations/coriolis-no-chikara-01.png`(回転台)/ `-02.png`(台風の渦)/ `-03.png`(スケール比較)

生成後、本文中の📎マーカーをファイル名で更新してください:
- `illustrations/coriolis-turntable.png` → `illustrations/coriolis-no-chikara-01.png`
- `illustrations/coriolis-typhoon.png` → `illustrations/coriolis-no-chikara-02.png`
- `illustrations/coriolis-scale-compare.png` → `illustrations/coriolis-no-chikara-03.png`
