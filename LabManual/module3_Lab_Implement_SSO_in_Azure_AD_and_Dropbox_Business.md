---
lab:
    title: '3 - Azure AD と クラウドアプリで SSO を実装する'
    learning path: '3'
    module: 'モジュール 3 - Azure AD と クラウドアプリで SSO を実装する'
---

# ラボ 3: Azure AD と クラウドアプリで SSO を実装する

## ラボ シナリオ

このラボでは以下のタスクを実施していただきます。

　**タスク1 - Dropbox Businessを利用登録する**

　**タスク2 - Azure AD でエンタープライズアプリケーションを登録する**

　**タスク3 - Dropbox Businessでシングルサインオンを構成する**

　**タスク4 - My Apps からDropbox Business にSSOを検証する**

> 参考：本ラボで「Dropbox Business」を採用した理由
>
> 　　　様々なクラウドアプリは無料版や試用版でも「クレジットカード」の登録が必要になります。
>
> 　　　「Dropbox Business」の試用版はクレジットカード登録不要で利用できるため、採用しています。



#### 推定時間: 30分

## タスク1 - Dropbox Businessを利用登録する

このタスクでは、「Dropbox Business」の利用登録を行います。登録にはメールアドレスが必要のため、Outlookを使用します。



1. https://outlook.live.com/owa/ へサインインします。

   > 注:XXXXはご自身のアカウント番号を入力してください。
   >
   > 注:「アカウントの保護にご協力ください」と表示された場合は「今はしない」を選択してください。

   | 項目                | 値                              |
   | ------------------- | ------------------------------- |
   | メール、電話、Skype | `admin@ctcXXXX.onmicrosoft.com` |
   | パスワード          | Pa55w.rd1234                    |

   ![module03-01](./media/module03-01.BMP)

   

2. 受信トレイを表示させ、Webブラウザを最小化します。

   > 注：後の手順で使用します。

   ![module03-02](./media/module03-02.BMP)

   

3. 新しいWebブラウザのウィンドウを開き、https://www.dropbox.com/business/try?sku=adv のページにアクセスします。

   > 参考：今回はSSOをするためAdvancedの無料試用版を用意しています。
   >
   > 　　　Dropboxには様々なプランがあります。利用申し込みページは以下になります。
   >
   > 　　　https://www.dropbox.com/business/plans-comparison

   ![module03-03](./media/module03-03.BMP)

   

   

4. 次の情報を使用して「無料トライアル版の利用を開始」をクリックします。

   > 注：XXXXはご自身のアカウント番号を入力してください。
   >
   > 注：指定の無い項目は、「空欄」または「デフォルト値」で結構です。

   | 項目                                 | 値                              |
   | ------------------------------------ | ------------------------------- |
   | トライアル版のプランをお選びください | Advanced                        |
   | 名前                                 | XXXX                            |
   | 姓                                   | ctc                             |
   | メールアドレス                       | `admin@ctcXXXX.onmicrosoft.com` |
   | パスワード                           | Pa55w.rd1234                    |
   | チーム名                             | ctcXXXX                         |

   ![module03-04](./media/module03-04.BMP)

   

   

5. 画面が遷移し、「受信トレイでメール アドレスを確認してください」と表示されます。![module03-05](./media/module03-05.BMP)

   

6. 先に開いているoutlookを表示し、メールが届いたことを確認します。さらにメールの記載内容にある「メールアドレスを確認する」をクリックします。

   > 注：受信までに3分ほどかかる可能性があります。
   >
   > 注：迷惑メールに保存される場合があります。ご確認ください。

   ![module03-06](./media/module03-06.BMP)

   

7. 画面が遷移し、アンケート画面が表示されます。どれを選択してもOKです。

   ![module03-07](./media/module03-07.BMP)

   

8. 「Dropbox をダウンロードして開始します」画面が表示されます。「後にする」をクリックします。

   ![module03-08](./media/module03-08.BMP)

   

9. Dropboxのダッシュボードが表示されます。「管理コンソール」をクリックします。

   ![module03-09](./media/module03-09.BMP)

   

10. 「管理コンソール」画面が表示されます。「設定」をクリックします。

    ![module03-10](./media/module03-10.BMP)

    

11. 設定画面が表示されます。「シングル サインオン」をクリックします。

    ![module03-11](./media/module03-11.BMP)

    

12. 「設定＞シングル サインオン」画面が表示されます。「SSO ログインの URL」の「リンクをコピー」をクリックし、メモ帳などに貼り付けます。

    > 注：コピーしたリンクは、後の手順で使用します。
    >
    > 注：コピーしたリンクのサンプルです。#の数字が異なります。
    >
    > `https://www.dropbox.com/sso/###########`

    ![module03-12](./media/module03-12.BMP)

    

13. 一度、Dropboxの画面を最小化します。

    

## タスク2 - Azure AD でエンタープライズアプリケーションを登録する

このタスクでは、エンタープライズアプリケーションにDropbox Business を登録します。

登録することにより、SSOの構成を設定することができます。



1.  https://entra.microsoft.com/ へアクセスします。

   > 注:XXXXはご自身のアカウント番号を入力してください。
   >
   > 注:「アカウントの保護にご協力ください」と表示された場合は「今はしない」を選択してください。

   | 項目                | 値                              |
   | ------------------- | ------------------------------- |
   | メール、電話、Skype | `admin@ctcXXXX.onmicrosoft.com` |
   | パスワード          | Pa55w.rd1234                    |

   

2. 画面左ツリーの「Azure Active Directory」→「アプリケーション」→「エンタープライズ アプリケーション」の順にクリックします。

   ![module03-13](./media/module03-13.BMP)

   

