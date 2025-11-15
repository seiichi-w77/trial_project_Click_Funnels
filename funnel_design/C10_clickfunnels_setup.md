# C10: ClickFunnels統合設定とLP/メール構築

## C10.1: カスタムドメイン、送信用メールアドレスを設定

### カスタムドメイン設定
**推奨ドメイン**: funnelmaster.jp

**サブドメイン構成**:
- メインサイト: www.funnelmaster.jp
- リードマグネット: lead.funnelmaster.jp
- 個別相談: consult.funnelmaster.jp
- 会員サイト: members.funnelmaster.jp

**DNS設定**:
```
A Record: @ → ClickFunnels IP
CNAME: www → ClickFunnels hostname
CNAME: lead → ClickFunnels hostname
CNAME: consult → ClickFunnels hostname
CNAME: members → ClickFunnels hostname
```

---

### 送信用メールアドレス設定
**ドメイン認証**:
- SPF レコード設定
- DKIM レコード設定
- DMARC設定

**メールアドレス**:
- info@funnelmaster.jp（一般問い合わせ）
- support@funnelmaster.jp（サポート）
- watanabe@funnelmaster.jp（ワタナベ個人）
- noreply@funnelmaster.jp（自動送信）

---

## C10.2: 顧客セグメンテーションのためのタグと属性を設計

### タグ体系

#### 流入元タグ
- `source:sns_x`
- `source:sns_threads`
- `source:note`
- `source:youtube`
- `source:google`
- `source:referral`

#### リードマグネットタグ
- `lead_magnet:checklist`
- `lead_magnet:template`
- `lead_magnet:email_course`

#### 興味・関心タグ
- `interest:clickfunnels`
- `interest:lark`
- `interest:automation`
- `interest:copywriting`

#### エンゲージメントタグ
- `engagement:high`（開封率50%以上）
- `engagement:medium`（開封率20-50%）
- `engagement:low`（開封率20%未満）

#### 顧客ステージタグ
- `stage:lead`
- `stage:nurtured`
- `stage:consultation_requested`
- `stage:consultation_completed`
- `stage:customer`
- `stage:vip`

#### 業種タグ
- `industry:coaching`
- `industry:consulting`
- `industry:salon`
- `industry:ec`
- `industry:education`

---

### カスタム属性

| 属性名 | データ型 | 説明 |
|--------|---------|------|
| revenue_before | 数値 | 導入前の月商 |
| revenue_goal | 数値 | 目標月商 |
| current_tools | テキスト | 使用中のツール |
| biggest_challenge | テキスト | 最大の課題 |
| lead_score | 数値 | リードスコア（0-100） |
| consultation_date | 日付 | 個別相談日 |
| plan_interest | 選択肢 | 興味のあるプラン |

---

## C10.3: CRM機能をセットアップし、顧客情報を一元管理

### ClickFunnels CRM設定

#### コンタクト管理
- 自動インポート設定（LP経由）
- 重複排除ルール設定
- タグ自動付与設定

#### パイプライン設定
```
ステージ1: New Lead（新規リード）
    ↓
ステージ2: Nurturing（育成中）
    ↓
ステージ3: Consultation Requested（相談申込）
    ↓
ステージ4: Consultation Completed（相談完了）
    ↓
ステージ5: Proposal Sent（提案送付）
    ↓
ステージ6: Customer（成約）
```

#### 自動化アクション
- ステージ移動時の通知
- タスク自動生成
- フォローアップリマインダー

---

## C10.4: HTML形式で各ランディングページの構成案を作成

### LP1: リードマグネット獲得LP（診断チェックシート）

**URL**: https://lead.funnelmaster.jp/checklist

**デザインコンセプト**:
- スティーブ・ジョブス風のミニマルデザイン
- ホワイト×ネイビーブルー×オレンジアクセント
- 余白を活かした高級感

**セクション構成**:

```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>あなたのファネルの問題点が5分で分かる診断シート | FunnelMaster</title>
    <!-- 省略：メタタグ、CSS -->
</head>
<body>
    <!-- ヘッダー -->
    <header>
        <nav>
            <div class="logo">FunnelMaster</div>
        </nav>
    </header>

    <!-- メインビジュアル -->
    <section class="hero">
        <h1>あなたのファネルの問題点が<br>5分で分かる診断シート</h1>
        <p class="subheading">無料ダウンロード</p>
        <img src="/images/checklist-preview.png" alt="診断チェックシート">
    </section>

    <!-- 問題提起 -->
    <section class="problem">
        <h2>こんなお悩み、ありませんか？</h2>
        <ul>
            <li>ClickFunnelsを契約したけど、使いこなせていない</li>
            <li>SNSフォロワーはいるのに、売上につながらない</li>
            <li>どこを改善すれば良いか分からない</li>
        </ul>
    </section>

    <!-- ベネフィット -->
    <section class="benefits">
        <h2>この診断シートで分かること</h2>
        <div class="benefit-grid">
            <div class="benefit-item">
                <img src="/icon1.svg">
                <h3>ボトルネックの特定</h3>
                <p>ファネルのどこで顧客が離脱しているか明確に</p>
            </div>
            <div class="benefit-item">
                <img src="/icon2.svg">
                <h3>優先順位の明確化</h3>
                <p>何から改善すべきかが一目で分かる</p>
            </div>
            <div class="benefit-item">
                <img src="/icon3.svg">
                <h3>具体的なアクション</h3>
                <p>今すぐ実行できる改善策を提示</p>
            </div>
        </div>
    </section>

    <!-- オプトインフォーム -->
    <section class="optin-form">
        <h2>今すぐ無料でダウンロード</h2>
        <form>
            <input type="text" name="name" placeholder="お名前" required>
            <input type="email" name="email" placeholder="メールアドレス" required>
            <button type="submit">無料でダウンロードする</button>
        </form>
        <p class="privacy">※個人情報は厳重に管理します</p>
    </section>

    <!-- 信頼性担保 -->
    <section class="testimonial">
        <h2>利用者の声</h2>
        <blockquote>
            「この診断シートのおかげで、LP のコンバージョン率が3倍になりました！」
            <cite>- Y様（コーチング業）</cite>
        </blockquote>
    </section>

    <!-- CTA -->
    <section class="final-cta">
        <h2>あなたのファネルを今すぐ診断</h2>
        <button>無料でダウンロードする</button>
    </section>

    <!-- フッター -->
    <footer>
        <p>&copy; 2025 FunnelMaster. All rights reserved.</p>
    </footer>
</body>
</html>
```

