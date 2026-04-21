# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev       # 開発サーバー起動 (http://localhost:4321)
npm run build     # 静的サイトビルド → dist/
npm run preview   # ビルド結果プレビュー
```

フォーマットはPrettier + prettier-plugin-astro。

## Architecture

Astroで構築したモダンHTML/CSS実験場サイト（静的出力）。

```
src/
  layouts/Layout.astro   # 全ページ共通レイアウト。CSS変数・ヘッダー・フッター定義
  pages/
    index.astro          # トップ（実験一覧カードグリッド）
    dialog.astro         # HTML <dialog> デモ
    popover.astro        # Popover API デモ
    accordion.astro      # <details>/<summary> アコーディオンデモ
```

### スタイル方針

- CSSはScoped（各`.astro`ファイル内 `<style>`）で管理
- グローバルCSS変数は `Layout.astro` の `:root` で定義（`--color-*`, `--radius`, `--font-*`）
- ダークテーマ固定（`--color-bg: #0f0f13`）

### 新しい実験ページの追加手順

1. `src/pages/<slug>.astro` を作成し `Layout` をインポート
2. `src/pages/index.astro` の `labs` 配列にエントリを追加
