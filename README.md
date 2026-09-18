# 第9回日本メディカルAI学会学術集会 ウェブサイト

2027年6月11日（金）〜12日（土）／パシフィコ横浜会議センター

`deploy/` 以下が公開されるサイト本体。GitHub Actions で GitHub Pages へ配信する。

## 構成

```
deploy/
├── index.html   サイト本体（単一ページ。ページ遷移は JS で行う）
├── support.js   index.html の描画ランタイム（生成物・編集禁止）
├── assets/
│   └── kv.avif  キービジュアル
└── .nojekyll    Jekyll の処理を無効化
```

## 編集方法

- ビルド工程はない。静的ファイルをそのまま配信する（npm / bundler は導入しない）。
- 内容の変更は `deploy/index.html` 内の `<x-dc>` テンプレートおよび `<script data-dc-script>` を編集する。
- `deploy/support.js` は生成物のため手で編集しない。React 18 は起動時に unpkg から読み込む。

## デプロイ

`main` へ push すると `.github/workflows/deploy.yml` が動作し、`deploy/` の内容が公開される。
