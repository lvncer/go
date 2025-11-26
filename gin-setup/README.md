# 簡単な API サーバーを構築

最初は軽量なフレームワーク「Gin」を使って API サーバーを作ります。

## Gin のインストール

以下を実行して依存をインストール：

```bash
go get github.com/gin-gonic/gin@latest
```

## サーバーコードを書く

`main.go`に以下のコードを書きます：

```go
package main

import "github.com/gin-gonic/gin"

func main() {
  r := gin.Default()
  r.GET("/ping", func(c *gin.Context) {
    c.JSON(200, gin.H{
      "message": "pong",
    })
  })
  r.Run() // listen and serve on 0.0.0.0:8080
}

```

## サーバーを実行

以下のコマンドでサーバーを起動：

```bash
go run main.go
```

ブラウザで`http://localhost:8080/ping`にアクセスすると、以下のレスポンスが返ってきます：

```json
{
  "message": "pong"
}
```

## コードの解説

- **ルーターの作成**:

  ```go
  r := gin.Default()
  ```

  Gin のルーターを作成し、ミドルウェア（ロギングやリカバリ）が自動で設定されます。

- **エンドポイントの登録**:

  ```go
  r.GET("/ping", func(c *gin.Context) { ... })
  ```

  HTTP メソッドとパス（`/ping`）を指定して処理を定義。

- **レスポンスの送信**:

  ```go
  c.JSON(200, gin.H{"message": "pong"})
  ```

  ステータスコード 200 と JSON 形式のレスポンスを返します。
