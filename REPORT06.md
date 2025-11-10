#第6回　Webエンジニアリング演習レポート
## 学籍番号
4723229

## 動作確認

入力
```
curl -X 'GET' \
  'http://localhost:8000/todos?query=%E3%82%AB%E3%83%AC%E3%83%BC' \
  -H 'accept: application/json'
```

出力
```
[
  {
    "id": 5,
    "title": "夕食の準備",
    "description": "カレーを作る",
    "completed": true
  }
]
```