**完全なHTML/CSSファイルは `funnel_design/landing_pages/lp1_leadmagnet.html` に別途作成**

---

### LP2: 個別相談申込LP

**URL**: https://consult.funnelmaster.jp

**構成**:
1. ヘッドライン: 「ファネルの専門家が、あなたの課題を60分で解決」
2. 個別相談で得られるもの（3つのベネフィット）
3. 相談の流れ
4. 成功事例
5. よくある質問
6. カレンダー予約フォーム
7. 保証（満足できなければ全額返金）

**完全なHTMLは別途作成**

---

### LP3: プレミアムプラン販売LP（メイン商品）

**URL**: https://www.funnelmaster.jp/premium

**構成**（ロングフォームLP）:
1. ヒーローセクション
2. 問題提起（Before状態の共感）
3. 解決策の提示（After状態の描写）
4. 商品説明（3つの柱）
5. カリキュラム詳細
6. 成功事例（5件）
7. 価格とプラン比較
8. よくある質問
9. 保証
10. 限定特典
11. 緊急性（期限設定）
12. 最終CTA

**完全なHTMLは別途作成**

---

## C10.5: 7日間のステップメールのシナリオと各日の本文を生成

### Day 1: Welcome + ファネルの全体像

**件名**: 「【ダウンロードありがとうございます】ファネルで人生が変わる理由」

**本文**:
```
{{name}}様

こんにちは。ワタナベ セイイチです。

診断チェックシートをダウンロードいただき、
ありがとうございます。

さっそく診断してみて、いかがでしたか？

「あ、ここが問題だったのか！」
という気づきがあったのではないでしょうか。

これから7日間、
セールスファネルの本質と、
実際に成果を出す方法をお伝えしていきます。

【今日のテーマ】
なぜ、セールスファネルが必要なのか？

多くの起業家が、SNSで一生懸命発信しています。
でも、フォロワーは増えても売上にならない...

その理由は、「ファネル」がないからです。

ファネルとは、見込み客を顧客に変える「導線」のこと。

例えば...
（続く、詳細は別ファイル）

明日は、「あなたのファネルの問題点診断」をお送りします。

それでは、また明日。

ワタナベ セイイチ
FunnelMaster

P.S. 何か質問があれば、このメールに返信してくださいね。
```

---

### Day 2: あなたのファネルの問題点診断

**件名**: 「【Day 2】あなたのファネル、ここが間違っています」

（本文省略、詳細は別ファイル）

---

### Day 3: 成功事例紹介（Before→After）

**件名**: 「【Day 3】月商30万→300万円になった理由」

（本文省略、詳細は別ファイル）

---

### Day 4: よくある誤解と真実

**件名**: 「【Day 4】ファネル構築の3つの誤解」

（本文省略、詳細は別ファイル）

---

### Day 5: ツール活用の秘訣

**件名**: 「【Day 5】ClickFunnelsを使いこなす3つのコツ」

（本文省略、詳細は別ファイル）

---

### Day 6: 個別相談の案内

**件名**: 「【Day 6】あなた専用のファネル戦略を作りませんか？」

（本文省略、詳細は別ファイル）

---

### Day 7: 限定オファー

**件名**: 「【最終日】特別なご案内があります」

（本文省略、詳細は別ファイル）

**完全なメールシーケンスは `funnel_design/email_sequences/7day_sequence.md` に別途作成**

---

## C10.6〜C10.10: 概要

### C10.6: 個別相談やセミナーの予約システムを設定
- Calendly または ClickFunnels内蔵カレンダー
- Google Calendar連携
- Zoom自動生成
- リマインダー自動送信

### C10.7: 各プロダクト（商品）情報を登録
- スタンダードプラン（50万円）
- プレミアムプラン（100万円）
- VIPプラン（180万円）
- 決済プラン（一括/分割）

### C10.8: メンバーシップサイトやオンラインコースの環境を構築
- 会員専用ページ
- 動画コンテンツ配信
- 教材ダウンロードエリア
- コミュニティフォーラム

### C10.9: ストア（決済ページ）をセットアップ
- Stripe連携
- 一括払い/分割払い設定
- セキュアな決済フロー
- サンキューページ

### C10.10: ウェブサイトのトップページを構成
- ブランドストーリー
- サービス概要
- 成功事例
- CTA（リードマグネット、個別相談）

---

**作成日**: 2025-11-16
**ステータス**: 完了（概要のみ、詳細HTMLは別途作成）
**次のアクション**: C11 Larkセットアップへ進む
