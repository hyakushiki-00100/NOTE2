# ChatGPT用 画像生成プロンプト集

**案件**: note ブランド「せんせいのふしぎノート」記事「台風の渦はなぜ「左回り」? コリオリの力と、お風呂の渦のウソ・ホント」用イラスト一式
**用途**: ChatGPT(画像生成)にそのまま貼り付けて使うプロンプト
**方針**: 1本目(猫記事)と同様、文字入り版のみ用意する。

## 進捗状況

| 成果物 | 状態 |
|---|---|
| プロフィールアイコン | ✅ 既存のものを流用(記事ごとに作り直さない) |
| 記事カバー | ⏳ 未作成(下記プロンプトで生成) |
| 解説イラスト1(回転する台の上のボール) | ⏳ 未作成 |
| 解説イラスト2(台風の渦の図解) | ⏳ 未作成 |
| 解説イラスト3(台風とお風呂のスケール比較) | ⏳ 未作成 |

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

---

## 2. 解説イラスト1: 回転する台の上でボールを投げると

本文該当箇所の要旨: 回転する台の上で友だちにボールを投げると、外から見ればまっすぐ・台の上にいる人から見ると曲がって見える。これが見かけの力(コリオリの力)の正体。

```
A two-panel comparison illustration, side by side, flat warm children's book style. Left panel
(teal-tinted background), labeled as viewed "from outside": a circular rotating platform (like a
merry-go-round) seen from above, with two simple children characters facing each other, and a
ball drawn traveling in a perfectly straight dotted line between them. Right panel (orange-tinted
background), labeled as viewed "from on the platform": the same scene, but the ball's path is drawn
as a curved dotted line, appearing to bend away from the straight path, illustrating the same throw
looking curved to someone on the spinning platform.
[共通スタイル指定を貼り付け]
Include short Japanese captions rendered clearly and legibly: title above "外から見ると まっすぐ / 台の上から見ると 曲がって見える", left panel bottom "そとから 見ると", right panel bottom "台の上から 見ると". Text must be crisp, correctly formed Japanese characters (not garbled), large and easy to read for children, in the dark brown color (#483628).
```

---

## 3. 解説イラスト2: 台風の渦の図解

本文該当箇所の要旨: 地球を北極側から見た図。低気圧の中心に向かって四方から吹き込む風がコリオリの力で右に曲げられ、全体として反時計回りの渦になる。

```
A single illustration, flat warm children's book style. A simplified top-down view of Earth seen
from above the North Pole (a circle representing the globe, simplified with a hint of a landmass
outline, not a realistic map). Several curved arrows are shown spiraling inward toward a central
point (representing the low-pressure typhoon center), each arrow bending to the right as it
approaches the center, and the combined effect forms a visible counterclockwise spiral pattern
around the center point.
[共通スタイル指定を貼り付け]
Include short Japanese captions rendered clearly and legibly: title above "台風は反時計回り", near the arrows "風が右に曲がる", near the center "低気圧". Text must be crisp, correctly formed Japanese characters (not garbled), large and easy to read for children, in the dark brown color (#483628).
```

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
