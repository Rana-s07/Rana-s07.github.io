+++
author = "←この日付無視してね"
title = "Intellij IDEA  ⏰約20分 "
date = "2024-12-27"
description = "ここはどこに表示されているのだろう"

+++

--------------------------------------------------------

Intellij IDEA 環境  
・製品名: IntelliJ IDEA 2024.2.3（Ultimate Edition）  
・ビルド番号: IU-242.23339.11  
・Runtime（Java）: Java 21.0.4   
・Ultimate （学生および教職員向けの個人ライセンス）を使用

--------------------------------------------------------
## 🌞 **アプリ開発における構成**
🌷 新田研のプロジェクトでは、役割ごとに3つのpackage を作って開発を進めます。  
- **entities**  
データの形を定義する
- **repositories**  
データを保存・取得する
- **resources**  
外部との窓口（API）  
<br> 

🌷それぞれのpackageの中に、対応するJavaファイルを作成します。  
例）19th　シトラスプロジェクト↓
![images](/images/in.png) 

## 🌞 **MemoServerを作っていきましょう！**

- **IntelliJ IDEAのバージョン**  
この教材では IntelliJ IDEA 2024.1（Ultimate Edition） を使って説明します。以降の画像はこのバージョンを基準にしているため、別のバージョンを使用している場合、表示や操作手順が一部異なることがあるため注意してください。
 
- **他のプロジェクトを開いている場合**  
ハンバーガーメニュー（左上の4本線）をクリック→Fileをクリック→Close Projectをクリックします。
![images](/images/Intellij_close.png)

## 🖊 Project作ります  
1. NewProjectをクリック
![images](/images/Intellij_new.png)  
2. 設定を変更して、Nextをクリック
➀ 左の Spring Boot を選択  
② Name は 「MemoServer」に変更    
③ JDK は「openjdk-23 (java version"23.0.1")」を選択    
※openjdk-23 (java version"ここは全く同じにしなくてもOK")
![images](/images/Intellij_new2.png)
3. Webをクリック、Jersey を選択し、Createクリック
![images](/images/Intellij_new3.png)
4. Gradleのimportが終わるまで待ちましょう
![images](/images/Intellij_new4.png)
🌷 **Project「MemoServer」の作成完了！**

## 🖊 MemoServerに3つのPackageを作ります  
1. ➀MemoServer → ②src → ③main → ④java の順にクリック  
![images](/images/Intellij_package.png)
2. com.example.memoserver を右クリック 
3. ➀New → ②package の順にクリック  
![images](/images/Intellij_package2.png)
4. com.example.memoserverの続きに「entities」を入力してEnter  
![images](/images/Intellij_package3.png)
![images](/images/Intellij_package4.png)
🌷 **「entities package」の作成完了！**
5. 同様に「repositories」「resources」packageを作成して下さい
![images](/images/Intellij_package_final.png)
🌷 **「repositories package」「resources package」の作成完了！**

## 🖊 それぞれのPackageの中にJava Classを作ります
- entitiesの中には「Memo.java」を作ります  
1. entities を右クリック
2. ➀New → ②Java Class の順にクリック  
![images](/images/Intellij_javaclass.png)
3. 「Memo」を入力してEnter  
![images](/images/Intellij_javaclass2.png)
![images](/images/Intellij_javaclass3.png)
🌷 **「Memo.java」の作成完了!**
- repositoriesの中には「MemoRepository.java」を作ります  
- resourcesの中には「MemoResource.java」を作ります  
4. Memo.javaと同様に「MemoRepository.java」と「MemoResource.java」を作成してください  
![images](/images/Intellij_javaclass_final.png)
🌷 **「MemoRepository.java」「MemoResource.java」の作成完了!**

## 🖊 JerseyConfig.javaを作ります
-  **JerseyConfigとは...**  
Jersey に「どのクラスを API として使うか」を教えるための設定クラスです。
この設定がないと、@Path を付けたクラスは API として動きません。
- Pacakegeと同じ位置に作ります
1. com.example.memoserver を右クリック  
2. ➀New → ②Java Class の順にクリック  
![images](/images/Intellij_config.png)
3. 「JerseyConfig」を入力してEnter
![images](/images/Intellij_config2.png)
![images](/images/Intellij_config_final.png)
🌷 **「JerseyConfig.java」の作成完了!**


## 🖊 コードを書きます
- それぞれのコードをコピペしてください

**JerseyConfig ↓** 
```java
package com.example.memoserver;

import org.glassfish.jersey.server.ResourceConfig;
import org.springframework.stereotype.Component;

@Component
public class JerseyConfig extends ResourceConfig {

    public JerseyConfig() {
        packages("com.example.MemoServer.resources");
    }
}
```

**Memo ↓**
```java
package com.example.memoserver.entities;

public class Memo {
    private String text;

    public Memo() {}

    public Memo(String text) {
        this.text = text;
    }

    public String getText() { return text; }
    public void setText(String text) { this.text = text; }
}
```

**MemoRepository ↓**
```java
package com.example.memoserver.repositories;


import com.example.memoserver.entities.Memo;
import org.springframework.stereotype.Repository;

@Repository
public class MemoRepository {
    private Memo memo = new Memo("（ここにメモが表示されます）");

    public Memo getMemo() {
        return memo;
    }

    public void setMemo(Memo newMemo) {
        this.memo = newMemo;
    }
}
```

**Memo Resource ↓**
```java
package com.example.memoserver.resources;

import com.example.memoserver.entities.Memo;
import com.example.memoserver.repositories.MemoRepository;
import jakarta.ws.rs.*;
import jakarta.ws.rs.core.MediaType;
import jakarta.ws.rs.core.Response;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;


@Path("/memo")
@Component
public class MemoResource {

    private final MemoRepository memoRepository;

    @Autowired
    public MemoResource(MemoRepository memoRepository) {
        this.memoRepository = memoRepository;
    }

    //メモの取得
    @GET
    @Produces(MediaType.APPLICATION_JSON)
    public Memo getMemo() {
        return memoRepository.getMemo();
    }

    // メモの更新
    @PUT
    @Consumes(MediaType.APPLICATION_FORM_URLENCODED)
    @Produces(MediaType.APPLICATION_JSON)
    public void updateMemo(@FormParam("text") String text) {
        if (text == null || text.isEmpty()) {
            Response response = Response.status(Response.Status.BAD_REQUEST)
                    .entity("メモの内容を入力してください")
                    .build();
            throw new WebApplicationException(response);
        }

        memoRepository.setMemo(new Memo(text));
    }
}
```

## 🖊 実行してみましょう
- 実行する前にGradleを更新します  
実行前にGradleを更新するのは、プロジェクトを正しく動かすための準備を整えるためです。Gradleが古いままだと、コードが正しくてもエラーになります。
1. 象のマーク🐘をクリック  
2. 更新マーク🔄をクリック
![images](/images/Intellij_gradle.png)
🌷 **Gradleの更新完了**
<br>
- 実行します
1. 実行ボタンをクリック
![images](/images/Intellij_run.png)
2. 画像の用にspringが出たら成功
![images](/images/Intellij_final.png)
以上でIntellij ideaは終わり🎉  

3/5終わったよ🎊  何分かかかったかな？  休憩してね☕

次はこのコードが動いているかPostmanで試していくよ！