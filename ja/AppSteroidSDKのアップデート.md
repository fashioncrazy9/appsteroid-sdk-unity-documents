# AppSteroid for Unity のアップデート

----------

AppSteroid のアップデート方法について説明します。新規でインストールする場合は、[GettingStarted](GettingStarted.md) をご参照ください。

## 通常のアップデート方法
1. **<span style="color:red">作業の前にプロジェクトのバックアップを行ってください。</span>**
2. [Fresvii のダウンロードサイト](https://fresvii.com/downloads)から、該当パッケージのダウンロードを行います。
3. パッケージのファイルをすべてインポートします。エラーが出ていなければ正常にアップデートが完了です。

## Unity 4.6.x から Unity 5.x.x にアップデートする方法
1. **<span style="color:red">作業の前にプロジェクトのバックアップを行ってください。</span>**
2. Unity 5 にて該当プロジェクトを開いて、プロジェクトをアップデートしてください。この時点では、Unity 4.6用の AppSteroid SDK が適用されていますので、インポート後にエラーが出る可能性があります。エラーが出ていない場合も Unity 5 用の AppSteroid の適用が必要ですので、以下の手順を引き続き行ってください。
3. `Assets/Fresvii/AppSteroid/Resources/FASSettings.asset`ファイルを`Assets/Fresvii`フォルダ以外にコピーして保存してください。`FASSettings.asset`ファイルは AppID や Secret Key などの AppSteroid の設定情報が保存されたファイルです。`Assets/Fresvii/AppSteroid/Scripts/FASSettings.cs`ではないのでご注意ください。
4. `Assets/Fresvii`フォルダを削除してください。
5. `Assets/Plugins`フォルダ内に、`Android/AppSteroidAndroid.dll`,`Android/AppSteroidWithVoiceChatAndroid.dll`,`iOS/AppSteroidIOS.dll`,`iOS/AppSteroidWithVoiceChatIOS.dll`のいずれかがありますので、それを削除してください。
6.  AppSteroid の Unity 5 用パッケージをインストールしてください。インポート後、エラーが出ていなければ正常にアップデートが完了です。保存した`FASSettings.asset`を元のフォルダに戻すか、上書きしてください。
7.  Android をご利用の場合は、Manifest ファイルを再作成してください。Unity 5 にて、UnityPlayerNativeActivity-> UnityPlayerActivity に変更が施されました。UnityPlayerNativeActivity-> UnityPlayerActivity に変更するか、FAS Settings -> Generate Android.manifest によりManifestファイルを再作成してください。
8.  インポート後にエラーが出た場合は、以下の**Unity 5 でインポート直後にエラーが出た場合**をご確認ください。

## ボイスチャット機能の「あり」「なし」の AppSteroid SDK の変更を行う方法
1. **<span style="color:red">作業の前にプロジェクトのバックアップを行ってください。</span>**
2. `Assets/Fresvii/AppSteroid/Resources/FASSettings.asset`ファイルを`Assets/Fresvii`フォルダ以外にコピーして保存してください。`FASSettings.asset`ファイルは AppID や Secret Key などの AppSteroid の設定情報が保存されたファイルです。`Assets/Fresvii/AppSteroid/Scripts/FASSettings.cs`ではないのでご注意ください。
3. `Assets/Fresvii`フォルダを削除してください。
4. `Assets/Plugins`フォルダ内に、`Android/AppSteroidAndroid.dll`,`Android/AppSteroidWithVoiceChatAndroid.dll`,`iOS/AppSteroidIOS.dll`,`iOS/AppSteroidWithVoiceChatIOS.dll`のいずれかがありますので、それらをすべて削除してください。また、ボイスチャット機能を「あり」→「なし」に変更する場合は、`Assets/Plugins/Android/libvoicechat.so`と `Assets/Plugins/iOS/libvoicechat.a` の２つを削除してください。
6.  AppSteroid の該当パッケージをインストールしてください。インポート後、エラーが出ていなければ正常に作業が完了です。
保存した`FASSettings.asset`を元のフォルダに戻すか、上書きしてください。
7. ボイスチャット「あり」に変更した場合は、[カスタム コンパイル フラグ「GROUP_CONFERENCE」を定義](%E3%82%B0%E3%83%AB%E3%83%BC%E3%83%97%E3%82%AB%E3%83%B3%E3%83%95%E3%82%A1%E3%83%AC%E3%83%B3%E3%82%B9%EF%BC%88%E3%83%9C%E3%82%A4%E3%82%B9%E3%83%81%E3%83%A3%E3%83%83%E3%83%88%EF%BC%89%E3%81%AE%E5%88%A9%E7%94%A8%E6%96%B9%E6%B3%95.md#2-%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%A0-%E3%82%B3%E3%83%B3%E3%83%91%E3%82%A4%E3%83%AB-%E3%83%95%E3%83%A9%E3%82%B0-%E3%82%92%E5%AE%9A%E7%BE%A9%E3%81%99%E3%82%8B) してください。「なし」に変更した場合は、「GROUP_CONFERENCE」の定義を削除してください。

ボイスチャット機能の「あり」「なし」の AppSteroid SDK の変更を行った場合、FASSettigns.asset を元のフォルダに戻したときに、設定ファイルが正常に認識されず、設定情報が初期状態になってしまうことが稀にあります。
この症状が起こってしまった場合には、お手数ですが Fresvii->FASSettings のメニューより設定情報を再度入力ください。

## インポート直後にエラーが出た場合
 
### Unity 5 でインポート直後にエラーが出た場合

    Assets/Fresvii/AppSteroid/GUI/Scripts/FresviiGUIChat.cs(406,161): error CS0234: The type or namespace name `Error' does not exist in the namespace `Fresvii.AppSteroid.Models'. Are you missing an assembly reference?
    .....

![DLL Duplicate](./Images/ImportDuplicateError.png)

Unity 5 にて、unitypackage からアセットがインポートされたときの挙動が変更されました。Asset の GUIDが一致しない場合、Unity が " 1" をファイル名に追加して重複したファイルを生成します。AppSteroid をアップデートした際、GUIDが一致しない場合があります。この場合は以下の対応を行ってください。

1. `Assets/Plugins/Android/AppSteroidAndroid.dll` と `Assets/Plugins/Android/AppSteroidAndroid　1.dll`、および、`Assets/Plugins/iOS/AppSteroidIOS.dll` と `Assets/Plugins/iOS/AppSteroidIOS　1.dll` が存在している場合、`AppSteroidAndroid.dll`,`AppSteroidAndroid 1.dll`, `AppSteroidIOS.dll`,`AppSteroidIOS 1.dll` の４つのファイルを削除してください。
2. 再度、AppSteroid の該当パッケージをインストールしてください。インポート後、エラーが出ていなければ正常にアップデートが完了です。

## GUI起動後に不具合がある場合

### Fresvii GUI の 「My Proflie」や「User Profile」 が正常に表示されない場合

#### Case 1 画面のレイアウトが崩れる場合

 1. ボイスチャット「あり」の場合は、[カスタム コンパイル フラグ「GROUP_CONFERENCE」を定義](%E3%82%B0%E3%83%AB%E3%83%BC%E3%83%97%E3%82%AB%E3%83%B3%E3%83%95%E3%82%A1%E3%83%AC%E3%83%B3%E3%82%B9%EF%BC%88%E3%83%9C%E3%82%A4%E3%82%B9%E3%83%81%E3%83%A3%E3%83%83%E3%83%88%EF%BC%89%E3%81%AE%E5%88%A9%E7%94%A8%E6%96%B9%E6%B3%95.md#2-%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%A0-%E3%82%B3%E3%83%B3%E3%83%91%E3%82%A4%E3%83%AB-%E3%83%95%E3%83%A9%E3%82%B0-%E3%82%92%E5%AE%9A%E7%BE%A9%E3%81%99%E3%82%8B) してください。「なし」の場合は、「GROUP_CONFERENCE」の定義を削除してください。
 2. ビルド設定を Android か iOS に設定して下さい。

#### Case 2 下記のようなエラーがフォーラムなどで出た場合

    MissingReferenceException: The variable userIconMaterial of FresviiGUIThreadCard doesn't exist anymore.
    You probably need to reassign the userIconMaterial variable of the 'FresviiGUIThreadCard' script in the inspector.
    UnityEngine.Material.SetColor (Int32 nameID, Color color) (at C:/buildslave/unity/build/artifacts/generated/common/runtime/ShaderBindings.gen.cs:194)
    UnityEngine.Material.SetColor (System.String propertyName, Color color) (at C:/buildslave/unity/build/artifacts/generated/common/runtime/ShaderBindings.gen.cs:191)
    UnityEngine.Material.set_color (Color value) (at C:/buildslave/unity/build/artifacts/generated/common/runtime/ShaderBindings.gen.cs:183)
    Fresvii.AppSteroid.Gui.FresviiGUIThreadCard.Draw (Single cardWidth) (at Assets/Fresvii/AppSteroid/GUI/Scripts/FresviiGUIThreadCard.cs:878)
    Fresvii.AppSteroid.Gui.FresviiGUIForum.OnGUI () (at Assets/Fresvii/AppSteroid/GUI/Scripts/FresviiGUIForum.cs:843)
    
Prefab のリンクが切れて、一部のマテリアルが null になっている可能性があります。Unity 5 を利用している場合は、Unityを 5.0.1 以上にアップデートいただくと修正される場合があります。さらに不具合がある場合は、下記の手順を行ってください。

1. **<span style="color:red">作業の前にプロジェクトのバックアップを行ってください。</span>**
2. `Assets/Fresvii/AppSteroid/Resources/FASSettings.asset`ファイルを`Assets/Fresvii`フォルダ以外にコピーして保存してください。`FASSettings.asset`ファイルは AppID や Secret Key などの AppSteroid の設定情報が保存されたファイルです。
3. `Assets/Fresvii`フォルダを削除してください。
4.  AppSteroid の該当パッケージを再度インストールしてください。インポート後、エラーが出ていなければ正常に作業が完了です。
保存した`FASSettings.asset`を元のフォルダに戻すか、上書きしてください。
