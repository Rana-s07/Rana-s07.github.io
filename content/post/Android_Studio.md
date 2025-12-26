+++
author = "←この日付無視してね"
title = "AndroidStudio ⏰約100分"
date = "2019-03-05"
description = ""
+++

## 🌞 **フロンドエンド書いていくよ！**
🌷 スマホやPC上で動くプログラムをフロントエンドといいます  
🌷 ここでは、アンドロイド向けのアプリを開発するので、Android Studio を使います  
🌷 Android Studio は IntelliJ IDEA と同じ会社が開発している統合開発環境なので、使い方は変わりません。言語も同じ Java で書いていきます  
🌷 まず、Android Studio のプロジェクトを作成していきましょう   

## 🖊手順を説明します🐘 
🌷 NewProjectを押します  
![images](/images/app1.png)  

-  
-  
-  
🌷 Empty Views Activity を押します  
![images](/images/app2.png)  

-  
-  
-  
🌷 Nameにタイトルを入力 （LesonServer）と入力 
🌷 Build configuration languageを Groovy DSL にする  
🌷 Minimum SDKを API30 にする  
![images](/images/app3.png)  

-  
-  
-   
🌷 左上がProjectとなっていますが、準備中なので、「Android」と表示されるまで待ちます  
![images](/images/app4.png)

-  
-  
-  
🌷 今、右で表示されている MainActivity.java のファイルの位置を確認します  
🌷 ＞をクリックしていきます
![images](/images/app5.png)

-  
-  
-  
🌷 Androidでは画面のことをActivityといいます  
🌷 １つの画面ごとに [画面名]Activity.java と、 activity_[画面名].xml の2つを作ります   
🌷 プロジェクトツールウィンドウ（左の部分）を見ると、app/java/com/example/lessonに MainActivity.java があることが分かります。   
🌷 次に、activity_main.xml を押しましょう

![images](/images/app6.png)

-  
-  
-  
🌷このxmlでは、一つの画面のレイアウトをいじります。（後で戻ってくるので理解はざっくりでok）
![images](/images/app7.png)

-  
-  
-  
🌷 プロジェクト全体をコンパイルすることをビルドといいます  
（コンパイルとは、コードを機械言語に変換することだが、javaの場合はコードと機械言語の中間に値する中間言語に変換する）  
🌷 🐘build.gradleにはビルドの設定と、使用するライブラリが書かれています  
🌷 今回は通信をするためにretrofit2というライブラリを使うので、これから設定していきます  
🌷 それでは、build.gradle をあけます  
![images](/images/app8.png)

-  
-  
-  
🌷 retrofitをダウンロードできるように以下を追加します  
🌷 エラーが出ますが、右上の 🐘を押すとビルドされ、エラーは消えます
![images](/images/app55.png)

-  
-  
-  
🌷 次に MainActivity の名前を SignUpActivity に変えます  
🌷 figmaでは３つの画面を作りましたね   
🌷 後ほど、SettingsActivity.java や AccountListActivity.java も作成します
![images](/images/app56.png)  

-  
-  
-  
🌷  MainActivityを右クリックして、Refactorを押し、Renameを押します
![images](/images/app11.png)  

-  
-  
-  
🌷 すると以下の画面が出てくるので、figmaに設定したのと同じ名前（にしたら分かりやすい）に変更します。  
～単語の先頭は大文字にするのが一般的～  
![images](/images/app12.png)  

-  
-  
-  
🌷 同じように、レイアウトの名前も分かりやすいように変えます
![images](/images/app13.png)  

-  
-  
-  
🌷mainの部分をsign_upなどと分かりやすいように変えます。  
～単語の先頭は小文字にし、大文字の前に_を入れるのが一般的（画像は_が入ってないけど無視してください）～  
![images](/images/app14.png)  

