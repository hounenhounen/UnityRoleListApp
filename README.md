# 【Unity】ユーザーのロール情報を一覧で取得する
![画像1](/readme-img/Top.png)

## 概要
* 簡単な操作ですぐに [ニフティクラウドmobile backend](http://mb.cloud.nifty.com/)の機能を体験いただけます★☆
* [ニフティクラウドmobile backend](http://mb.cloud.nifty.com/)の『会員管理機能』を利用したサンプルプロジェクトです
* できること
 * Loginsigninシーンでユーザーのログイン、サインインができます
    ![概要1](/readme-img/demoLoginSignIn.png)

 * LogOutシーンでロール機能を使い会員をグルーピングできます。また、ログイン中のユーザーの会員情報にロールをリレーションで関連付けられます
    ![概要2](/readme-img/addRoleRelation.png)

 * ログインをしている会員から、ロールの一覧を取得できます
    ![概要3](/readme-img/viewRoleList.png)
    


## ニフティクラウドmobile backendって何？？
スマートフォンアプリのバックエンド機能（プッシュ通知・データストア・会員管理・ファイルストア・SNS連携・位置情報検索・スクリプト）が**開発不要**、しかも基本**無料**(注1)で使えるクラウドサービス！今回はデータストアを体験します

注1：詳しくは[こちら](http://mb.cloud.nifty.com/price.htm)をご覧ください

![画像2](https://github.com/natsumo/SwiftLoginApp/blob/master/readme-img/002.png)

## 動作環境
* Mac OS X 10.11.5(EI Capitan)
* Unity ver. 5.2.1f1
* MonoDevelop-Unity ver. 4.0.1

※上記内容で動作確認をしています。


## 使い方手順
### 1. [ニフティクラウドmobile backend](http://mb.cloud.nifty.com/)の会員登録とログイン→アプリ作成

* 上記リンクから会員登録（無料）をします。登録ができたらログインをすると下図のように「アプリの新規作成」画面が出るのでアプリを作成します

![画像3](https://github.com/natsumo/SwiftLoginApp/blob/master/readme-img/003.png)

* アプリ作成されると下図のような画面になります
* この２種類のAPIキー（アプリケーションキーとクライアントキー）はXcodeで作成するiOSアプリに[ニフティクラウドmobile backend](http://mb.cloud.nifty.com/)を紐付けるために使用します

![画像4](https://github.com/natsumo/SwiftLoginApp/blob/master/readme-img/004.png)

* 動作確認後に会員情報が保存される場所も確認しておきましょう

![画像5](https://github.com/natsumo/SwiftLoginApp/blob/master/readme-img/005.png)

### 2. [GitHub](https://github.com/hounenhounen/UnityRoleListApp)からサンプルプロジェクトのダウンロード

* この画面([GitHub](https://github.com/hounenhounen/UnityRoleListApp))の![画像10](https://github.com/natsumo/SwiftLoginApp/blob/master/readme-img/010.png)ボタンをクリックし、さらに![画像11](https://github.com/natsumo/SwiftLoginApp/blob/master/readme-img/011.PNG)ボタンをクリックしてサンプルプロジェクトをMacにダウンロードします

### 3. Unityでアプリを起動

* ダウンロードしたフォルダを解凍し、Unityから開いてください。その後、Loginsigninシーンを開いてください。


### 4. APIキーの設定

* Loginsigninシーンの`NCMBSettings`を編集します
* 先程[ニフティクラウドmobile backend](http://mb.cloud.nifty.com/)のダッシュボード上で確認したAPIキーを貼り付けます

![画像07](https://github.com/hounenhounen/UnityLoginApp/blob/master/readme-img/ApiKey.png)

* それぞれ`YOUR_NCMB_APPLICATION_KEY`と`YOUR_NCMB_CLIENT_KEY`の部分を書き換えます
 * このとき、ダブルクォーテーション（`"`）を消さないように注意してください！
* 書き換え終わったら`command + s`キーで保存をします

### 5. 動作確認
* Unity画面で上部真ん中の実行ボタン（さんかくの再生マーク）をクリックします
* シミュレーターが起動したら、Login&SignIn画面が表示されます
* 初回は__`SignIn`__ ボタンをクリックして、会員登録を行います

![画像14](/readme-img/LoginSignIn.png)

* ２回目以降は`UserName`と`Password`を２つ入力して__`Login`__ ボタンをタップします
* 会員登録が成功するとログインされ、下記画面が表示されます
 * このときmBaaS上に会員情報が作成されます！
 * ログインに失敗した場合は画面にエラー内容が表示されます
 * 万が一エラーが発生した場合は、[こちら](http://mb.cloud.nifty.com/doc/current/rest/common/error.html)よりエラー内容を確認いただけます

![画像15](/readme-img/LogoutRoleView.png)

* InputFiealdに「文字列」を入力して__`AddRole`__ボタンをタップすると、ログイン中のユーザーを「文字列」の名前のロールに追加されます
* __`SeeBlongRole`__ボタンをタップすると、ログイン中のユーザーの所属ロール情報を一覧で見れます
     ![概要3](/readme-img/viewRoleList.png)
* __`Logout`__ ボタンをタップするとログアウトし、元の画面に戻ります
* 登録された会員情報を使ってLogin画面からログインが可能です（操作は同様です）

-----

* 保存に成功したら、[ニフティクラウドmobile backend](http://mb.cloud.nifty.com/)のダッシュボードから確認してみましょう！


## 解説
サンプルプロジェクトに実装済みの内容のご紹介

#### SDKのインポートと初期設定
* ニフティクラウドmobile backend の[ドキュメント（クイックスタート）](http://mb.cloud.nifty.com/doc/current/introduction/quickstart_unity.html)をUnity版に書き換えたドキュメントをご用意していますので、ご活用ください

#### Login・SignIn・LogOutについて
下記のプロジェクトをそのまま使いましたのでそちらをご参照ください
https://github.com/hounenhounen/UnityLoginApp


####ロジック
* `Role.cs`にロジックを書いています
* まず、ロールの追加部分について記載します。コメントアウト部分に各所の説明があるのでそちらをご参考にしてください

`Role.cs.cs`

```csharp
public void AddRole(){
    NCMBUser currentUser;
    currentUser = NCMBUser.CurrentUser;
    //InputFiealdに記入されたRoleNameをもとにロールクラスを検索
    NCMBRole.GetQuery ().WhereEqualTo ("roleName", RoleName.text).FindAsync ((roleList, error) => {
        NCMBRole role = roleList.FirstOrDefault ();
        if (role != null) {
            //既存のロールと一致したら、ユーザーを既存ロールに追加する
            role.Users.Add (currentUser);
            role.SaveAsync ((NCMBException addRoleError) => {
                if(addRoleError != null){
                    UnityEngine.Debug.Log ("role追加に失敗: " + addRoleError.ErrorMessage);
                }else{
                    UnityEngine.Debug.Log ("roleへの追加に成功");
                    //ロールの情報を現在ログイン中のユーザーに関連づける
                    NCMBRelation<NCMBObject> relation = currentUser.GetRelation<NCMBObject> ("Role");
                    relation.Add(role);
                    currentUser.SaveAsync();
                }
            });

        }else{
            //既存ロールと一致しなければ、ロールを新たに作成しそのロールに追加する
            NCMBRole newRole = new NCMBRole (RoleName.text);
            newRole.Users.Add (currentUser);
            newRole.SaveAsync ((NCMBException newRoleError) => {
                if(newRoleError != null){
                    UnityEngine.Debug.Log ("role新規登録に失敗: " + newRoleError.ErrorMessage);
                }else{
                    UnityEngine.Debug.Log ("role新規登録に成功");
                    //ロールの情報を現在ログイン中のユーザーに関連づける
                    NCMBRelation<NCMBObject> relation = currentUser.GetRelation<NCMBObject> ("Role");
                    relation.Add(newRole);
                    currentUser.SaveAsync();
                }
            });
        }
    });
}
```
* 次に、ロールの一覧取得について記載します。コメントアウト部分に各所の説明があるのでそちらをご参考にしてください

```csharp
//現在ログイン中のユーザーに関連付いているロール情報を取得する
public void seeBelongRole(){
    NCMBUser currentUser;
    currentUser = NCMBUser.CurrentUser;
    currentUser.FetchAsync ((NCMBException e) => {
        if (e != null) {
            //エラー処理
            UnityEngine.Debug.Log ("ユーザー取得に失敗: " + e.ErrorMessage);
        } else {
            //ユーザーのリレーション取得
            NCMBRelation<NCMBRole> relation = currentUser.GetRelation<NCMBRole> ("Role");
            NCMBQuery<NCMBRole> query = relation.GetQuery ();

            //リレーション先検索
            query.FindAsync ((List<NCMBRole> roleList,NCMBException findRoleError) => {
                if (findRoleError != null) {
                    //エラー処理
                    UnityEngine.Debug.Log ("role取得に失敗: " + findRoleError.ErrorMessage);
                } else {
                    //成功時の処理
                    UnityEngine.Debug.Log ("role取得に成功");
                    foreach (NCMBRole role in roleList) {
                        //uGuiに表示させる
                        RoleText.text += role.Name;
                        RoleText.text += "\n";
                        Debug.Log( role.Name );
                        Debug.Log ("objectId : " + role.ObjectId);
                    }
                }
            });
        }
    });
}
```


## 参考
* ニフティクラウドmobile backend の[ドキュメント（会員管理）](http://mb.cloud.nifty.com/doc/current/user/basic_usage_unity.html)
