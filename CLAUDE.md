# 栗人 Kuryudo — プロジェクト概要

## このプロジェクトについて
自立支援事業「栗人（くりまんくりまん）」のWebサイト。
福島県南相馬市を拠点に、報徳思想を軸とした循環設計支援を提供する。

## ファイル構成
```
kuryudo/
├── index.html              # トップページ（全面再設計済み）
├── kuryudo_keiei.html      # 経営同行支援ページ（作成済み）
├── kuryudo_kemono.html     # 心の獣・伴走型自律支援ページ（作成済み）
├── kuryudo_about.html      # 獣の足跡（栗人のプロフィール）
├── kuryudo_contact.html    # お問い合わせ
├── image/                  # 画像保存フォルダ
└── CLAUDE.md
```

### 作成しないファイル
- `kuryudo_politics.html` — 政治活動ページ（保留・作成しない）

## 技術スタック
- 純粋なHTML / CSS / Vanilla JS（フレームワーク不使用）
- Google Fonts：Shippori Mincho, Cormorant Garamond, Noto Serif JP
- WebGL（生シェーダー）によるヒーロー「循環の波紋」演出（`#hero-ink` canvas）：湖面に立つ人物の足元から金の楕円波紋が広がる。読み込み時の三重発火のみ（ホバー連動・周期リピートなし）
- 巨大家紋ウォーターマーク（`.crest-mark`）：黒ロゴ.pngをCSS maskで淡金化し、各セクション背景に120vmin（モバイル150vmin）で配置。全ページ共通（index／keiei／kemono／contact。aboutは既存の`about-intro::before`ロゴに同アニメーション適用）
  - 基本は「呼吸」（crestBreath 8秒周期：拡大1.05×と濃度上昇が連動）
  - indexのSNSセクションとcontactは「ゆらゆら」（crestSway 11秒周期：拡大なし・±3.2度の揺れと濃淡が交差）
- IntersectionObserver によるスクロールリビール（.js-reveal → .is-visible）：淡→濃の着色リビール（sepia/saturateフィルタが解けて色が入る）。index／keiei／kemono／aboutに適用。contactは読み込み時fadeUpに着色を組み込み

