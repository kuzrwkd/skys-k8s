# SKYS K8S

## 開発環境立ち上げ手順（Mac）

① docker desktop for Macをインストール

② docker desktopのkubernetesを有効にする

③ `brew install helm`を実行し、`helm`コマンドを使えるようにする

④ 各プロジェクトのリポジトリをローカルへcloneする  
- https://github.com/kuzrwkd/skys-client
- https://github.com/kuzrwkd/skys-api
- https://github.com/kuzrwkd/skys-scraper

⑤ `skys-k8s`ローカルリポジトリのルートに`envfile`を作成する  

`envfile`の内容
```
# project root
SKYS_SCRAPER_ROOT_PATH=/Users/＜Macのユーザー名＞/＜skys-scraperのローカルリポジトリまでのパス＞
SKYS_API_ROOT_PATH=/Users/＜Macのユーザー名＞/＜skys-apiのローカルリポジトリまでのパス＞
SKYS_CLIENT_ROOT_PATH=/Users/＜Macのユーザー名＞/＜skys-clientのローカルリポジトリまでのパス＞

# pm2.io（無くても良い）
PM2_PUBLIC_KEY=＜pm2plusのダッシュボードで入手したpublic_key＞
PM2_SECRET_KEY=＜pm2plusのダッシュボードで入手したsecret_key＞
```

⑥ 「基本操作一覧」のコマンドが使える事を確認する

## 基本操作一覧

|                            | all                | client                | api                | scraper                | 
| :------------------------- | :----------------- | :-------------------- | :----------------- | :--------------------- | 
| docker imageのビルド       | make build-all     | make build-client     | make build-api     | make build-scraper     | 
| docker imageの削除         | make clean-all     | make clean-client     | make clean-api     | make clean-scraper     | 
| kubernetes環境を構築する   | make install-all   | make install-client   | make install-api   | make install-scraper   | 
| kubernetes環境を終了させる | make uninstall-all | make uninstall-client | make uninstall-api | make uninstall-scraper | 
