# gsij_tile_downloader

国土地理院地図タイルダウンロードツール

国土地理院が発行している地図タイルをダウンロード、最新の状態に保つツールです。

### このリポジトリについて

[akchan/gsij_tile_downloader](https://github.com/akchan/gsij_tile_downloader) の fork です。元のリポジトリから、次の 1 点を修正しています。

- **1 月に実行すると更新分を取得できない不具合の修正**: 更新情報（nippo）を取得する期間は「先月の 1 日から今日まで」ですが、元の版は先月を求めるときに年を繰り下げていません。このため 1 月に実行すると、期間の始まりが「今年の 12 月 1 日」という未来の日付になり、取得対象の日が 0 件になります。1 月の場合は前年の 12 月 1 日から始めるように直しました。

それ以外は元のリポジトリと同じです。

### 背景

国土地理院が実験的に配布している地図タイルダウンロードツール（[tdlmn](https://github.com/gsi-cyberjapan/tdlmn/tree/main)）がありますが、下のような課題があります。

- Windows環境が想定されており、そのままでは他の環境で動作しない
- 逐次的処理のためダウンロード完了まで時間がかかる

gsij_tile_downloaderはこれらの課題を解消するために開発されました。

### 特徴

gsij_tile_downloaderには下記の様な特徴があります。

- [mokuroku](https://github.com/gsi-cyberjapan/mokuroku-spec), [nippo](https://github.com/gsi-cyberjapan/nippo-spec)に基づいて必要な最新を取得
- 最新版とmd5値が異なるタイルのみをダウンロード
- 作業の並列化による短い処理時間
- windows/mac/linux環境での動作
- PNG形式からJPEG形式へのconversion機能

# Usage

```bash
git clone https://github.com/bishi-eava/gsij_tile_downloader.git

cd gsij_tile_downloader

pip install -r requirements.txt

python gsij_tile_downloader.py
```

# License

MIT License

Copyright (c) 2024 Satoshi Funayama（元のリポジトリの作者）。詳細は [LICENSE](LICENSE) を参照。
