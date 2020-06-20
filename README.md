# RustでのServerlessFrameworkサンプル


## 環境準備
### node_moduleインストール
```
npm install
```

## ServerlessFramework
### init


## 実行コマンド
### build
```
cargo build
```

### ローカル環境実行
```
npx sls invoke local -f hello_world --path src/test/resources/test_request.json
```

### デプロイ
```
npx sls deploy
```

### AWS Lambdaに対してのテスト
```
npx sls invoke -f hello_world --path src/test/resources/test_request.json
```

### API Gatewayに向けてのテスト
```
curl -X GET  https://xxxxxxxx.execute-api.ap-northeast-1.amazonaws.com/dev/
```

### Resources削除
```
npx sls remove
```
