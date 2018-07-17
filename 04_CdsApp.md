# Common Data Service でデータをクラウドに安全に保存する

アプリケーションで扱う **データをクラウド上に保存** して、改めて参照したり、権限を持つ適切な社員と共有したいことがあります。

PowerApps では、**CDS (Common Data Service)** を使うことによりデータを安全に保存することができます。

以下では、**CDS を使った PowerApps アプリ** を開発してみます。

CDS ではアプリ専用のデータベースを作成することができます。  
今回は、手順の簡単化のために CDS のサンプルとして自動生成されるデータベースを使うことにします。  
（アプリ専用のデータベース作成については、このステップの最後に簡単に手順を紹介します）

---

## CDS の作成

アプリ開発を始める前に、**専用のデータベース** を作成します。

1. [PowerApps](https://web.powerapps.com/) にサインインします。
2. **データ** - **エンティティ** - **データベースの作成** を選択します。

    <img src="Assets/Images/04/data_entity_newcds.png" width="420px" />

3. 既存の環境に CDS を作成できないため、**新しい環境を作成する** をクリックして、専用の環境を用意します。

    <img src="Assets/Images/04/data_entity_newenv_for_cds.png" width="420px" />

4. **環境名** を指定して **環境の作成** をクリックします。

    <img src="Assets/Images/04/new_env_settings.png" width="420px" />

5. **データベースの作成** で専用の CDS を作成します。

    <img src="Assets/Images/04/add_cds_to_newenv.png" width="420px" />

6. CDS を設定します。

    以下の設定をしたら **データベースの作成** をクリックします。

    - 通貨・・・JPY
    - 言語・・・Japanese
    - サンプルアプリとデータを含める・・・チェック

    <img src="Assets/Images/04/new_cds_settings.png" width="420px" />

---

## テンプレートを選択して新しいアプリの作成

1. アプリのテンプレートを選択します。

    CDS が作成されると自動的に **ホーム** に遷移します。（もし遷移しない場合は、**ホーム** をクリックします）  
    続いて、**データから開始** の **このアプリの作成** をクリックします。

    <img src="Assets/Images/04/select_datadriven_template.png" width="420px" />

2. **Common Data Service** の **携帯電話レイアウト** をクリックします。

    <img src="Assets/Images/04/newapp_template_cds_mobile.png" width="420px" />

3. CDS への接続を **作成** します。

    <img src="Assets/Images/04/create_cds_connector.png" width="420px" />

4. 自動的に **テーブルの選択** 画面に遷移するので、**タスク** テーブルに接続します。

    検索ボックスに **タスク** と入力し、リストに **タスク** が表示されたら、それを選択して **接続** をクリックします。

    <img src="Assets/Images/04/select_table_for_app.png" width="420px" />

5. 接続したテーブル（タスクテーブル）を操作するためのアプリが自動的に生成されます。

    アプリ生成が終了すると、自動的に **3個のスクリーン (画面) からなるアプリ** のデザイン画面が表示されます。

    <img src="Assets/Images/04/building_new_app.png" width="420px" />
    <img src="Assets/Images/04/new_app_for_tasktable.png" width="420px" />

表示項目は適切ではないので、この後の手順で変更しますが、完全に動作するアプリケーションが完成しています。

画面は、以下の 3画面からなります。

    - 一覧画面 (BrowseScreen1)
    - 詳細画面 (DetailScreen1)
    - 編集画面 (EditScreen1)

---

## 一覧画面の変更

一覧画面 (BrowseScreen1) の表示内容を変更します。

1. 左側のコントロールツリーで **BrowseScreen1** の **BrowseGallery1** を選択して、右側のフィールドの **編集** をクリックします。

    <img src="Assets/Images/04/browsescreen_gallery_fields.png" width="420px" />

2. フィールド表示で以下の設定をします。

    - Body1 ・・・説明 (description)
    - Subtitle1 ・・・期限 (scheduledend)
    - Title1 ・・・件名 (subject)

    <img src="Assets/Images/04/browsescreen_gallery_fieds_settings.png" width="420px" />

---

## 詳細画面の変更

同様に、詳細画面 (DetailScreen1) の表示内容を変更します。

1. 左側のコントロールツリーで **DetailScreen1** の **DetailForm1** を選択して、右側の **フィールド欄のボタン** ("7件選択済み" と表示されているはず) をクリックします。

    <img src="Assets/Images/04/detailscreen_form_fields.png" width="420px" />

2. フィールドの **優先度** および **状態** をチェックします。

    見えない場合はスクロールして探します。

    <img src="Assets/Images/04/detail_select_fields.png" width="420px" />

3. 選択済みのフィールドから、以下の4個のチェックを外します。

    - 関連
    - 所有者
    - 期間
    - 優先度 Value

    <img src="Assets/Images/04/detail_hide_fileds.png" width="420px" />

4. 選択状態のフィールドをドラッグして、以下の順番に並べます。

    - 件名
    - 優先度
    - 期日
    - 状態
    - 説明

    <img src="Assets/Images/04/detail_order_fields.png" width="420px" />

以上で、詳細画面の表示内容が適切なものになりました。

---

## 編集画面の変更

編集画面も同様に表示内容を変更します。

1. 左側のコントロールツリーで **EditScreen1** の **EditForm1** を選択して、右側の **フィールド欄のボタン** ("7件選択済み" と表示されているはず) をクリックします。

    <img src="Assets/Images/04/editscreen_form_fields.png" width="420px" />

2. 詳細画面と同様の操作で、表示するフィールドを以下の通り指定します。

    - 件名
    - 優先度
    - 期日
    - 状態
    - 説明

    <img src="Assets/Images/04/edit_order_fields.png" width="420px" />

以上で、すべての画面の変更が完了です。

---

## プレビュー実行

**BrowseScreen1** を選択してから、**プレビュー実行** をクリックして、プレビュー実行してみます。

<img src="Assets/Images/04/start_preview.png" width="420px" />

以下の機能が実装されています。

- タスクの一覧表示
- 詳細表示
- タスクの変更
- タスクの新規作成
- タスクの削除

<img src="Assets/Images/04/preview_browsescreen.png" width="420px" />
<img src="Assets/Images/04/preview_detailscreen.png" width="420px" />
<img src="Assets/Images/04/preview_editscreen.png" width="420px" />

**データから開始** でアプリ開発をすると、非常に簡単にアプリが完成します。

PowerApps の画面遷移や CDS へのデータ保存・参照の参考にもなるので、コントロールやプロパティを選択しながら、設定を確認してみるとよいと思います。

---

## (参考) 専用のテーブルの作成方法

ハンズオンではサンプルのテーブルを使いましたが、専用のテーブルを作成してからアプリを開発することもできます。

以下では、専用のテーブルの作成手順を紹介します。

1. PowerApps 画面で、**データ** - **エンティティ** - **新しいエンティティ** を選択します。

    <img src="Assets/Images/04/create_new_entity.png" width="420px" />

2. **新しいエンティティ** を定義します。

    参考として、経費精算を定義する場合は、以下のように入力して **次へ** をクリックします。

    <img src="Assets/Images/04/new_entity_settings.png" width="420px" />

3. **フィールドの追加** で、必要なフィールドを順に定義します。

    例えば、以下のように入力して、**完了** をクリックします。

    <img src="Assets/Images/04/new_field_settings.png" width="420px" />

4. フィールドの定義がすべて終わったら、**エンティティの保存** をクリックします。

    以下では、氏名フィールドのみ定義した状態ですが、実際には必要なフィールドをすべて定義してから、エンティティの保存をします。

    <img src="Assets/Images/04/new_entity_completed.png" width="420px" />

以上で、専用のテーブルが完成しました。  
このテーブルに接続するアプリケーションは、このハンズオンと同じように開発できます。