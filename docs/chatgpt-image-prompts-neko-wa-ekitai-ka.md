# ChatGPT用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「猫は液体か?」用イラスト一式
**用途**: ChatGPT(画像生成)にそのまま貼り付けて使うプロンプト

---

## 先に: 日本語テキストについての注意

ChatGPT/DALL-E系の画像生成は、**画像内の日本語テキストの描画が不安定**です(文字化け・崩れが起きやすい)。
今回の解説イラストは「固体っぽい!」「液体っぽい!」のような日本語ラベルが説明の核なので、以下のいずれかで
進めることをおすすめします。

- **方法A(推奨)**: プロンプトでは**文字を描かせず、絵の要素だけを生成**させ、日本語ラベルは note の編集画面や
  画像編集ソフトで**後から自分で追加**する。各プロンプトに「文字なしバージョン」も併記しました。
  カバー・アイコン)。
- **方法B**: 文字入り版もダメ元で試す(各プロンプトに文字入り版も併記)。崩れたら生成し直すか、方法Aに切り替える。
- 生成後は**必ず日本語テキスト部分を拡大して確認**してください。崩れていたら方法Aに切り替えます。

---

## 共通スタイル指定(毎回のプロンプト冒頭に付けると絵柄が揃います)

```
Flat, warm, friendly children's educational illustration style (like a Japanese picture book for
elementary schoolers). Simple flat shapes, soft rounded corners, no photorealism, no realistic
human faces. Clean vector-like line art with a warm brown outline (#483628). Color palette limited
to: cream background (#FBF3E4), terracotta orange (#E08454, shadow #BF673C), deep teal
(#3A6960, light teal #92B5AB). Cheerful and gentle mood, appropriate for children. No text unless
specified.
```

---

## 1. プロフィールアイコン

用途: note アカウントのプロフィール画像。正方形。中央にトリミングされるので主要素は中央に。

**そら先生キャラクターの制約(重要)**: 写実的な人間の顔にしない。実在の教員だったかのような具体的な設定
(制服・年齢・特定の学校を思わせる意匠)は入れない。「先生っぽい」小物(メガネ・本など)で雰囲気だけ出す。
今回は記事テーマ(猫)に合わせて、**擬人化した「先生猫」のマスコット**として作る案を基本にしています
(人間キャラクターにしたい場合は末尾の代替案を使用)。

```
A cute flat-illustration mascot: an orange cat character wearing round glasses and a graduation cap,
smiling warmly, front-facing, head-and-shoulders framing, centered in a square 1:1 composition.
[共通スタイル指定を貼り付け]
No text. Square image, subject centered with generous margin so it reads clearly even when cropped
into a circle.
```

**代替案(人間の先生キャラクターにしたい場合)**:
```
A cute flat-illustration mascot of a gentle, friendly female teacher character (stylized, NOT
photorealistic, no specific identifiable facial features), wearing simple glasses, warm smiling
expression, front-facing, head-and-shoulders framing, centered in a square 1:1 composition.
[共通スタイル指定を貼り付け]
No text. Square image, subject centered with generous margin so it reads clearly even when cropped
into a circle.
```

---

## 2. 記事カバー画像

用途: 記事「猫は液体か?」のサムネイル。横長 1280×670 相当(16:8.35程度の横長比率を指定)。

**内容の注意**: 記事本文は「猫は文字通りの液体ではない」と明確に説明しています。**猫が完全に液状化して
見えるほどの表現は避け**、「液体っぽく見える」程度の、ユーモラスだが誤解を招かない絵にしてください
(例: 瓶から顔と前足がのぞいている程度で、体は瓶の形に沿ってはいるが「猫」と分かる輪郭を保つ)。

```
A wide horizontal illustration (aspect ratio approximately 16:8.4), flat warm children's book style.
An orange cat is nestled snugly inside a glass jar, its body gently conforming to the jar's rounded
shape while still clearly readable as a cat (head, ears, and front paws visible over the rim,
cheerful expression). The cat should look "liquid-like" in a playful, rounded way, but NOT fully
melted or shapeless — it must still read unmistakably as a cat, not a puddle.
[共通スタイル指定を貼り付け]
No text. Leave calm, uncluttered negative space in the upper third for a title to be added later.
```

---

## 3. 解説イラスト(3点)

各図は本文(`articles/neko-wa-ekitai-ka.md`)の該当箇所の説明**だけ**を絵にしてください。本文にない設定・
仕組みの解釈を絵の演出のために付け足さないこと(過去に、本文にない解剖学的説明をイラストが独自に描き足し、
しかも内容が事実と逆だった、という事故が実際に起きています。ラベルの文言は必ず本文の記述に合わせてください)。

### 3-1. デボラ数のイメージ図(見ている時間で見え方が変わる)

