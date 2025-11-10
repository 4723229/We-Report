#第7回　Webエンジニアリング演習レポート
## 学籍番号
4723229

## 動作確認
## PUTリクエスト検証用のモデルとAPI部分のコード
モデル
```
class TodoPutSchema(BaseModel):
    title: Optional[str] = None
    description: Optional[str] = None
    completed: Optional[str] = None
```

API
```
@app.put("/todos/{todo_id}")
def put_todos(todo_id: int, req: TodoPutSchema):
    for i, todo in enumerate(todos):
        if todo.id == todo_id:
                todo.title = req.title if req.title is not None else todo.title
                todo.description = req.description if req.description is not None else todo.description
                todo.completed = req.completed if req.completed is not None else todo.completed
                return todo
            
    raise HTTPException(status_code=404, detail=f"ID{todo_id}のTODOが見つかりません")
```

## 動作確認結果
- Swagger UIでのPUTエンドポイントテスト結果
- 正常系：存在するタスクの更新

リクエスト
```
curl -X 'PUT' \
  'http://127.0.0.1:8000/todos/1' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "title": "string",
  "description": "string",
  "completed": "string"
}'
```
結果
```
{
  "id": 1,
  "title": "string",
  "description": "string",
  "completed": "string"
}
```
- 異常系：存在しないタスクIDでのエラー確認

リクエスト
```
curl -X 'PUT' \
  'http://127.0.0.1:8000/todos/100' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "title": "string",
  "description": "string",
  "completed": "string"
}'
```
結果
```
{
  "detail": "ID100のTODOが見つかりません"
}
```