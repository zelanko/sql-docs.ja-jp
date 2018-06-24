---
title: 'タスク 4: 照合アクティビティを Excel ファイルから結果をエクスポートする |Microsoft ドキュメント'
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
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 440e8c0db00d5087334746f4094c61de52bf1bc5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072657"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a>タスク 4: 照合アクティビティから Excel ファイルに結果をエクスポートする
  ここでは、照合アクティビティから Excel ファイルに結果をエクスポートします。  
  
1.  **エクスポート**] ページで、[ **Excel ファイル**の**変換先の型**です。  
  
2.  選択**サバイバーシップの結果**オプション。 サバイバーシップ プロセスでは、DQS はに基づいて各クラスターで保持するレコードが決定、**サバイバーシップ ルール**を選択します。  
  
3.  をクリックして**参照**出力ファイルを保存するフォルダーに移動します。  
  
4.  型**Cleansed and Matched Suppliers.xls**名とクリック**開く**です。  
  
5.  いることを確認**ピボット レコード**が選択されて、**サバイバーシップ ルール**です。 このオプションを選択すると、各クラスターのピボット レコードがクラスターからの出力に選択されます。 サバイバーシップ ルールの他のオプションは次のとおりです。  
  
    1.  **最も完全なレコード:** 保持するレコードが設定されたフィールドの数が 1 つです。  
  
    2.  **最長のレコード:** 保持するレコードのソース フィールド内の語句の最大数です。  
  
    3.  **最も完全で最長のレコード:** 保持するレコードが、設定されたフィールドの数が 1 つになり各フィールドで用語の最大数を持ちます。  
  
     ![照合 ページから結果をエクスポート](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "照合 ページから結果をエクスポート")  
  
6.  をクリックして**エクスポート**結果を Excel ファイルにエクスポートします。  
  
7.  をクリックして**閉じる**を閉じる、**一致するエクスポート** ダイアログ ボックス。  
  
8.  をクリックして**完了**照合アクティビティを終了します。  
  
9. 開く、 **Cleansed and Matched Suppliers.xlsx**ファイルし、重複項目 (SupplierID) が表示されないことを確認します。  
  
 これで、仕入先データは重複項目を削除するためにクレンジングおよび照合されました。  
  
## <a name="next-step"></a>次の手順  
 [レッスン 4: MDS に仕入先データを格納する](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)  
  
  