---
lab:
    title: '4 - Azure AD で SMS を使用した MFA を実装する'
    learning path: '4'
    module: 'モジュール 3 - Azure AD で SMS を使用した MFA を実装する'
---

# ラボ 4: Azure AD で SMS を使用した MFA を実装する

## ラボ シナリオ

あなたの会社でユーザーアカウントのセキュリティ向上のため、SMSを使用したMFAを実装します。



#### 推定時間: 20分

## タスク1 - 多要素認証の設定を確認する

1. 「[Azure Active Directory 管理センター](https://aad.portal.azure.com/)」へサインインします。

   > 注:XXXXはご自身のアカウント番号を入力してください。
   >
   > 注:「アカウントの保護にご協力ください」と表示された場合は「今はしない」を選択してください。

   | 項目                | 値                              |
   | ------------------- | ------------------------------- |
   | メール、電話、Skype | `admin@ctcXXXX.onmicrosoft.com` |
   | パスワード          | Pa55w.rd1234                    |

   

2. 画面左ツリーの「すべてのサービス」をクリックします。

   ![module04-01](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-01.BMP)

   

3. 「すべてのサービス」画面が表示されます。「セキュリティ」をクリックし、さらに「多要素認証」をクリックします。

   ![module04-02](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-02.BMP)

   

4. 「多要素認証 | はじめに」画面が表示されます。「クラウドベースの多要素認証の追加設定」をクリックします。

   ![module04-03](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-03.BMP)

   

5. 別タブが開き「多要素認証」画面が表示されます。設定できる項目を確認し、タブを閉じます。

   > 注：ここでは設定変更は行いません。設定できる項目を見ていただきました。

   ![module04-04](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-04.BMP)

   

6. 画面左上の「Azure Active Directory 管理センター」というロゴをクリックし、ダッシュボード画面に戻ります。

   ![module04-05](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-05.BMP)

   

## タスク2 - MFAの条件付きアクセスのルールを設定する

1. 画面左ツリーの「Azure Active Directory」をクリックし、さらに「セキュリティ」をクリックします。

   ![module04-06](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-06.BMP)

   

2. 「セキュリティ | はじめに」画面が表示されます。画面左ツリーの「条件付きアクセス」をクリックします。

   ![module04-07](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-07.BMP)

   

   

3. 「条件付きアクセス | ポリシー」画面が表示されます。「+新しいポリシー」をクリックします。

   ![module04-08](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-08.BMP)

   

   

4. 「新規」画面が表示されます。

   ![module04-09](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-09.BMP)

   

5. 名前に「Offce365_MFA」と入力します。

   ![module04-13](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-13.BMP)

   

6. 「ユーザーまたはワークロード ID」にて、次の情報を使用して「作成」をクリックします。

   | 項目                               | 値                           |
   | ---------------------------------- | ---------------------------- |
   | このポリシーは何に適用されますか？ | ユーザーとグループ           |
   | 対象                               | ユーザーとグループの選択     |
   | -                                  | ユーザーとグループにチェック |
   | 選択                               | Miriam Graham                |

   ![module04-10](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-10.BMP)

   

7. 「クラウド アプリまたは操作」にて、次の情報を使用して「作成」をクリックします。

   | 項目                                   | 値              |
   | -------------------------------------- | --------------- |
   | このポリシーが適用される対象を選択する | クラウド アプリ |
   | 対象                                   | アプリを選択    |
   | 選択                                   | Office 365      |

   ![module04-11](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-11.BMP)

   

8. 「許可」にて、次の情報を使用して「作成」をクリックします。

   | 項目                 | 値               |
   | -------------------- | ---------------- |
   | 多要素認証を要求する | チェックを入れる |

   ![module04-12](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-12.BMP)

   

9. 「レポートの有効化」を「オン」に変更し、「作成」をクリックします。

   ![module04-14](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-14.BMP)

   

10. 「条件付きアクセス | ポリシー」画面に遷移します。作成したポリシーが一覧に表示されたことを確認してください。

    ![module04-15](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-15.BMP)

    

    

## タスク3 - MFAに必要な電話番号をユーザープロファイルに登録する

1. 画面左ツリーの「Azure Active Directory」をクリックし、さらに「ユーザー」をクリックします。

2. 「ユーザー」画面が表示されます。「Miriam Graham」をクリックします。

   ![module04-16](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-16.BMP)

   

3. 画面左ツリーの「認証方法」をクリックします。

4. ![module04-17](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-17.BMP)

   

5. 「Miriam Graham | 認証方法」画面が表示されます。「電話」の欄にあなたの携帯電話番号を入力し、「保存をクリックします。

   > 注：記入例「+81 08012345678」です。「81」と「080」の間は半角空白です。
   >
   > 注：この後の演習でSMSを受信するために使用します。

   ![module04-18](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-18.BMP)

   

   

## タスク4 - Office 365 にアクセスし、MFAを検証する

1. 新しい InPrivate ブラウザー ウィンドウを開きます。

   > 注:演習の中ではWebブラウザの機能を使って別セッションでサインインします。
   >
   > 　 どのWebブラウザもウィンドウ右上の設定ボタンから表示することが可能です。
   >
   > 　 Microsoft Edgeでは「InPrivate」ウィンドウ
   >
   > 　 Google Chromeでは「シークレット」ウィンドウ
   >
   > 　 Mozilla Fire Foxでは「プライベート」ウィンドウ

2. Miriam Graham として、[Offcie365](https://www.office.com)へアクセスします。

   > 注:XXXXはご自身のアカウント番号を入力してください。

   | 項目                | 値                                |
   | ------------------- | --------------------------------- |
   | メール、電話、Skype | `MiriamG@ctcXXXX.onmicrosoft.com` |
   | パスワード          | Pa55w.rd123                       |

3. パスワードを更新します。

   > 注：Miriamを使用して初回サインインのため、パスワード更新が求められます。
   >
   > 　　MFAの設定とは関係ありません。

   | 設定             | 値           |
   | ---------------- | ------------ |
   | 現在のパスワード | Pa55w.rd123  |
   | 新しいパスワード | Pa55w.rd1234 |
   | パスワードの確認 | Pa55w.rd1234 |

   

4. パスワード認証後に「ID を確認する」画面が表示されます。「SMSを送信」をクリックします。

   ![module04-19](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-19.BMP)

   

5. 登録した携帯電話に届いたSMSの番号を入力します。

   ![module04-20](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-20.BMP)

   

6. 「サインインの状態を維持しますか?」と表示される場合があります。「いいえ」を選択してください。

   > 注:誤って「はい」を選択しても、演習に影響はありません。
   >
   > 注:「アカウントの保護にご協力ください」と表示された場合は、「今はしない」をクリックしてください。

   

7. Office 365にサインインできました。

   ![module04-21](C:\Users\otokita\Documents\Azure-Active-Directory-for-Beginners\media\module04-21.BMP)

   

   

###### Module4 Lab は以上です。お疲れ様でした。
