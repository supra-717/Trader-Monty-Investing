---
layout: default
title: "Portfolio Review"
grand_parent: 日本語
parent: スキルガイド
nav_order: 36
lang_peer: /en/skills/portfolio-review/
permalink: /ja/skills/portfolio-review/
---

# Portfolio Review
{: .no_toc }

DeGiroスイングトレーダー向け14ルール取引システムを使った完全なポートフォリオレビューを実行するスキルです。ポートフォリオのスクリーンショット、CSV、またはデータの貼り付けを提供してレビュー、ポジション分析、EUR建て新規エントリースキャン、優先アクションを求める場合に使用します。
{: .fs-6 .fw-300 }

<span class="badge badge-free">API不要</span>

[スキルパッケージをダウンロード (.skill)](https://github.com/tradermonty/claude-trading-skills/raw/main/skill-packages/portfolio-review.skill){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[GitHubでソースを見る](https://github.com/tradermonty/claude-trading-skills/tree/main/skills/portfolio-review){: .btn .fs-5 .mb-4 .mb-md-0 }

<details open markdown="block">
  <summary>目次</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

詳細な英語ガイドは [English version](/en/skills/portfolio-review/) をご参照ください。

## 概要

DeGiro EUR建てスイングトレーダー向けの7ステップ構造ポートフォリオレビューを実行し、全ポジションに14のハードルールを適用します。スクリーンショット、CSVペースト、手動入力から動作し、ブローカーAPIや外部口座接続は不要です。出力はテーブルのみで、具体的なアクション指示を含みます。

## 主な機能

- スクリーンショットやCSVからポジションデータを読み取り
- WebSearchで現在の市場データを取得
- 14のハードルールを全ポジションに適用
- 市場レジーム判定（RISK-ON / NEUTRAL / RISK-OFF）
- EUR建て新規エントリーのスキャン（Tradegate Core ETFs含む）
- 優先アクションリスト（緊急度順）
- ポートフォリオヘルススコア（10点満点）

## リソース

| ファイル | 目的 |
|------|---------|
| `references/trading-rules.md` | 14のハードルールと違反チェックリスト |
| `references/review-framework.md` | 出力テンプレート付きレビュー構造 |
| `references/degiro-reference.md` | 取引所、EUR ETFリスト、ウォッチリスト、逆指値設定 |
| `TRADING_SYSTEM_MASTER.md` (root) | 完全な取引システム（ポートフォリオベースライン含む） |
