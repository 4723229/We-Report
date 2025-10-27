#第5回　Webエンジニアリング演習レポート
## 学籍番号
4723229

##各エンドポイントのSwagger UIでのテスト結果

##GET/

Request:

```
curl -X 'GET' \
  'http://127.0.0.1:8000/' \
  -H 'accept: application/json'
```

Response:
```
{
  "Hello": "World"
}
```

##GET/health

Request:
```
curl -X 'GET' \
  'http://127.0.0.1:8000/health' \
  -H 'accept: application/json'
```
Response:
```
{
  "status": "healthy"
}
```

##GET/ items/{item_id}

Request:
```
curl -X 'GET' \
  'http://127.0.0.1:8000/items/-1?q=test' \
  -H 'accept: application/json'
```
Response:
```
{
  "detail": "Item ID must be positive"
}
```