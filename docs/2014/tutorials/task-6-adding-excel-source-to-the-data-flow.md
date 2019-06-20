---
title: タスク 6:Excel ソースをデータ フローに追加する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0209055e-cb6b-4a07-909e-836596727a2c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: e31b673d7bb80a74cccd664f1e29b72dcd49f4a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65489322"
---
# <a name="task-6-adding-excel-source-to-the-data-flow"></a>タスク 6:Excel ソースをデータ フローに追加する
  ここでは、Excel ソースをデータ フローに追加してソース Excel ファイルから仕入先データを読み取ります。 Excel ソースは、Microsoft Excel ブック内のワークシートまたは範囲からデータを抽出します。 参照してください[Excel ソース](../integration-services/data-flow/excel-source.md)詳細についてはトピック。  
  
1.  ドラッグ アンド ドロップ**Excel ソース**から**その他のソース**で**SSIS ツールボックス**を**データ フロー**タブ。  
  
2.  右クリックして**Excel ソース**で、**データ フロー**タブをクリックし、をクリックして**の名前を変更**します。  
  
3.  型**Read Supplier Data from Excel ファイル**キーを押します**ENTER**します。  
  
4.  ダブルクリック**Read Supplier Data from Excel ファイル**を起動する、 **Excel ソース エディター**  ダイアログ ボックス。  
  
5.  **Excel ソース エディター**ダイアログ ボックスで、をクリックして**新規**Excel 接続を作成します。  
  
6.  **Excel 接続マネージャー**ダイアログ ボックスで、をクリックして**参照**を選び、 **Suppliers.xls**ファイル、 **EIM チュートリアル**フォルダー. 確認します**Microsoft Excel 97-2003**でが選択されて、 **Excel バージョン**ボックスをクリックして**OK**。  
  
     ![Excel 接続マネージャー ダイアログ ボックス](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "Excel 接続マネージャー ダイアログ ボックス")  
  
7.  **Excel ソース エディター**ダイアログ ボックスで、 **IncomingSuppliers$** で、 **Excel シートの名前**ボックスの一覧。  
  
     ![名前の Excel シート - 受信の仕入先 $](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "Excel シート - 受信の仕入先 $ の名前")  
  
8.  クリックして**プレビュー**を Excel ファイル内のデータをプレビューします。  
  
9. **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
10. ドラッグ アンド ドロップ**DQS クレンジング**変換**その他の変換**上、 **SSIS ツールボックス**を**データ フロー**タブ**Excel ファイルから仕入先データを読み取る**します。 DQS クレンジング変換では、Data Quality Services (DQS) を使用し、ナレッジ ベースの承認済みのルールを適用することで、データを修正します。 この変換は、実行時に、DQS サーバー上に DQS クレンジング プロジェクトを作成します。 参照してください[DQS クレンジング変換](https://msdn.microsoft.com/library/ee677619.aspx)詳細についてはトピック。  
  
## <a name="next-step"></a>次の手順  
 [タスク 7:追加の DQS クレンジング変換データ フローを](../integration-services/data-flow/data-flow.md)  
  
  
