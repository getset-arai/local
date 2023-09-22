## VM
### app
- アプリサーバ
- Laravel 10
- 内部的にapp:9000でリッスン
- DockerfileのCOPYコマンドとdocker composeのvolumes機能の兼ね合いの問題でホストマシンでの初回起動時のみこのコンテナ内でinit.shを実行する
### web
- webサーバ
- nginx 
- localhost:8080でアクセス可能
## SQL Database
### db
- MySQL
- localhost:3306でアクセス可能（ymlにユーザ情報記載）
## Azure Archive Storage(=Azure Blob Storage内のアクセス層をarchiveにしたもの)
### azurite
- Azure Storageのローカルエミュレータ（Azure Blob Storageも含まれる）
- アカウント名（エミュレータ固定）: `devstoreaccount1`
- アカウントキー（エミュレータ固定）: `Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==`
- 接続文字列: `AccountName=devstoreaccount1;AccountKey=Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==;DefaultEndpointsProtocol=http;BlobEndpoint=http://127.0.0.1:10000/devstoreaccount1;QueueEndpoint=http://127.0.0.1:10001/devstoreaccount1;TableEndpoint=http://127.0.0.1:10002/devstoreaccount1;`
- 他のdockerコンテナから通信する場合はドメインをコンテナ名にする（例: http://127.0.0.1:10000/devstoreaccount1→http://azurite:10000/devstoreaccount1）
- [Azure StorageのGUIクライアント](https://azure.microsoft.com/ja-jp/products/storage/storage-explorer)
## SSO
### KeyCloak
- OSSでSAML IdP機能を持つ
- keycloak:8080（または8443）で他のdockerコンテナからアクセス可能
- https://www.keycloak.org/

