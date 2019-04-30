---
title: タスク 4:照合アクティビティを Excel ファイルから結果をエクスポートする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c9424f2ba21fb4b93e359c8662974a82c62b4895
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63250892"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a>タスク 4:照合アクティビティから Excel ファイルに結果をエクスポートする
  ここでは、照合アクティビティから Excel ファイルに結果をエクスポートします。  
  
1.  **エクスポート**] ページで、[ **Excel ファイル**の**変換先の型**します。  
  
2.  選択**サバイバーシップの結果**オプション。 サバイバーシップ プロセスで DQS によってに基づいて各クラスターに保持するレコードが、**サバイバーシップ ルール**を選択します。  
  
3.  クリックして**参照**出力ファイルを保存するフォルダーに移動します。  
  
4.  型**Cleansed and Matched Suppliers.xls**名とクリック**オープン**します。  
  
5.  確認します**ピボット レコード**が選択されている、**サバイバーシップ ルール**します。 このオプションを選択すると、各クラスターのピボット レコードがクラスターからの出力に選択されます。 サバイバーシップ ルールの他のオプションは次のとおりです。  
  
    1.  **最も完全なレコード:** 保持するレコードは、設定されたフィールドの最大数です。  
  
    2.  **最長のレコード:** 保持するレコードは、ソース フィールド内の語句の最大数です。  
  
    3.  **最も完全で最長のレコード:** 保持するレコードは、設定されたフィールドの数が 1 つであるため、各フィールドに語句の最大数があります。  
  
     ![結果の照合 ページからエクスポート](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "照合 ページからの結果のエクスポート")  
  
6.  クリックして**エクスポート**結果を Excel ファイルにエクスポートします。  
  
7.  クリックして**閉じます**を閉じる、**一致するエクスポート** ダイアログ ボックス。  
  
8.  クリックして**完了**照合アクティビティを終了します。  
  
9. 開く、 **Cleansed and Matched Suppliers.xlsx**ファイルを開き、重複項目 (SupplierID) が表示されないことを確認します。  
  
 これで、仕入先データは重複項目を削除するためにクレンジングおよび照合されました。  
  
## <a name="next-step"></a>次の手順  
 [レッスン 4:MDS の仕入先データを格納します。](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)  
  
  
