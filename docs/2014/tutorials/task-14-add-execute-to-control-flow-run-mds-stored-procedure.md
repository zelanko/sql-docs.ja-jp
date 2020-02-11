---
title: 'タスク 14: SQL 実行タスクを制御フローに追加して MDS のストアドプロシージャを実行する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 9a5d1b52-d505-4e6f-8a89-569329c094e2
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 3fe1eb6032d9d550b36252e16eee51c98c5d2384
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65477098"
---
# <a name="task-14-adding-execute-sql-task-to-control-flow-to-run-the-stored-procedure-for-mds"></a>タスク 14: SQL 実行タスクを制御フローに追加して MDS のストアド プロシージャを実行する
  MDS のステージング テーブルにデータを読み込んだ後、ステージングから MDS データベース内の適切なテーブルにデータを読み込むために、そのテーブルに関連付けられているストアド プロシージャを実行します。 このストアド プロシージャには、2 つの必須パラメーター LogFlag および VersionName を渡す必要があります。 LogFlag はトランザクションがステージング処理中にログ記録されるかどうかを指定し、VersionName はモデルのバージョンを示します。 詳細については、「[ステージングストアドプロシージャ](https://msdn.microsoft.com/library/hh231028.aspx)」を参照してください。  
  
 ここでは、適切な MDS テーブルにステージング データを読み込むためのストアド プロシージャを起動する制御フローに SQL 実行タスクを追加します。  
  
1.  次に、[**制御フロー** ] タブに切り替えます。  
  
2.  **SSIS ツールボックス**から [**制御フロー** ] タブに**SQL 実行タスク**をドラッグアンドドロップします。  
  
3.  [**制御フロー** ] タブで [ **SQL 実行タスク**] を右クリックし、[**名前の変更**] をクリックします。 「**データを MDS に読み込むためのトリガーストアドプロシージャ**」と入力し、 **enter**キーを押します。  
  
4.  緑色のコネクタを使用して**データを読み込むストアドプロシージャをトリガー**するために、 **Supplier データの受信、クレンジング、照合、および curate**を接続します。  
  
     ![SQL 実行タスクへの接続](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "SQL 実行タスクへの接続")  
  
5.  [**変数**] ウィンドウで、次の設定を使用して2つの新しい変数を追加します。 [**変数**] ウィンドウが表示されない場合は、メニューバーの [ **SSIS** ] をクリックし、[**変数**] をクリックします。  
  
    |Name|データ型|Value|  
    |----------|---------------|-----------|  
    |LogFlag|Int32|1 で保護されたプロセスとして起動されました|  
    |VersionName|String|VERSION_1|  
  
     ![[SSIS 変数] ウィンドウ](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "[SSIS 変数] ウィンドウ")  
  
6.  [トリガーストアドプロシージャ] をダブルクリックして、 **MDS にデータを読み込み**ます。  
  
7.  [ **SQL 実行タスクエディター** ] ダイアログボックスで、[(ローカル)] を選択し**ます。MDS** (または**localhost。****接続**用の MDS)。  
  
8.  「 **EXEC [stg]」と入力します。 [udp_Supplier_Leaf]?,?,?** **SQL ステートメント**の場合。 SQL Server Management Studio を使用して名前を確認できます。  
  
     ![[SQL 実行エディター] ダイアログ ボックス - [全般設定]](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "[SQL 実行エディター] ダイアログ ボックス - [全般設定]")  
  
9. 左側のメニューの [**パラメーターマッピング**] をクリックします。  
  
10. [**パラメーターマッピング**] ページで、[**追加**] をクリックしてマッピングを追加します。 ドロップダウン リストに値が正しく表示されるようにウィンドウを最大化し、列のサイズを変更します。  
  
11. **変数名**のドロップダウンリストから [ **User:: versionname** ] を選択します。  
  
12. [**データ型**] で [ **NVARCHAR** ] を選択します。  
  
13. **パラメーター名**として「 **0** 」 (ゼロ) を入力します。  
  
14. 前の 4 つの手順を繰り返して、さらに 2 つの変数を追加します。  
  
    |変数名|データ型 (重要)|パラメーター名|  
    |-------------------|-----------------------------|--------------------|  
    |User::LogFlag|LONG|1 で保護されたプロセスとして起動されました|  
    |User::BatchTag|NVARCHAR|2|  
  
     ![SQL 実行タスク エディター - パラメーター マッピング](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "SQL 実行タスク エディター - パラメーター マッピング")  
  
15. [ **OK** ] をクリックして [ **SQL 実行エディター** ] ダイアログボックスを閉じます。  
  
## <a name="next-step"></a>次のステップ  
 [タスク 15: SSIS プロジェクトをビルドおよび実行する](../../2014/tutorials/task-15-building-and-running-the-ssis-project.md)  
  
  
