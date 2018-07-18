---
title: 'タスク 5: クレンジングの結果を Excel ファイルをエクスポートする |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3cc3e51ee8b07ad017e6bf33150ec83e30ec4ff8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155533"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a>タスク 5: Excel ファイルにクレンジングの結果をエクスポートする
  ここでは、クレンジング アクティビティから Excel ファイルに結果をエクスポートします。 参照してください[エクスポート ステージ](http://msdn.microsoft.com/library/hh213061.aspx#Export)詳細についてはトピック。  
  
1.  右側のウィンドウで次のように選択します。 **Excel**の、**変換先の型**します。  
  
2.  をクリックして**参照**、として出力ファイル名を指定**Cleansed Supplier List.xls**、順にクリックします**オープン**します。  
  
3.  選択**データのみ**の**出力**クレンジングされたデータのみをエクスポートする形式。 2 番目のオプションでは、**データとクレンジング情報**、クレンジングされたデータと共にクレンジング アクティビティの詳細をエクスポートすることができます。 **標準化形式**オプションを使用して、そのドメインの値のドメインで定義する出力形式を適用できます。 チュートリアルのドメインには、出力形式を定義していません。  
  
     ![エクスポートのクレンジング結果ページ](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "エクスポート クレンジングの結果 ページ")  
  
4.  クリックして**エクスポート**にデータをエクスポートします。 クリックしてしないでください**完了**まだします。  
  
5.  クリックして**閉じる**上、**エクスポート** ダイアログ ボックス。  
  
6.  クリックして**完了**してアクティビティを終了します。 クリックする前に結果をエクスポートすることを忘れた場合**完了**、 をクリックして**データ品質プロジェクトを開く**のメイン ページで**DQS クライアント**を選択します**Cleanse Supplierリスト**プロジェクト、およびクリックの一覧から**次**を取得するには、画面の下部にある、**エクスポート**クレンジング プロセスをもう一度のステージ。 切り替えることもできます**管理し、結果を表示する** タブをクリックして**戻る**ボタンをクリックします。  
  
7.  開く、 **Cleansed Supplier List.xls**次の操作を行います。  
  
    1.  ワークシートで adventure-work.com を検索して、末尾が adventure-work.com (文字 's' が抜けている) の電子メール アドレスがないことを確認します。  
  
    2.  あることを確認しない**USA**値、**国**列。  
  
    3.  検索**Los Angeles**ことを確認し、**状態**に設定されている**CA**します。  
  
    4.  条件がないことを確認します。 **co.**、 **Corp.**、と**Inc.** します。  
  
    5.  削除、 **Address Validation**列、スプレッドシートから、excel ファイルを保存します。 この追加列は Address Validation 複合ドメインに対応します。  
  
## <a name="next-step"></a>次の手順  
 [タスク 6: Cleanse Supplier List プロジェクトから値をインポートする](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  
