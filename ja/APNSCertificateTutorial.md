
# Push Notificationの導入手順
Fresvii AppSteroid のプッシュ通知は Apple Push Notification Service (APNS) を利用しています。そのため、AppSteroid でプッシュ通知を利用するには、AppSteroid への設定の他、APNS の設定及びそれぞれの環境に合わせた整備も必要になります。

以下に示した手順に従って操作すると、AppSteroid のプッシュ通知を受け取る設定が完了したことになります。

## App ID の取得
APNS を利用するにあたり、アプリケーションを判別するための固有のアプリケーションIDをそれぞれのiOSアプリケーションごとに発行する必要があります。まずは、iOS Developer Center から、あなたのアプリケーションに対する Apple APP IDを取得します。

1. プッシュ通知を使うための第一歩として、Apple Developer アカウントの設定を行う必要があります。[iOS Developer ポータル](https://developer.apple.com/devcenter/ios/) にログインしてください。

2. "Certificates, Identifiers & Profiles" をクリックしてください。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_01.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />
3. "Identifiers" をクリックしてください。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_02.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

4. "App IDs" タブを開き、"+" へ進み、新たに App ID を取得します。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_03.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

5. ①にあなたのアプリ名を入力してください。②に Bundle ID を入力してください。（ワイルドカードは使用できません）ID例："com.fresvii.appsteroidtest"

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_04.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

6. 取得した App ID を確認し、Submit ボタンをクリックします。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_05.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

----------

## Certificate Signing Request (CSR) の作成

SSL 証明書を要求するために、CSR を作成する必要があります。以下の手順に従って操作を行ってください。

1. Mac OS X 上で Keychain Access application を立ち上げます。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_06.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

2. キーチェーンアクセス > 証明書アシスタント > 認証局に証明書を要求と進みます。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_07.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

3. 以下の各フィールドに情報を入力します。"Saved to disk" を選択し、"Continue" をクリックしてください。ここで入力した内容は後ほど使用するため、どこかに保存しておいてください。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_08.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

4. ファイル名と保存場所はそのままにし、Save をクリックしてください。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_09.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

5. プロダクション証明書を作成する際にも、上記に記した手順と同様の手順になります。

----------

## Push Certificate の設定

1. リストより、先ほど作成した App ID をクリックしてください。現在のサービス内容が確認できます。Edit ボタンをクリックし、プッシュ通知の設定を開始します。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_11.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

2. 設定画面が開くので、Push Notification セクションまで移動します。①のボックスがデフォルトで無効になっているので、チェックボックスをクリックし有効にした後、Development SSL Certificate 内の② "Create Certificate…" をクリックします。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_12.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

3. セットアップウィザードが表示されるのでContinueをクリックします。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_13.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

4. "Choose File" ボタンをクリックし、先ほど作成した CSR ファイルの保存先を指定し、"Generate" ボタンをクリックします。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_14.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

5. SSL 証明書が作成されるので、 "Download" 後 "Done" をクリックします。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_15.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

6. プロダクション証明書を作成する際にも、上記に記した手順と同様の手順になります。

----------

## APNS 証明書の入手
1. 以下の箇所からも証明書のダウンロードができます。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_16.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

2. 先ほどダウンロードした SSL 証明書、"aps_developer_identity.cer" をダブルクリックし、Keychain Access application にインストールします。SSL 証明書は APNS を通してあなたのアプリケーションにプッシュ通知を送信するために使われます。

3. Keychain Assistant を立ち上げ、前のステップで作成した証明書が表示されていることを確認してください。左のリストから "login" 、"Certificates" を選択します。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_Z.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

4. ドロップオプションを開き、"Apple Development iOS Push Services" -> Export "Apple Development iOS Push Services …" を選択し、"apnscert.-dev-p12" として保存します。

  エクスポート用のパスワードを入力します。（空でもかまいません）

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_X.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

  操作しているデバイスでセットアップされている管理者パスワードを入力してください。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_Y.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

5. プロダクション証明書を作成する際にも、上記に記した手順と同様の手順になります。

----------

## p12ファイルのアップロード

これで Fresvii のウェブコンソールに証明書をアップロードする準備が整いました。

1. [Fresvii](http://fresvii.com) にログインして、Settings->Notification より作成したp12ファイルをアップロードします。p12ファイルを書き出す際にパスワードを設定した場合は "Password" フォームにパスワードを入力してください。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_A.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />


2. アップロードが完了すると以下の画面が表示されます。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_B.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

----------

## Provision Profile の作成

1. ブラウザより Apple Developer ポータルを開き、"Provisioning Profiles" を選択します。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_17.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

2. 右上の "+" をクリックし、新しいプロファイルを作成します。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_18.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

3. 必要なプロファイルを選択後、"Continue" をクリックします。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_19.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

4. 先ほど作成した App ID を選択します。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_20.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

5. プロファイルに含みたい Development Certificate を選択し、"Continue" をクリックします。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_21.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

6. アプリケーションを実行するデバイスを選択します。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_22.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

7. 好まれるプロファイル名を入力し、 “Generate” ボタンをクリックしプロファイルを作成します。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_23.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

8. 最後に Provisioning Profile をダウンロードします。ダウンロード後、ファイルを開いてください。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_24.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

9. 以下の画面から Provisioning Profile をダウンロード、編集する事も出来ます。

  <img src="https://raw.githubusercontent.com/fresvii/appsteroid-sdk-ios-documents/master/ja/GetStarted/Images/APNS/certificate_25.png" style="border: 1px solid #A0A0A0; border-radius: 12px;" />

----------

## Xcode のセットアップ

1. 次のステップとして、プロジェクトの設定を行います。まず、 Xcode でプロファイルが正しく読み込まれている事を確認してください。Preferences 内の Accounts から、 View Details を実行するとインストールが完了したプロファイルを確認する事が出来ます。

2. アプリケーションプロジェクトの bundle id が、前の手順で作成した App ID の bundle identifier と一致している事を確認してください。

3. Project Settings より、 Target を選択し、 Code Signing タブをクリックしてください。ページ下部に先ほど作成した Provision Profile があるのでそれを選択します。

4. おつかれさまでした、以上で設定作業は完了です。
