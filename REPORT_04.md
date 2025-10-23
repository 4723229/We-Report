##第4回WEBエンジニアリング演習　レポート
##4723229

##実装したプログラム
import sys
import json

#元のデータを辞書型のbooksへ
books = [
    {
        "title": "Java基礎",
        "author" : "佐藤花子",
        "year": 2023,
        "isbn": "978-4-987654-32-1",
        "price": 2800
    },
    {
        "title": "Web開発",
        "author" : "山田次郎",
        "year": 2023,
        "isbn": "978-4-111111-11-1",
        "price": 3200
    },
]

#実行時引数を取得し、辞書型データに変換したのちbooksに追加
new_data = sys.argv[1]
new_book = json.loads(new_data)
books.append(new_book)

#それぞれのデータを番号をつけて出力
num = 0
for book in books:
    num += 1
    print(f" {num} . {book['title']} -  {book['author']} ({book['year']}) ISBN: {book['isbn']} 価格: {book['price']}円")