-  
-  
-  
🌷 次に、com/example/lessonの下にPackageをviews,models,restの3つ作ります   
🌷 理由は、後でファイルを探すときに困るので、整理するために作っておきます  
![images](/images/app15.png)

-  
-  
-  
🌷 まず、viewsパッケージを作ります
![images](/images/app16.png)

-  
-  
-  
🌷viewsというPackageにSignUpActivityをドラック＆ドロップする（viewの中に入れる）
![images](/images/app17.png)  

-  
-  
-  
🌷 Refactorを押す  
![images](/images/app18.png)  

-  
-  
-  
🌷 次にviewsと同じ階層にmodelsパッケージを作りたいです  
🌷 com.example.lesson.viewsとあるが、お構いなしに右クリックを押す
![images](/images/app20.png)

-  
-  
-  
🌷 com.example.lesson.viewsの、viewsを消して、modelsと書き換えることで、同じ階層にPackageが作られます
![images](/images/app21.png)

-  
-  
-  
🌷 modelパッケージの中にはAccount.javaを作ります
![images](/images/app23.png)

-  
-  
-  
🌷 Accountと入力
![images](/images/app24.png)

-  
-  
-  
🌷 Account.javaには、Intellijに書かれたAccount.javaのコードをそのまま貼り付ける  
🌷 1行目だけ消し、以下のように赤線のところにマウスをかざし、青色のメッセージをおす  
![images](/images/app94.png)
🌷 次にviewsやmodelsと同じ階層にrestパッケージを作りたいです。  
🌷 com.example.lessonを右クリックする。
![images](/images/app25.png)

-  
-  
-  
🌷 restと入力
![images](/images/app26.png)

-  
-  
-  
🌷 restパッケージの中にはAccountRest.javaを作る
![images](/images/app27.png)

-  
-  
-  
🌷 AccountRestと入力し、Interfaceを選択する
![images](/images/app28.png)

-  
-  
-    
🌷 作られました(o^―^o)ﾆｺ
![images](/images/app29.png)

-  
-  
-  
🌷 ここでは、IntellijのAccountRestと対応するように書いていく  
🌷 IntelijではFormParamと書かれているがAndroidStudioではFieldと書く
![images](/images/app85.png)
```java
package com.example.lessonClient.rest;

import com.example.lessonClient.models.Account;
import java.util.Set;
import retrofit2.Call;
import retrofit2.http.Field;
import retrofit2.http.FormUrlEncoded;
import retrofit2.http.GET;
import retrofit2.http.POST;
import retrofit2.http.PUT;
import retrofit2.http.Path;
import retrofit2.http.Query;

public interface AccountsRest {
  // 全体のアカウント一覧
  @GET("accounts")
  Call<Set<String>> getAccounts(
  );

  // サインアップ
  @FormUrlEncoded
  @POST("accounts")
  Call<Void> signup(
      @Field("account_id") String account_id,
      @Field("password") String password
  );

  //指定されたアカウント情報を返す
  @GET("accounts/{account_id}")
  Call<Account> getAccountInfo(
      @Path("account_id") String account_id,
      @Query("password") String password
  );

  // パスワード変更
  @FormUrlEncoded
  @PUT("accounts/{account_id}/password")
  Call<Void> changePW(
      @Path("account_id") String account_id,
      @Field("new_password") String new_password,
      @Field("old_password") String old_password
  );

}
```

-  
-  
-  
🌷 activity.sign_up_xmlで画面が小さいなぁって思ったら、ctrl押しながらカーソルころころすると、
![images](/images/app30.png)

-  
-  
-  
🌷 アップできます(o^―^o)ﾆｺ
![images](/images/app31.png)

-  
-  
-  
🌷 左側のButtonやTextBoxを引っ張ってきて配置できるので、  
![images](/images/app32.png)

-  
-  
-   
🌷 figma参考にしながらこのような画面を作る
![images](/images/app33.png)

-  
-  
-  
🌷 Buttonを選択しているとき、右のtextでRegisterと打ち、Enterを押すと、  
![images](/images/app34.png)

