---
title: 'タスク 6: から値のインポート、Cleanse Supplier List プロジェクト |Microsoft ドキュメント'
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
ms.assetid: fec0deef-a729-4ff1-b709-72d2b3f407ac
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7a915013d779392d585bd5609384fab7bffd2800
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074090"
---
# <a name="task-6-importing-values-from-the-cleanse-supplier-list-project"></a>タスク 6: Cleanse Supplier List プロジェクトから値をインポートする
  ここでは、クレンジング プロセスで収集したデータ品質ナレッジをインポートします。 参照してください[クレンジング プロジェクトの値をドメインにインポートする](http://msdn.microsoft.com/library/hh479581.aspx)詳細についてはトピックです。 エクスポートすることも、ナレッジ ベースを DQS ファイルに、更新を発行する前に**Suppliers**サポート技術情報。  
  
1.  メイン ページで**DQS クライアント**をクリックして**右矢印** の横に**Suppliers** **最近使用したナレッジ ベース** をクリック**ドメイン管理**です。  
  
2.  をクリックして**Contact Email**に切り替えると、ドメインの一覧で、**ドメイン値**右ペインでタブです。  
  
3.  をクリックして**下向きの矢印** の横に、**値のインポート**アイコンをクリックして、ツールバーを**プロジェクト値のインポート**です。  
  
     ![プロジェクトのインポート ツール バー ボタンの値](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-01.jpg "プロジェクト値のツール バー ボタンのインポート")  
  
4.  **プロジェクト値のインポート**ダイアログ ボックスで、 **Cleanse Supplier List** [プロジェクト] とをクリックして**OK**です。  
  
5.  すべての電子メールが、インタラクティブなクレンジングで行った 2 つの修正と共にインポートされることに注意してください。 スクロールして 2 つの修正を確認します。  
  
    |値|次に修正|  
    |-----------|----------------|  
    |bobby0@adventure-work.com|bobby0@adventure-works.com|  
    |tad0@adventure-work.com|tad0@adventure-works.com|  
  
6.  プロジェクト値のインポートの前の手順を繰り返して、**国**ドメインと解決策として新しいエントリを追加することに注意してください**United State**に**アメリカ合衆国**(で '%s ')。  
  
    |値|次に修正|  
    |-----------|----------------|  
    |United State|United States|  
  
7.  古いドメイン値を表示するをオフに**新規のみ表示**チェック ボックスをオンします。  
  
8.  プロジェクト値のインポートの前の手順を繰り返して、 **Supplier Name**ドメイン。 インポート後は、既定で新しい値だけが表示されます。 すべての値を表示するをオフに**新規のみ表示**チェック ボックスをオンします。 情報を追加した、 **Suppliers**クレンジング アクティビティから学習した内容をナレッジ ベース。 ナレッジ ベースが充実するほど、クレンジング結果が向上します。  
  
    > [!NOTE]  
    >  複合ドメインの値をインポートすることはできません。  
  
9. をクリックして**ナレッジ ベースのエクスポート**アイコンをクリックしてツールバー**ナレッジ ベースのエクスポート**です。  
  
     ![ナレッジ ベース メニューのエクスポート](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-02.jpg " メニューのサポート技術情報のエクスポート")  
  
10. 型、Tutorial フォルダーに移動**Suppliers.dqs**の**ファイル名**、 をクリック**保存**です。 この DQS ファイルを使用して、これに基づく新しいナレッジ ベースを作成できます。  
  
11. をクリックして**OK**を閉じる、**ナレッジ ベースのエクスポート – Suppliers**メッセージ ボックスです。  
  
12. をクリックして**完了**アクティビティを終了します。  
  
13. **[パブリッシュ]** をクリックします。  
  
14. をクリックして**OK**メッセージ ボックスにします。  
  
## <a name="next-step"></a>次の手順  
 [レッスン 3: データを照合して仕入先の一覧から重複を削除する](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)  
  
  