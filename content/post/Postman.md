---
author: ←この日付無視してね
title: Postman  ⏰約20分
date: 2019-03-08
description: 
math: true
---

## 📚 [PostMan](https://www.postman.com/downloads/)
-  ↑ここからデスクトップ版Postmanアプリをダウンロードできます
-  Postmanにはweb版というブラウザで開けるものと、デスクトップ版があり、デスクトップ版しかlocalhost環境にアクセスできません  
-  デスクトップにPostmanアプリがない人はダウンロードしましょう 
1. Windows 64-bit などと書いたオレンジ色のボタンを押す  
2. ダウンロードしたexeを開く（setup)
3. sign upする  
4. 新しい Workspaces を作るので WorkSpaces と Create Workspace を押す    
![images](/images/postman8.png) 
5. 名前をLessonServerなどと決め、指示に従っていく  
🌷 この画面が出たらOK
![images](/images/postman9.png) 

## 🌞 **Postmanとは**  
🌷 記述したバックエンドのコードが正しく動いているのかをテストするためのツールです  
🌷 バックエンドの Web API を呼び出して、何が返ってきているのかを可視化することができます  


## 🖊 作っていきます  
🌷 + を押します
![images](/images/postman1.png)   

-  
-  
-  
🌷 Rest API basics を押します
![images](/images/postman2.png)  

-  
-  
-   
🌷 GET POST PUT DELが出てきます  
🌷 POSTを押します     
![images](/images/postman3.png)

-  
-  
-   
## Post 
🌷 パスは **{{< color  yellowgreen "localhost:8080/accounts" >}}**と{{< color  deeppink "入力" >}}     
🌷 {{< color  deeppink "Bodyを選択" >}}    
🌷 {{< color  deeppink "x-www-form-urlencodedを選択" >}}    
🌷 {{< color  deeppink "アカウントとパスワード" >}} の {{< color  purple "KeyとValueを入力するための欄が出てきます" >}}  
🌷 {{< color  purple "Key" >}} に {{< color  green "account_id ,  password" >}}と{{< color  deeppink "入力" >}}  
🌷 {{< color  purple "Value" >}} に 自分のつけたいアカウント名とパスワードを{{< color  deeppink "入力" >}} （ここでは name と password）   
（これがフォームデータとして {{< color  deeppink "x-www-form-urlencoded" >}} 形式で送信される  
🌷 **Intellij起動**し、LessonServer実行してください、  
🌷 {{< color  deeppink "Sendを押すと" >}}  
🌷 {{< color  purple "200か204" >}}と表示されるとOKです      
🌷 **{{< color  yellowgreen "localhost:8080" >}}**   
-  **localhost**はコンピュータ自信を指す特別なホスト名  
-  IPアドレスに置き換えると127.0.0.1と同じ  
-  **8080**はポート番号   
![images](/images/postman6.png)  
👀 swagger
![images](/images/swagger2.png)

👀 AccountRest.java (Intellij IDEA)  
🌷 POSTは、@Consumesがいる
![images](/images/post1.png)
account_idとそれに対応するAccount情報（Account）がまとまったHashMapを作成し、accounts変数に代入
### **accountsの内容例 (HashMap)**

| **Key (`account_id`)** | **Value (`Account` オブジェクト)**                 |
|------------------------|------------------------------------                 |
|    "name"              |  Account(account_id="name", password="password")    |
|    "name2"             |  Account(account_id="name2", password="password!")` |

🌷  KeyはSet（集合）なので、かぶってはいけない

-  
-  
-  
## GET  
🌷 次に、Getを選択  
🌷 {{< color  yellowgreen "{ここに" >}}{{< color  green "accountId" >}}{{< color  yellowgreen "入れる。"}>}}  
🌷 Query Params に入力すると、勝手にパスも?password=passwordと入力される
🌷 Sendを押すと、JSON形式で返ってきている 
![images](/images/postman7.png) 
  
👀 Swagger  
![images](/images/swagger3.png)

👀 AccountRest.java  (Intellij IDEA)
![images](/images/get1.png)　　 

👀 Account.java  
![images](/images/aj.png)

以上でPostmanは終わり🎉  

4/5終わったよ🎊  何分かかかったかな？  休憩してね☕  

次はAndroidStudioでフロントエンドを書いていくよ！  