-  
-  
-  
🌷 ボタンにはRegisterと表示される  
🌷 右のidにはRegisterbuttonなどと入力しておく。（後で使う）
![images](/images/app35.png)

-  
-  
-  
🌷 次に、ボタンやテキストは、選択したときに出てくる青い点を縦横右左に引っ張って、端にくっつける
![images](/images/app36.png)

-  
-  
-  
🌷 くっつけた状態で配置したい位置に配置する  
![images](/images/app37.png)

-  
-  
-  
🌷 テキストボックスも同じようにtextをSignUpに変え、idもSignUpなどとし、Refactorを押す  
![images](/images/app38.png)  

-  
-  
-  
🌷 このようになっていたらOK
![images](/images/app39.png) 

-  
-  
-  
🌷 acitvity_sign_up.xmlの、Codeの方を選ぶと、このようなコードが書かれている  
🌷 以下の部分でSignUpのテキストのことが書かれている  
🌷 以下のように android:textAlignment="center"を入れると、右でも左でもなく真ん中に来てくれる  
![images](/images/app40.png)  

-  
-  
-  
🌷 android:textColor="#000000"  色が黒にできる  
🌷 android:textSize="38sp"  テキストのサイズを調節できる  
🌷 android:textStyle="bold"  文字が太くなる
![images](/images/app42.png)

-  
-  
-  
🌷 Designに戻るとこんな風に表示される
![images](/images/app43.png)

-  
-  
-  
🌷 ここはmatch_parentにする
![images](/images/app44.png)

-  
-  
-  
🌷 次に入力画面を作りたいとき、Text の Plain Text を画面に引っ張ってくる
![images](/images/app45.png)  

-  
-  
-  
🌷 android:hint=" Username" 薄く入力内容のヒントを書くときこのように書く  
🌷 textは消す  
![images](/images/app48.png)  

-  
-  
-  
🌷 UsernameとPasswordそれぞれにidを設定し、壁に固定して、以下のようになるとOK
![images](/images/app50.png)

-  
-  
-  
🌷 空のテキストボックスも作る。これはエラーを表示させる場所。idも設定する
![images](/images/app53.png)  

-  
-  
-  
🌷 次に、SettingActivityを作りたい  
![images](/images/app33.png)

-  
-  
-   
🌷 SignUpActivityを選択した状態で、File → New Activity → Empty Views Activityを押す  
🌷 この作り方だと、javaファイルだけでなく、xmlファイルも同時に作ってくれる👏	　　
![images](/images/app57.png)  

-  
-  
-  
🌷 同時にAccountsListActivityも作る  
🌷 以下のようになれば正解  
![images](/images/app81.png)  

-  
-  
-  
🌷 activity_settings.xmlをfigmaを見ながら作る
![images](/images/app33.png)

-  
-  
-  
🌷 パスワード変更のボタンを忘れていたので少しレイアウトが変わりました笑  
🌷 こちらを見よう見まねで作ってみましょう  
![images](/images/app86.png)  

-  
-  
-  
🌷 次に、SignUpActivityに戻り、registerボタンを押すとSettings画面に遷移するようにする  
🌷 最初はこのようになっているはずだが、少なかったら以下のようにする
![images](/images/app64.png)  

-  
-  
-  
🌷 以下のコードを追加する   
![images](/images/app65.png) 


🌷 findViewByIdメソッド：  
XMLレイアウトファイルで定義されたボタンのIDを引数に渡してボタンを取得します  

🌷 (Button)：  
取得したビュー（View オブジェクト）を Button 型にキャストする必要があります。
これは、findViewById が View 型を返すためです。

🌷 button_register：  
取得したボタンを操作するために button_register という名前の変数に代入しています。
この変数を使ってボタンに機能を追加します。

