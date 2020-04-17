---
title: 'タスク 2: Excel 用 MDS アドインを使用して MDS にサプライヤー データをアップロードする |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4e3cd4cecd88bcad83c6e9f2a59ecd5f225fb02a
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487696"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a>タスク 2: Excel 用 MDS アドインを使用して仕入先データを MDS にアップロードする
  このタスクでは **、Excel 用 MDS アドイン**を使用して、クレンジングおよびサプライヤ データを**MDS**に発行します。 前のレッスンで作成**Supplier**した**仕入先**モデルで Supplier という名前のエンティティを作成します。 エンティティは、Excel ファイルの各列に属性を持ちます。 Supplier エンティティのコード属性と名前属性は、Excel の **[仕入先コード]** 列と **[仕入先名]** 列に対応します。  
  
1.  **Excel****で [クレンジングおよび一致仕入先.xls]** を開きます。  
  
2.  **Ctrl キーを押しながら A キー**を押して、データ全体を選択します。 スプレッドシートのデータ全体を選択することが**重要**です。  
  
3.  メニュー バーの [**マスター データ**] をクリックします。  
  
4.  リボンの [**エンティティの作成**] ボタンをクリックします。  
  
     ![Excel - [マスター データ] タブ - [エンティティの作成] ボタン](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - [マスター データ] タブ - [エンティティの作成] ボタン")  
  
5.  [**接続の管理**] ダイアログ ボックスで、[既存の接続] の下に**ローカル MDS サーバー**への**接続**が表示されない場合は、次の操作を行います。  
  
    1.  [**新しい接続を作成する**] を選択し、[新規] ボタン**を**クリックします。  
  
    2.  [**新しい接続の追加**] ダイアログ ボックスで、[**説明**] と**\/[HTTP: /localhost/MDS** for MDS サーバー アドレス] に「**ローカル MDS** **サーバー**」と入力し **、[OK] を**クリックしてダイアログ ボックスを閉じます。  
  
6.  [**接続の管理**] ダイアログ ボックスで、[ローカル`http://localhost/MDS` **MDS サーバー** ( ) を選択し、**テスト**をクリックして接続をテストします。 メッセージ ボックスで **[OK] を**クリックします。  
  
7.  [**接続**] をクリックして、MDS サーバーに接続します。  
  
8.  [**エンティティの作成 ]** ダイアログ ボックスで、 **[ モデル**] の [**仕入先 ]** を選択します。  
  
9. **[バージョン****] で [VERSION_1]** が選択されていることを確認します。  
  
10. **新規エンティティ名**に **「仕入先**」と入力します。  
  
11. **一意の識別子フィールドを含む列に**[**仕入先コード**] を選択します (コードを自動的に生成することもできます)。 基本的に **、Excel**の **[仕入先コード]** 列を**Supplier**エンティティの **[コード**] 属性にマッピングしています。  
  
12. [**仕入先名] を**選択**し、名前フィールドを含む列に対して**選択します。 基本的に **、Excel**の **[仕入先名]** 列を**Supplier**エンティティの **[名前]** 属性にマッピングしています。 **コード**属性と**名前**属性は、MDS のエンティティの必須属性です。  
  
     ![[エンティティの作成] ダイアログ ボックス](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "[エンティティの作成] ダイアログ ボックス")  
  
13. **[OK] を**クリックして MDS 上にエンティティを作成し、マスター データをエンティティに公開して、[**エンティティの作成**] ダイアログ ボックスを閉じます。  
  
14. これで、エンティティ名である**Supplier**という新しいシートが Excel スプレッドシートに追加され、ワークシートの上部にワークシートが MDS サーバーに接続されていることが確認できます。 元のワークシート **(Sheet1)** がまだ存在していることに注意してください。  
  
     ![Excel - [仕入先] と [Sheet1] タブ](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - [仕入先] と [Sheet1] タブ")  
  
     ![Excel - MDS 接続の詳細の表示](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - MDS 接続の詳細の表示")  
  
15. **Excel を**開いたままにします。  
  
## <a name="next-task"></a>次の作業  
 [タスク 3: マスター データ マネージャーのデータを確認する](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  