**文字なし版(推奨・後からラベルを自分で追加)**:
```
A two-panel comparison illustration, side by side, flat warm children's book style. Left panel
(teal-tinted background): an orange cat mid-jump, dynamic action pose, limbs stretched, motion
lines, looking energetic and "solid-like". A small clock icon nearby suggesting a short moment.
Right panel (orange-tinted background): the same cat curled up and settled, body gently spread and
rounded on a shallow plate/tray shape, calm and "liquid-like", suggesting a long time has passed. An
arrow points from the left panel to the right panel labeled with a clock/time motif.
[共通スタイル指定を貼り付け]
No text, no labels — leave clear empty space above each panel and below each panel for captions to
be added later.
```

**文字入り版(ダメ元で試す場合、上のプロンプト末尾を以下に差し替え)**:
```
Include short Japanese captions rendered clearly and legibly: above the illustration "「見ている時間」で見え方がかわる", left panel top "見ている時間が みじかい" bottom "固体っぽい!", right panel top "見ている時間が ながい" bottom "液体っぽい!". Text must be crisp, correctly formed Japanese characters (not garbled), large and easy to read for children.
```

### 3-2. ヒトとネコの鎖骨の比較図

本文の要旨: ヒトの鎖骨は肩・胸の骨としっかりつながっていて肩幅を大きく変えられない。ネコの鎖骨は筋肉の中に
浮いていて他の骨とつながっておらず、肩幅を狭められる。**「ヒトの腕の可動域が狭い」という説明は誤り。ヒト側は
「肩幅を変えられない」という点だけを描くこと。**

**文字なし版(推奨)**:
```
A two-panel simplified anatomical comparison illustration, side by side, flat warm children's book
style (simplified, diagrammatic, not realistic anatomy). Left panel (teal-tinted background): a
simple flat silhouette of a human upper body/torso from the front, with two collarbones drawn as
solid rod shapes firmly connecting the shoulder points to the breastbone in the center (rigid,
fixed, clearly "locked in place"). Right panel (orange-tinted background): a simple flat cat
silhouette from the front, with two small bone shapes drawn floating inside soft muscle-colored
ovals near the front leg joints, connected by a dashed outline to suggest they are NOT rigidly
attached to other bones (loose, floating, flexible).
[共通スタイル指定を貼り付け]
No text — leave clear empty space above and below each panel for captions to be added later.
```

**文字入り版**:
```
Include short Japanese captions rendered clearly and legibly: title above "鎖骨のつながりかたが ちがう", left panel top "ヒトの鎖骨" bottom "肩とむねの骨に しっかりつながっている" and "だから 肩はばを 大きく 変えられない", right panel top "ネコの鎖骨" bottom "筋肉の中に浮いていて 他の骨とつながっていない" and "だから 肩はばを せまくできる". Text must be crisp, correctly formed Japanese characters (not garbled), large and easy to read for children.
```

### 3-3. 猫が容器の形になじんでいく図(ビフォーアフター)

**文字なし版(推奨)**:
```
A two-panel before/after illustration, side by side, flat warm children's book style. Left panel
(teal-tinted background): an orange cat sitting freely in a loose, round, relaxed pose next to an
empty rectangular box, not yet inside it. Right panel (orange-tinted background): the same cat now
settled snugly inside the box, body gently adapted to the box's shape, content expression, an arrow
with a small clock/slow-motion motif between the panels suggesting gradual change over time.
[共通スタイル指定を貼り付け]
No text — leave clear empty space above and below each panel for captions to be added later.
```

**文字入り版**:
```
Include short Japanese captions rendered clearly and legibly: title above "時間をかけて、体が箱の形になじんでいく", left panel bottom "自由な まるい形", right panel bottom "はこに ぴったり", between panels "ゆっくり 時間をかけて". Text must be crisp, correctly formed Japanese characters (not garbled), large and easy to read for children.
```

---

## 生成後のチェックリスト

- [ ] サイズ: アイコンは正方形(500×500px以上にリサイズ)、カバーは1280×670px、解説イラストは横1200px前後にリサイズ
- [ ] 日本語ラベルが崩れていないか拡大して確認(崩れていたら方法Aで文字を後付け)
- [ ] カバーの猫が「完全に液状化」して見えすぎていないか確認
- [ ] 解説イラストのラベルが本文の記述と一致しているか確認(本文にない説明を勝手に加えていないか)
- [ ] そら先生アイコンが写実的な人間の顔になっていないか確認

保存先の目安: `profile/icon.png` / `covers/neko-wa-ekitai-ka.png` /
`illustrations/neko-wa-ekitai-ka-01.png`〜`-03.png`(既存のAI制作版から差し替える場合)。