-  
-  
-   
```java
button_register.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View view) {
        // LoginActivity に遷移するための Intent を作成
        Intent intent = new Intent(SignUpActivity.this, SettingsActivity.class);
        startActivity(intent); // 遷移を実行
    }
});
```

🌷 button_register.setOnClickListenerメソッド:

このメソッドは、ボタンがクリックされたときに実行する処理（クリックリスナー）を設定します。

🌷 @Override:

onClick メソッドをオーバーライドしています。  
@Override と書くことで、「元々用意された『onClick』の動きを上書きして自分で作り直してますよ！」とプログラムに伝える。そうすることで、onClickのスペルミスによって新しいメソッドが作られてしまうことを防げる  

🌷 onClick(View view):

ボタンがクリックされるとこのメソッドが呼び出されます。
引数 view は、クリックされたビュー（この場合は button_register）を指します。

🌷 Intent:

Intent は、Android でアクティビティ（画面）間の通信を行う仕組みです。このコードでは、現在のアクティビティ（SignUpActivity）から別のアクティビティ（SettingsActivity）に遷移するための指示を Intent を使って作成しています


-  
-  
-  
🌷 赤くなっている部分をなくすために以下のようにimport文を追加する

![images](/images/app66.png)   
![images](/images/app67.png)  

-  
-  
-  
🌷 動かす仮想マシーンを選択する 
![images](/images/app88.png) 
🌷 これで実行▷を押し、ユーザーネームなどは触らず、Registerボタンの押し、Settings画面に遷移するとOK
![images](/images/app82.png)

-  
-  
-   
🌷 次に、サーバー（intellij）と通信できるようにするコードを追加し、SignUp時に、account_idとpasswordをサーバに保存してもらえるようにする   
🌷 サーバーと通信を行うため、Android Studio を実行するときには、Intellijを先に実行させておく必要があります   
🌷 まず、SignUpActivity.java の onCreate() メソッドに以下を書く
![images](/images/app83.png)
🌷 AccountsRest accountsRest = retrofit.create(AccountsRest.class);  
🌷 この行を書くことで   
🌷 accountsRest を使うと、サーバーにデータを送る、サーバーからデータを受け取るといった通信処理を簡単に書けるようになります。  

-  
-  
-  
🌷 次に以下を書く  
🌷 ボタンがクリックされたときに、editidという変数は場所を示す情報が入っており、getTextを使ってaccount_idという変数にはidが取得される  
🌷 パスワードも同様にpasswordという変数にidが取得される  


![images](/images/app84.png)
🌷 Call<Void> call = accountsRest.signup(account_id, password); は、  
🌷 AccountRestのCall<void> signupの書き方とそろえる  
🌷 サーバーに「account_id と password を使って、新しいアカウントを作成してください！」とお願いする準備をしています。  

-  
-  
-  
↓コピー用  
```java
 call.enqueue(new Callback<Void>() {  // call.enqueueはリクエストをサーバーに送るよ！結果が返ってきたらこれをやってね」という動きを設定します。
          @Override  // 元々用意された『onResponse』の動きを上書きして自分で作り直してますよ！」とプログラムに伝える。
          public void onResponse(Call<Void> call, Response<Void> response) {  // サーバーから返事が返ってきた場合に呼ばれる。
            if (response.isSuccessful()) {  // さらに返事が「成功かどうか」
              Intent intent = new Intent(SignUpActivity.this, SettingsActivity.class);  // SettingsActivity に遷移
              intent.putExtra("account_id", account_id);  // account_idを乗せて次の画面に遷移する
              startActivity(intent);  // intentを使って画面遷移
            }
          }

          @Override
          public void onFailure(Call<Void> call, Throwable t) { // サーバーから返事が返ってこなかった場合に呼ばれる。
            System.out.println("!!!");  // コンソールに!!!と表示（Android画面ではない）
          }
        });
```
 

🌷 以上のコードを書くと、サインアップができるようになったので実行を押す  

