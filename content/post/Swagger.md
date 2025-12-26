+++
author = "←この日付無視してね"
title = "Swagger  ⏰約20分"
date = "2024-12-28"
description = ""
+++

--------------------------------------------------------

Swagger 環境  
・API version：OpenAPI 3.0.0  
・API表示ツール：Swagger UI  
・API編集ツール：Swagger Editor   

--------------------------------------------------------

## 📚 [swagger editor](https://editor.swagger.io/)   
-  ↑まずはここをクリック

## 🌞 **Swaggerとは**  
🌷 オンラインのアプリを作るには、バックエンド（Webサーバ上で動くプログラム）を開発する必要があります  
🌷 バックエンドのコードを書く前に、何のデータをどんな形でサーバに送るのか、アカウントがなかったらどのようなエラーを返すか（404？401？)などを決めておく必要があります。これを Web API と言います  
🌷 Web API （厳密には RESTful API）を決めるために、Swaggerというツールが便利です。バックエンドのコードを書くときには Swagger で決めた内容を確認しながら書いていきます  

## 🖊 パスの説明をします  
### 1. パスとは何か？
🌷 パスは、Web サーバー上で特定のデータや機能にアクセスするための「住所」のようなものです。  
たとえば：  

- 住所（パス）: localhost:8080/accounts  
- 意味: 「アカウントの情報がある場所」  
- これをブラウザやアプリが指定して、サーバーに「この住所にある情報をください」と頼む形です。  

### 2. 操作（HTTPメソッド）と組み合わせる  
🌷 パスは操作の種類と一緒に使います。操作の種類は「HTTPメソッド」と呼ばれる以下のものです：  

- GET: データを取得する（見るだけ）  
- POST: 新しいデータを追加する（作る）  
- PUT: データを更新する（書き換える）  
- DELETE: データを削除する（消す）  
※今回使用するのはGETとPUT
  

## 🖊 実際に書いていきます     
🌷 画像はswagger editor (左) とswagger UI (右) です   
- editor: 設定を書く場所
- UI：editorで書いた設定が反映されてドキュメントになる場所  

🌷 コードをeditorにコピペしながら、UIと比べて理解していきましょう     
🌷 途中エラーが出ますが、最終的に解消されるのでそのまま進めてください（最終的にエラーが解消されなかったときは再起動してください）

 ![images](/images/Swagger_final.png)

--------------------------------------------------------
## ediorを空にして書いていきましょう！
![images](/images/Swagger_first.png)
<br/>

## ① openapi / info
- API の名前・説明を書く場所。
- UI の一番上にそのまま表示されます。

コピペ用↓
``` yaml
openapi: 3.0.0
info:
  title: メモAPI
  version: 1.0.0
  description: |
    簡単なメモアプリ用のAPIです。
    1つのメモデータを取得・更新することができます。
```
 ![images](/images/Swagger_openapi_info.png)
<br/>

## ② tags
- APIをグループ分けするためのタグ。
- UIにmemoという見出しができます。

コピペ用↓
``` yaml
tags:
  - name: memo
    description: メモ内容の取得・更新
```
 ![images](/images/Swagger_tags.png)
<br/>

## ③ paths（APIの本体）
### 1. GET /memo（取得）
- メモを「読む」API。
- UI に青い「GET」ボタンが表示されます。

コピペ用↓
``` yaml
paths:
  /memo:
    get:
      tags:
        - memo
      summary: 現在のメモ内容を取得する
      description: 保存されている最新のメモ内容を取得します。
      responses:
        "200":
          description: メモの取得に成功しました
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Memo"
```
 ![images](/images/Swagger_paths_get.png)
 <br/>

### 2. PUT /memo（更新）
- メモを「書き換える」API。
- UI に黄色いフォームが表示され、text を入力できます。

コピペ用↓　⚠インデントに注意！
``` yaml
    put:
      tags:
        - memo
      summary: メモ内容を更新する
      description: 指定されたメモ内容で /memo リソースを上書きします。
      requestBody:
        required: true
        content:
          application/x-www-form-urlencoded:
            schema:
              type: object
              required:
                - text
              properties:
                text:
                  type: string
                  description: 保存するメモのテキスト（空文字不可）
                  example: "買い物リスト：りんご、牛乳"
      responses:
        "200":
          description: メモの更新に成功しました
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Memo"
        "400":
          description: textが空
          content:
            text/plain:
              schema:
                type: string
                example: "メモを入力してください"
```
 ![images](/images/Swagger_paths_put.png)
 <br/>

## ④ components（データ型）
- API が扱うデータの形（モデル）を定義します。
- UI の下部に「Memo」が表示されて中身が確認できます。

コピペ用↓　⚠インデントに注意！
``` yaml
components:
  schemas:
    Memo:
      type: object
      properties:
        text:
          type: string
          example: "買い物リスト：りんご、牛乳"
      required:
        - text
```
 ![images](/images/Swagger_components.png)
### 🌷完成！

--------------------------------------------------------

## ☆最終版editor↓
``` yaml
openapi: 3.0.0
info:
  title: メモAPI
  version: 1.0.0
  description: |
    簡単なメモアプリ用のAPIです。
    1つのメモデータを取得・更新することができます。

tags:
  - name: memo
    description: メモ内容の取得・更新

paths:
  /memo:
    get:
      tags:
        - memo
      summary: 現在のメモ内容を取得する
      description: 保存されている最新のメモ内容を取得します。
      responses:
        "200":
          description: メモの取得に成功しました
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Memo"

    put:
      tags:
        - memo
      summary: メモ内容を更新する
      description: 指定されたメモ内容で /memo リソースを上書きします。
      requestBody:
        required: true
        content:
          application/x-www-form-urlencoded:
            schema:
              type: object
              required:
                - text
              properties:
                text:
                  type: string
                  description: 保存するメモのテキスト
                  example: "買い物リスト：りんご、牛乳"
      responses:
        "200":
          description: メモの更新に成功しました
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Memo"
        "400":
          description: textが空
          content:
            text/plain:
              schema:
                type: string
                example: "メモを入力してください"

components:
  schemas:
    Memo:
      type: object
      properties:
        text:
          type: string
          example: "買い物リスト：りんご、牛乳"
      required:
        - text
```

## ☆最終版UI↓
 ![images](/images/Swagger_final_UI.png)
 ![images](/images/Swagger_final_UI2.png)
 ![images](/images/Swagger_final_UI3.png)


🌷 FileタブのSave as YAML を押すと左のコードをyaml形式で保存できるため、このコードをチームで共有できます。  
🌷 他のチームのコードを開くときは、FileタブのImport fileを押し、保存したファイルを開くと閲覧や編集ができる。

## まとめ
- info: APIの基本情報
- tags: カテゴリ分け
- paths: GETやPUTの処理を書く本体
- components: データの定義

以上でswaggerは終わり🎉  

2/5進んだよ🎊  何分かかかったかな？  休憩してね☕  

次はIntellij ideaでバックエンドのコードを書いていくよ！   