3. 「エンタープライズ アプリケーション | すべてのアプリケーション」が表示されます。「+新しいアプリケーション」をクリックします。

   ![module03-14](./media/module03-14.BMP)

   

4. 「Azure AD ギャラリーの参照」が表示されます。「アプリケーションを検索」に「Dropbox」と入力し、「Dropbox Business」をクリックします。

   ![module03-15](./media/module03-15.BMP)

   

5. 「Dropbox Business」画面が表示されます。「作成」をクリックします。

   ![module03-16](./media/module03-16.BMP)

   

6. 画面が遷移し「Dropbox Business | 概要」が表示されます。「ユーザーとグループ」をクリックします。

   ![module03-17](./media/module03-17.BMP)

   

7. 「Dropbox Business | ユーザーとグループ」画面が表示されます。「+ユーザーまたはグループの追加」をクリックします。

   ![module03-18](./media/module03-18.BMP)

   

8. 「割り当ての追加」画面が表示されます。以下のユーザーを選択し、「割り当て」をクリックします。

   > 注：XXXXはご自身のアカウント番号を入力してください。

   　・`admin@ctcXXXX.onmicrosoft.com`

   ![module03-19](./media/module03-19.BMP)

   

   

9. 「Dropbox Business | ユーザーとグループ」で割りあてたユーザーが一覧に表示されたことを確認します。その後、「シングルサインオン」をクリックします。

   ![module03-20](./media/module03-20.BMP)

   

10. 「Dropbox Business | シングル サインオン」画面が表示されます。「SAML」をクリックします。

    ![module03-21](./media/module03-21.BMP)

    

    

11. 「Dropbox Business | SAML ベースのサインオン」画面が表示されます。「基本的なSAML構成」の「編集」をクリックします。

    ![module03-22](./media/module03-22.BMP)

    

    

12. 「基本的な SAML 構成」が表示されます。前の演習手順でコピーしたSSO ログインの URL」を用意し、次の情報を使用して「保存」をクリックします。

    > 注：指定の無い項目は、「空欄」または「デフォルト値」で結構です。
    >
    > 注：コピーしたリンクのサンプルです。#の数字が異なります。
    >
    > 　　`https://www.dropbox.com/sso/###########`

    | 項目            | 値                                        |
    | --------------- | ----------------------------------------- |
    | 応答 URL の追加 | `https://www.dropbox.com/saml_login`      |
    | サインオン URL  | `https://www.dropbox.com/sso/###########` |

    ![module03-23](./media/module03-23.BMP)

    

13. 保存成功後、画面右上の「閉じる」ボタンをクリックします。

    > 注：Webブラウザの「閉じる」ボタンではありません。

    ![module03-24](./media/module03-24.BMP)

    

14. 「Dropbox BusinessでシングルサインオンをTest」と表示されます。「いいえ、後でtestします」をクリックします。

    ![module03-25](./media/module03-25.BMP)

    

15. 「Dropbox Business | SAML ベースのサインオン」の「SAML 証明書」の項目にある「証明書 (Base64)」をダウンロードして自身のPCに保存します。

    > 注：ダウンロードしたデータは後の手順で使用します。保存場所はどちらでもOKです。
    >
    > 注：「Dropbox Business.cer」ファイルがダウンロードされます。

    ![module03-27](./media/module03-27.BMP)

    

16. 「Dropbox Business | SAML ベースのサインオン」の「Dropbox Business のセットアップ」にある「構成URLを展開し、「ログイン URL」の値をコピーしメモ帳などに貼り付けます。

    > 注：コピーしたリンクは、後の手順で使用します。

    ![module03-27](./media/module03-27.BMP)

    

## タスク3 - Dropbox Businessでシングルサインオンを構成する

このタスクでは、AzureAD のエンタープライズアプリケーション側で出力した情報を、Dropbox Business側でも設定し連携します。



1. Dropbox Businessの「設定＞シングル サインオン」画面を表示します。

   ![module03-28](./media/module03-28.BMP)

   

2. 次の情報を使用して「保存」をクリックします。

   | 項目                                      | 値                                                           |
   | ----------------------------------------- | ------------------------------------------------------------ |
   | シングルサインオン                        | 任意                                                         |
   | アイデンティティ プロバイダのログイン URL | エンタープライズアプリケーションの設定でコピーした「ログイン URL」 |
   | X.509 証明書                              | エンタープライズアプリケーションの設定でダウンロードした「Dropbox Business.cer」 |

   ![module03-30](./media/module03-29.BMP)

   

   

## タスク4 - My Apps からDropbox Business にSSOを検証する

このタスクでは、エンタープライズアプリケーションに登録されたアプリを「My Apps」からアクセスします。

アクセスする際にパスワード認証なしでDropbox Businessを利用することができます。



1. https://myapplications.microsoft.com/ へサインインします。

   > 注:XXXXはご自身のアカウント番号を入力してください。
   >
   > 注:「アカウントの保護にご協力ください」と表示された場合は「今はしない」を選択してください。

   | 項目                | 値                              |
   | ------------------- | ------------------------------- |
   | メール、電話、Skype | `admin@ctcXXXX.onmicrosoft.com` |
   | パスワード          | Pa55w.rd1234                    |

   

2. 「マイアプリ」画面が表示されます。「Dropbox Business」をクリックします。

   ![module03-30](./media/module03-30.BMP)

   

3. サインイン画面に遷移します。そのままサインインします。

   > 注：正常に動作する場合、パスワード入力せずにサインインが行われます。

   

4. Dropboxのトップページが表示されます。

   ![module03-31](./media/module03-31.BMP)

   

   

Module3 Lab は以上です。お疲れ様でした。



