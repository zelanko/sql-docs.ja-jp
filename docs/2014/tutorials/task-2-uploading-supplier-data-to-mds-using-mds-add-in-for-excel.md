---
title: 'タスク 2: Excel 用 MDS アドインを使用して Supplier データを MDS にアップロードする |Microsoft Docs'
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81487696"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a>タスク 2: Excel 用 MDS アドインを使用して仕入先データを MDS にアップロードする
  このタスクでは、 **Excel 用 MDS アドイン**を使用して、クレンジングおよび仕入先データを**MDS**に発行します。 **Supplier**という名前のエンティティを作成するには、前のレッスンで作成した**サプライヤー**モデルを使用します。 エンティティは、Excel ファイルの各列に属性を持ちます。 Supplier エンティティの Code 属性と Name 属性は、Excel の [**仕入**先] 列と [ **supplier name** ] 列に対応しています。  
  
1.  **クレンジングされ、一致した仕入先 .xls**を**Excel**で開きます。  
  
2.  Ctrl キーを押し**ながら A**キーを押してデータ全体を選択します。 スプレッドシートでデータ全体を選択することが**重要**です。  
  
3.  メニューバーの [**マスターデータ**] をクリックします。  
  
4.  リボンの [**エンティティの作成**] ボタンをクリックします。  
  
     ![Excel - [マスター データ] タブ - [エンティティの作成] ボタン](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - [マスター データ] タブ - [エンティティの作成] ボタン")  
  
5.  [**接続の管理**] ダイアログボックスで、[**既存の接続**] に [**ローカル MDS サーバー**への接続] が表示されない場合は、次の手順を実行します。  
  
    1.  [**新しい接続の作成**] を選択し、[**新規**] ボタンをクリックします。  
  
    2.  [**新しい接続の追加**] ダイアログボックスで、[**説明**] に「**ローカル MDS サーバー** 」と入力し、 **mds サーバーアドレス**には**http:\//localhost/MDS**を入力し、[ **OK** ] をクリックしてダイアログボックスを閉じます。  
  
6.  [**接続の管理**] ダイアログボックスで [**ローカル MDS サーバー** (`http://localhost/MDS`)] を選択し、[**テスト**] をクリックして接続をテストします。 メッセージボックスで [ **OK]** をクリックします。  
  
7.  [**接続**] をクリックして MDS サーバーに接続します。  
  
8.  [**エンティティの作成**] ダイアログボックスで、**モデル**の [**仕入先**] を選択します。  
  
9. **VERSION_1**が**バージョン**に対して選択されていることを確認します。  
  
10. **新しいエンティティ名**として「 **Supplier** 」と入力します。  
  
11. **一意の識別子フィールドを含む列**の [**仕入**先] を選択します (コードを自動的に生成することもできます)。 基本的には、 **Excel**の **"仕入先" 列を** **Supplier**エンティティの**Code**属性にマップします。  
  
12. [名前] フィールド**が含まれている列**の [ **Supplier Name** ] を選択します。 基本的には、 **Excel**の**supplier Name**列を**supplier**エンティティの**name**属性にマップします。 **Code**属性と**Name**属性は、MDS のエンティティの必須属性です。  
  
     ![[エンティティの作成] ダイアログ ボックス](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "[エンティティの作成] ダイアログ ボックス")  
  
13. [ **OK]** をクリックして MDS にエンティティを作成し、マスターデータをエンティティにパブリッシュして、[**エンティティの作成**] ダイアログボックスを閉じます。  
  
14. これで、" **Supplier**" という名前の新しいシートが表示されます。これは、Excel スプレッドシートに追加され、ワークシートの上部に、ワークシートが MDS サーバーに接続されていることを示します。 元のワークシート ( **Sheet1**) は依然として存在することに注意してください。  
  
     ![Excel - [仕入先] と [Sheet1] タブ](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - [仕入先] と [Sheet1] タブ")  
  
     ![Excel - MDS 接続の詳細の表示](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - MDS 接続の詳細の表示")  
  
15. **Excel**を開いたままにします。  
  
## <a name="next-task"></a>次の作業  
 [タスク 3: マスター データ マネージャーのデータを確認する](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  
