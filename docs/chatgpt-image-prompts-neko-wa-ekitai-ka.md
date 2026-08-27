# ChatGPT用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「猫は液体か?」用イラスト一式
**用途**: ChatGPT(画像生成)にそのまま貼り付けて使うプロンプト
**方針**: 日本語テキストは実際の生成で問題なく描画できたため、**以降は文字入り版のみ**を用意する。

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | ✅ 完成・確認済み(オーナー確認OK) |
| 記事カバー | ✅ 完成。`covers/neko-wa-ekitai-ka.png` に反映済み(1280×670) |
| 解説イラスト1(デボラ数) | ✅ 完成。`illustrations/neko-wa-ekitai-ka-01.png` に反映済み(1200×800) |
| 解説イラスト2(鎖骨比較) | ✅ 完成。`illustrations/neko-wa-ekitai-ka-02.png` に反映済み(1200×800) |
| 解説イラスト3(容器になじむビフォーアフター) | ✅ 完成。`illustrations/neko-wa-ekitai-ka-03.png` に反映済み(1200×800) |

全成果物完成。イラスト外注(ChatGPT版)の試験は完了とする。

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

## 1. 記事カバー(再生成用・修正版)

**修正点**: 前回の生成は猫の体がツヤのある液体そのものに見えすぎていた(毛並み・脚の質感が消えていた)。
記事本文は「猫は文字通りの液体ではない」と明確に説明しているため、絵と矛盾しないよう修正。
**タイトルは【タイトル案】の1つ目「猫は液体か? 科学者が大まじめに調べた話」を仮で入れる**
(タイトルは `viral-analyst` の評価前で未確定。確定後に差し替える可能性あり)。

```
A wide horizontal illustration (aspect ratio approximately 16:8.4), flat warm children's book style.
An orange tabby cat is nestled inside a glass jar, its fluffy body clearly still readable as a cat —
visible fur texture, striped pattern continuing down the body, tucked paws and a hint of haunches —
gently curled to fit the jar's rounded shape. The cat should look snug and round, like a cat curled
up in a small space, NOT like a glossy liquid or melted substance. Avoid glassy/liquid highlights on
the body; keep the fur matte and clearly furry. Head and front paws rest on the rim, cheerful
expression.
[共通スタイル指定を貼り付け]
Include a title at the top of the image in bold, clearly legible Japanese text: 「猫は液体か? 科学者が大まじめに調べた話」. The title text must be crisp, correctly formed Japanese characters (not garbled), large enough to read clearly as a thumbnail, in the dark brown color (#483628), positioned in the upper third with calm uncluttered space behind it so it doesn't overlap the cat illustration below.
```

---

## 2. 解説イラスト3(容器になじんでいくビフォーアフター)※未作成

本文該当箇所の要旨: 自由な丸い姿勢の猫が、時間をかけて箱やボウルの形にぴったり収まっていく様子。

```
A two-panel before/after illustration, side by side, flat warm children's book style. Left panel
(teal-tinted background): an orange tabby cat sitting freely in a loose, round, relaxed pose next to
an empty rectangular box, not yet inside it. Right panel (orange-tinted background): the same cat
now settled snugly inside the box, body gently adapted to the box's shape, content expression, an
arrow with a small clock/slow-motion motif between the panels suggesting gradual change over time.
[共通スタイル指定を貼り付け]
Include short Japanese captions rendered clearly and legibly: title above "時間をかけて、体が箱の形になじんでいく", left panel bottom "自由な まるい形", right panel bottom "はこに ぴったり", between panels "ゆっくり 時間をかけて". Text must be crisp, correctly formed Japanese characters (not garbled), large and easy to read for children, in the dark brown color (#483628).
```

---

## 生成後のチェックリスト

- [ ] サイズ: カバーは1280×670pxにリサイズ、解説イラストは横1200px前後にリサイズ
- [ ] 日本語テキスト(タイトル・ラベルとも)が崩れていないか拡大して確認
- [ ] カバーの猫が「完全に液状化」して見えすぎていないか確認(毛並み・輪郭が残っているか)
- [ ] 解説イラストのラベルが本文の記述と一致しているか確認(本文にない説明を勝手に加えていないか)

保存先の目安: `covers/neko-wa-ekitai-ka.png` / `illustrations/neko-wa-ekitai-ka-03.png`
(アイコン・イラスト1・2は確認済みのため、確定後にこのリポジトリの既存ファイルと差し替えます)。