-  
-  
-  
🌷 次に、Setting画面に現在のパスワードと新しいパスワードを正しく入力すると変更されるように以下の場所にコードを書いていきます  
![images](/images/app87.png) 
🌷 以下のコードをSettingsActivity.java の onCreateメソッド内に書いてください  
🌷 ほとんどSignUpActivityの応用なので、なにが書いてあるか読んでみましょう  

```java
    String str_account_id = getIntent().getStringExtra("account_id");
    ((TextView) findViewById(R.id.account_id)).setText(str_account_id);

    //通信の初期化
    Retrofit retrofit = new Retrofit.Builder()
        .baseUrl("http://10.0.2.2:8080/")
        .addConverterFactory(JacksonConverterFactory.create())
        .build();
    AccountsRest accountsRest = retrofit.create(AccountsRest.class);

    // listボタンを押してlist画面に遷移
    Button button_list = (Button) findViewById(R.id.List);
    button_list.setOnClickListener(new OnClickListener() {
      @Override
      public void onClick(View view) {
        Intent intent = new Intent(SettingsActivity.this, AccountListActivity.class);
        startActivity(intent);
      }
    });

    // changeボタンを押してメッセージ表示
    Button button_change = (Button) findViewById(R.id.change);

    button_change.setOnClickListener(new OnClickListener() {
      @Override
      public void onClick(View view) {

        EditText pw = (EditText) findViewById(R.id.password);
        String oldpass = pw.getText().toString().trim();
        EditText newpw = (EditText) findViewById(R.id.newpassword);
        String newpass = newpw.getText().toString().trim();


        Call<Void> call = accountsRest.changePW(str_account_id, newpass, oldpass);
        call.enqueue(new Callback<Void>() {

          @Override
          public void onResponse(Call<Void> call, Response<Void> response) {
            if (response.isSuccessful()) {
              ((TextView) findViewById(R.id.message)).setText("パスワードが変更されました");
            } else {
              ((TextView) findViewById(R.id.message)).setText("パスワードが違います");
            }
          }

          @Override
          public void onFailure(Call<Void> call, Throwable t) {
            ((TextView) findViewById(R.id.message)).setText("Failure");
          }
        });


      }


    });
```

-  
-  
-  
🌷 AccountListActivityにも以下をonCreate内に追加します
 
```java
//通信の初期化
    Retrofit retrofit = new Retrofit.Builder()
        .baseUrl("http://10.0.2.2:8080/")
        .addConverterFactory(JacksonConverterFactory.create())
        .build();
    AccountsRest accountsRest = retrofit.create(AccountsRest.class);
    Call<Set<String>> call = accountsRest.getAccounts();
    call.enqueue(new Callback<Set<String>>() {

      @Override
      public void onResponse(Call<Set<String>> call, Response<Set<String>> response) {
        ((TextView) findViewById(R.id.accounts)).setText(response.body().toString());
      }

      @Override
      public void onFailure(Call<Set<String>> call, Throwable t) {
        ((TextView) findViewById(R.id.accounts)).setText("通信失敗");
      }
    });

```
🌷 実行しましょう  
 ![images](/images/app89.png) 
 ![images](/images/app90.png) 
 ![images](/images/app91.png) 
 ![images](/images/app92.png)
🌷 私はaaaの前にも11というアカウント名で実行していたので二つのアカウントidが出力されました   
 ![images](/images/app93.png)  


🌷 課題は以上です🎊  何分かかかったかな？  

🌷 お疲れ様！  


{{< css.inline >}}

<style>
.emojify {
	font-family: Apple Color Emoji, Segoe UI Emoji, NotoColorEmoji, Segoe UI Symbol, Android Emoji, EmojiSymbols;
	font-size: 2rem;
	vertical-align: middle;
}
@media screen and (max-width:650px) {
  .nowrap {
    display: block;
    margin: 25px 0;
  }
}
</style>

{{< /css.inline >}}
