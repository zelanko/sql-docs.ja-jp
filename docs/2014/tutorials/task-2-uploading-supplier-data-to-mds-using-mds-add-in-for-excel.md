---
title: 'タスク 2: Excel 用 MDS アドインを使用して MDS に仕入先データをアップロードして |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1831fc9ea79027e24d752d05e3b50d3a58d6e06f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072919"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a>タスク 2: Excel 用 MDS アドインを使用して仕入先データを MDS にアップロードする
  このタスクで、クレンジングされた仕入先データを発行する**MDS**を使用して、 **MDS アドインを Excel 用**です。 という名前のエンティティを作成する**業者**で、 **Suppliers**前のレッスンで作成したモデル。 エンティティは、Excel ファイルの各列に属性を持ちます。 Supplier エンティティの Code および Name 属性に対応して、 **SupplierID**と**Supplier Name** Excel の列です。  
  
1.  開いている**クレンジングおよび照合 Suppliers.xls**で**Excel**です。  
  
2.  キーを押して**CTRL + A**データ全体を選択します。 **重要**スプレッドシートのデータ全体を選択します。  
  
3.  をクリックして**マスター データ**メニュー バーでします。  
  
4.  をクリックして**エンティティの作成**リボンのボタンをクリックします。  
  
     ![Excel - [マスター データ] タブ - エンティティ ボタンを作成する](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - [マスター データ] タブ - エンティティ ボタンを作成します。")  
  
5.  **接続の管理**] ダイアログ ボックスへの接続が表示されない場合**ローカル MDS サーバー** [**既存の接続**を次の操作します。  
  
    1.  選択**新しい接続を作成**、 をクリック**新規**ボタンをクリックします。  
  
    2.  **新しい接続の追加** ダイアログ ボックスで、「**ローカル MDS サーバー**の**説明**と**http://localhost/MDS**の**MDS サーバー アドレス**、 をクリック**OK**  ダイアログ ボックスを閉じます。  
  
6.  **接続の管理**ダイアログ ボックスで、**ローカル MDS サーバー** (http://localhost/MDS)をクリックして**テスト**接続をテストします。 をクリックして**OK**メッセージ ボックスにします。  
  
7.  をクリックして**接続**MDS サーバーに接続します。  
  
8.  **エンティティの作成**ダイアログ ボックスで、 **Suppliers**の**モデル**です。  
  
9. いることを確認**VERSION_1**が選択されて**バージョン**します。  
  
10. 入力**業者**の**新しいエンティティ名**です。  
  
11. 選択**SupplierID**の**を一意の識別子を含む列**(生成することも、コードに自動的に) フィールドです。 基本的にマッピングする、 **SupplierID**内の列**Excel**を**コード**の属性**業者**エンティティです。  
  
12. 選択**Supplier Name**の**名前を含む列**フィールドです。 基本的にマッピングする、 **Supplier Name**内の列**Excel**を**名前**の属性、**業者**エンティティ。 **コード**と**名前**属性は、MDS のエンティティの必須の属性です。  
  
     ![エンティティのダイアログ ボックスを作成する](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "エンティティ ダイアログ ボックスを作成します。")  
  
13. をクリックして**OK**を MDS にエンティティを作成するエンティティにマスター データを発行して閉じます**エンティティの作成** ダイアログ ボックス。  
  
14. これで、という名前の新しいシートを表示する必要があります**業者**、これは、Excel スプレッドシートに追加するエンティティの名前と、ワークシートの上部にあるワークシートが MDS サーバーに接続されていることを確認する必要があります。 注意して元のワークシート (という**Sheet1**) が存在します。  
  
     ![Excel - [仕入先と Sheet1] タブ](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - [仕入先と Sheet1] タブ")  
  
     ![Excel - MDS 接続の詳細を示す](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - MDS 接続の詳細を表示")  
  
15. 保持**Excel**を開きます。  
  
## <a name="next-task"></a>次の作業  
 [タスク 3: マスター データ マネージャーのデータを確認する](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  