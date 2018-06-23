---
title: 'タスク 5: クレンジングの結果を Excel ファイルにエクスポートする |Microsoft ドキュメント'
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
ms.topic: article
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f8a716d3b6c0007ceb89f36f23584bb4adb4f706
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072006"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a>タスク 5: Excel ファイルにクレンジングの結果をエクスポートする
  ここでは、クレンジング アクティビティから Excel ファイルに結果をエクスポートします。 参照してください[エクスポート ステージ](http://msdn.microsoft.com/library/hh213061.aspx#Export)詳細についてはトピックです。  
  
1.  右側のペインで選択**Excel**の**変換先の型**です。  
  
2.  をクリックして**参照**、として出力ファイル名を指定**Cleansed Supplier List.xls**、順にクリック**開く**です。  
  
3.  選択**データのみ**の**出力**クレンジングされたデータのみをエクスポートする形式。 2 番目のオプションでは、**データとクレンジング情報**、クレンジングされたデータと共にクレンジング アクティビティの詳細をエクスポートすることができます。 **標準化形式**オプションでは、そのドメインの値のドメインで定義する出力形式を適用することができます。 チュートリアルのドメインには、出力形式を定義していません。  
  
     ![エクスポートのクレンジングの結果 ページ](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "エクスポート クレンジングの結果 ページ")  
  
4.  をクリックして**エクスポート**にデータをエクスポートします。 クリックしてしないでください**完了**まだです。  
  
5.  をクリックして**閉じる**上、**エクスポート** ダイアログ ボックス。  
  
6.  をクリックして**完了**アクティビティを終了します。 クリックする前に結果のエクスポートを忘れた場合**完了**、] をクリックして**データ品質プロジェクトを開く**のメイン ページで**DQS クライアント**[ **Cleanse Supplierリスト**プロジェクト、およびクリックの一覧から**次**を表示する画面の下部にある、**エクスポート**クレンジング プロセスをもう一度のステージ。 切り替えることも**管理と結果を表示する** タブをクリックして**戻る**ボタンをクリックします。  
  
7.  開く、 **Cleansed Supplier List.xls**し、次の操作を行います。  
  
    1.  ワークシートで adventure-work.com を検索して、末尾が adventure-work.com (文字 's' が抜けている) の電子メール アドレスがないことを確認します。  
  
    2.  あることを確認なし**USA**値で、**国**列です。  
  
    3.  検索**Los Angeles**ことを確認し、**状態**に設定されている**CA**です。  
  
    4.  条件がないことを確認**co.**、 **Corp.**、および**Inc.** です。  
  
    5.  削除、 **Address Validation**列のスプレッドシートから excel ファイルを保存します。 この追加列は Address Validation 複合ドメインに対応します。  
  
## <a name="next-step"></a>次の手順  
 [タスク 6: Cleanse Supplier List プロジェクトから値をインポートする](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  