## デザイン規律（必ず守ること）
- カラー：クリーム地(#F7F3EB ベース) × ゴールド(#B8932A アクセント)
- 黒背景は使わない
- フォント：見出しはShippori Mincho、本文はNoto Serif JP
- アニメーションは静かで有機的に。派手・急激なものは排除
- 「煽ってあげる」系のコピーは書かない。問いかけのトーンを維持

## ブランドの核心
- キャッチコピー：「世界は、循環でできている。」（読点あり）
- サブキャッチ：「言葉が届き、人が動き、経済が回り、命が巡る。」
- トーン：静寂・冷念・湧き出しの生命力
- 思想的背景：報徳四柱（至誠・勤労・分度・推譲）→ 一円融合・積小為大へとつながる

## SNSアカウント
- note：kuryudo_hotoku（https://note.com/kuryudo_hotoku）
- X（Twitter）：@kuryudo_hotoku（https://twitter.com/kuryudo_hotoku）
- Instagram：kuryudo_hotoku（https://www.instagram.com/kuryudo_hotoku/）
- 全ページのナビにSNSアイコン（X/Instagram/note・インラインSVG・`.nav-sns`）をロゴ横に設置。ヒーロー上はクリーム→スクロールでインク色。640px以下はタグライン（.nav-logo-en）を隠してアイコンを優先

## サービス構造
```
根っこ：循環設計支援
　─ 滞りを診て、循環を設計し、手放す ─

　　　↙　　　　　　　　↘

伴走型自律支援　　　　経営同行支援
（対象：個人）　　　（対象：事業者・法人）
心の獣ページへ　　　kuryudo_keiei.htmlへ
```

## 各ページの役割

### index.html（トップ・全面再設計済み）
1. ヒーロー：「世界は、循環でできている。」（1文字ずつアニメーション）
2. 報徳とはセクション（#houtoku）：四柱カード×4（各3文説明）＋一円融合・積小為大
3. サービスセクション（#service）：2カード横並び（個人/法人）
   - 個人向け「あなたの心に、獣がいる。」→ kuryudo_kemono.html
   - 事業者向け「事業の循環を、設計する。」→ kuryudo_keiei.html
4. 発信セクション（#media）：eyebrow「OurSocial」/ heading「栗人SNSアカウント」
   - noteカラム：「世界を見つめる。」
   - Xカラム：「尊徳の教えと気づきの断片を。」
   - Instagram：リンクボタンのみ
5. フッター（`id="footer-logo"` / Canvasスパークルの吸着先）

### kuryudo_keiei.html（経営同行支援・作成済み）
1. ヒーロー：「経営同行支援」（背景：IMG_5743.jpg）
2. こんなお悩みはありませんか？（5カード・2+2+1グリッド）
3. それは構造の問題かもしれません（.structure-coda引用ブロック）
4. サービスの流れ（4ステップ・料金表示なし・各ステップにイラスト：無料相談/構造診断/循環設計/運用同行.png）
5. CTA：「まずは、話してみてください。」→ ボタン「お問い合わせはこちら」→ kuryudo_contact.html

### kuryudo_kemono.html（心の獣・作成済み）
- What's Kuryudo（獣の5段階：宿る野生→自律の綻び→自我の埋没→命の対峙→誇り高き共生）
- 報徳の四柱セクション（至誠・勤労・分度・推譲）
- サービスの流れ（#flow・四柱の直後）：①獣の輪郭をなぞる（診断フォームリンク）→②獣の声を聴く（お問い合わせリンク）→③獣との調律を設計する→④巡礼に同行する
- CTA（ページ末尾）：
  1. 誘導文：「あなたの心に棲む獣は、どんな姿をしていますか？」
  2. ボタン①「心の獣を診断する」→ https://forms.gle/GLU93FmgXzxZbuwD6
  3. ボタン②「お問い合わせはこちら」→ kuryudo_contact.html

## 料金体系（内部資料。サイト上では非表示 — keieiは「サービスの流れ」として料金なしで掲載）
### 経営同行支援
| ステップ | 内容 | 料金 |
|---|---|---|
| ① 無料相談 | まず話を聞く | 無料 |
| ② 構造診断 | 構造把握・問題抽出・整理・共有 | 30,000円/回 |
| ③ 循環設計 | 循環の仕組みを設計 | 50,000〜150,000円 |
| ④ 運用同行 | 介入の深さ・回数を都度設定 | 都度見積もり |

### 伴走型自律支援（個人）
| | 料金 |
|---|---|
| 初回 | 無料 |
| 2回目以降 | 1,080円/30分＋おきもち |

## 外部連携（発信セクション）
- **note**：allorigins.win プロキシ経由でRSS自動取得（AbortController 6秒タイムアウト）
  - RSS URL：https://note.com/kuryudo_hotoku/rss
- **X（Twitter）**：公式ウィジェット（platform.twitter.com/widgets.js）+ エラーフォールバック
- **Instagram**：リンクボタンのみ（自動埋め込み不要）

## 外部リンク
- 心の獣診断：https://forms.gle/GLU93FmgXzxZbuwD6
- 初回面談予約：https://cal.com/kuryudo/syokaimuryo（現在サイト内からのリンクなし。CTAはすべてお問い合わせページへ集約）
- 2回目以降の面談：https://cal.com/kuryudo/mendan（同上）
- お問い合わせ：kuryudo_contact.html

## 作業時のルール
- 既存のJS/CSSの動作を壊さずに変更を加えること
- 変更前に必ず該当箇所を読んでから編集する
- 写真プレースホルダーはそのままにしておく（後で差し替え）
- GitHubにpushする前に必ず動作確認を促すこと
- ヒーローの「循環の波紋」演出・タイトルアニメーションは維持する

## 完了済み作業
- 料金体系の設計
- サービス構造の確定（循環設計支援）
- サービス資料スライド作成（循環設計支援_サービス資料.pptx）
- index.html 全面再設計（報徳四柱・一円融合・積小為大・サービス導線・OurSocial発信セクション）
- kuryudo_keiei.html 新規作成
- kuryudo_kemono.html 新規作成（index.htmlから心の獣コンテンツ移植）
- note RSS埋め込み実装（allorigins.win プロキシ使用）
- Xウィジェット埋め込み実装（@kuryudo_hotoku）
- 面談予約URLをcal.comに移行
- SNSアカウントID確定（X: @kuryudo_hotoku / Instagram: kuryudo_hotoku / note: kuryudo_hotoku）
- GitHub Pages 公開（kuryudo.com）
- kuryudo_anga.html / kuryudo_v3.html / CLAUDE.rtf の削除（旧ファイル整理完了）
- ヒーローのモーション刷新：全ページスクロール連動の「黄金のポイント」演出（`road` canvas）を廃止し、ヒーロー内WebGLの「循環の波紋」演出（`#hero-ink`）に置き換え。人物の足元から金の楕円波紋が広がる（初回三重発火→6.4秒周期で反復＋ホバー波紋）。WebGL非対応環境は`.hero.no-webgl`で静止画にフォールバック

- 巨大家紋ウォーターマーク＋着色リビール追加（20th.oikaze.jp リサーチの翻案。「ブランドモチーフを装飾言語として貫く」手法をロゴ×淡金で採用）

## 今後の予定
- 写真の差し込み（栗人から提供予定。image/IMG_0161.heic・巡礼.png など未反映分あり）
