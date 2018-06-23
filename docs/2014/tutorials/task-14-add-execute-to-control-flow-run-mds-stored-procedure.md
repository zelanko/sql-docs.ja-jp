---
title: 'タスク 14: 追加する SQL 実行タスクを MDS のストアド プロシージャを実行する制御フロー |Microsoft ドキュメント'
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
ms.assetid: 9a5d1b52-d505-4e6f-8a89-569329c094e2
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3d364f3e0a2fbff167336bffa6ea5092d0954d14
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074303"
---
# <a name="task-14-adding-execute-sql-task-to-control-flow-to-run-the-stored-procedure-for-mds"></a>タスク 14: SQL 実行タスクを制御フローに追加して MDS のストアド プロシージャを実行する
  MDS のステージング テーブルにデータを読み込んだ後、ステージングから MDS データベース内の適切なテーブルにデータを読み込むために、そのテーブルに関連付けられているストアド プロシージャを実行します。 このストアド プロシージャには、2 つの必須パラメーター LogFlag および VersionName を渡す必要があります。 LogFlag はトランザクションがステージング処理中にログ記録されるかどうかを指定し、VersionName はモデルのバージョンを示します。 参照してください[ステージング ストアド プロシージャ](http://msdn.microsoft.com/library/hh231028.aspx)詳細についてはトピックです。  
  
 ここでは、適切な MDS テーブルにステージング データを読み込むためのストアド プロシージャを起動する制御フローに SQL 実行タスクを追加します。  
  
1.  切り替えます、**制御フロー**タブです。  
  
2.  ドラッグ アンド ドロップ**SQL 実行タスク**から、 **SSIS ツールボックス**を**制御フロー**タブです。  
  
3.  右クリック**SQL 実行タスク**で、**制御フロー**タブをクリックし、をクリックして**の名前を変更**です。 型**MDS にデータを読み込むストアド プロシージャのトリガー**とキーを押します**ENTER**です。  
  
4.  接続**受信、クレンジング、照合、および Curate Supplier Data**に**Trigger Stored Procedure to Load Data**緑色のコネクタを使用します。  
  
     ![SQL 実行タスクに接続](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "SQL 実行タスクへの接続")  
  
5.  使用して、**変数**ウィンドウで、次の設定で 2 つの新しい変数を追加します。 表示されない場合、**変数**ウィンドウで、をクリックして**SSIS**クリックしてメニュー バー**変数**です。  
  
    |名前|データ型|値|  
    |----------|---------------|-----------|  
    |LogFlag|Int32|1|  
    |VersionName|String|VERSION_1|  
  
     ![SSIS 変数 ウィンドウ](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "SSIS 変数 ウィンドウ")  
  
6.  ダブルクリックして**MDS にデータを読み込むストアド プロシージャのトリガー**です。  
  
7.  **SQL 実行タスク エディター**ダイアログ ボックスで、 **(ローカル)。MDS** (または**localhost です。MDS**) の**接続**です。  
  
8.  型**EXEC [stg]. [udp_Supplier_Leaf]?、?、?** **SQL ステートメント**です。 SQL Server Management Studio を使用して名前を確認できます。  
  
     ![SQL エディター] ダイアログ ボックス - [全般設定を実行](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "SQL エディター] ダイアログ ボックス - [全般設定の実行")  
  
9. をクリックして**パラメーター マッピング**左側のメニューからです。  
  
10. **パラメーター マッピング**] ページで [**追加**マッピングを追加します。 ドロップダウン リストに値が正しく表示されるようにウィンドウを最大化し、列のサイズを変更します。  
  
11. 選択**user::versionname**のドロップダウン リストから、**変数名**です。  
  
12. 選択**NVARCHAR**の**データ型**です。  
  
13. 型**0** (ゼロ) を**パラメーター名**です。  
  
14. 前の 4 つの手順を繰り返して、さらに 2 つの変数を追加します。  
  
    |[変数名]|データ型 (重要)|[パラメーター名]|  
    |-------------------|-----------------------------|--------------------|  
    |User::LogFlag|LONG|1|  
    |User::BatchTag|NVARCHAR|2|  
  
     ![SQL 実行タスク エディター - パラメーター マッピング](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "SQL 実行タスク エディター - パラメーター マッピング")  
  
15. をクリックして**OK**を閉じる、 **SQL 実行エディター**  ダイアログ ボックス。  
  
## <a name="next-step"></a>次の手順  
 [タスク 15: SSIS プロジェクトをビルドおよび実行する](../../2014/tutorials/task-15-building-and-running-the-ssis-project.md)  
  
  