# ウェルネスの森を守る会のサイトの開発について
## vercel.jsonの記述の説明
このプロジェクトの `vercel.json` には以下の配信ルールが設定されています。
1. **検索エンジンの非公開化（noindex）**
   サイト全体("source": "/(.*)")がGoogleなどの検索結果に引っかからないようにしています。
   →"X-Robots-Tag": "noindex, nofollow"
2. **CSVファイルのキャッシュ無効化**
   `activity.csv` や `album_list.csv` などのCSVデータ("source": "/(.*\\.csv)")は、
   更新が即座に画面へ反映されるよう、Vercelおよびブラウザ側のキャッシュを完全に
   無効化（`s-maxage=0`）しています。
   →"Cache-Control": "... s-maxage=0"
   ※CSV以外の画像やHTML/CSSはキャッシュされるため、通信量をsaveし通信速度を高める事になる。
