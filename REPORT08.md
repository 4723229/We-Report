#　第8回 Webエンジニアリング演習 レポート

##　学籍番号
4723229

## 実装した内容
```
@app.put("/todos/{todo_id}")
async def put_todo(todo_id:int, req:TodoItemUpdate_Pydantic):
    todo = await TodoItem.get(id=todo_id)
    if todo:
        todo.title = req.title if req.title is not None else todo.title
        todo.description = req.description if req.description is not None else todo.description
        todo.completed = req.completed if req.completed is not None else todo.completed
        await todo.save()
        return todo
    raise HTTPException(status_code=404, detail=f"ID{todo_id}のTODOが見つかりません")
```

##　動作確認結果


