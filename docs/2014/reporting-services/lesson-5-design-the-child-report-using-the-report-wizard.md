---
title: レッスン 5:レポート ウィザードを使用して子レポートの設計 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 19a3f927-ea97-4f40-a5f8-cd5f2598e4da
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: bc993c0881eb4aeeddb18c8df0efad69dbba261e
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52418353"
---
# <a name="lesson-5-design-the-child-report-using-the-report-wizard"></a>レッスン 5:レポート ウィザードを使用して、子レポートをデザインします。
  子レポートのデータ接続とデータ テーブルを作成した後は、レポート デザイナーのレポート ウィザードを使用して子レポートを設計します。 レポート デザイナーの詳細については、「[レポート デザイナーを使用してレポートをデザインする &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)」を参照してください。  
  
### <a name="to-design-the-child-report-using-the-report-wizard"></a>レポート ウィザードを使用して子レポートを設計するには  
  
1.  **ソリューション エクスプローラー**でトップレベル Web サイトが選択されていることを確認します。  
  
2.  Web サイトを右クリックし、 **[新しい項目の追加]** を選択します。  
  
3.  **新しい項目の追加**ダイアログ ボックスで、をクリックして**レポート ウィザード**、レポート ファイルの名前を入力し、**追加**します。  
  
     これにより、レポート ウィザードが起動します。  
  
4.  **データセットのプロパティ**ページで、**データ ソース**ボックスで、 **DataSet2**します。  
  
     作成した DataTable で **[使用できるデータセット]** ボックスが自動的に更新されます。  
  
5.  **[次へ]** をクリックします。  
  
6.  **[フィールドの配置]** ページで、次の操作を行います。  
  
    1.  **[ProductID]**、 **[PurchaseOrderID]**、 **[PurchaseOrderDetailID]**、 **[OrderQty]**、 **[ReceivedQty]**、 **[RejectedQty]**、および **[StockedQty]** を、 **[使用できるフィールド]** から **[値]** ボックスにドラッグします。  
  
    2.  矢印をクリックして**Sum(ProductID)**、 **Sum(PurchaseOrderID)**、 **Sum(PurchaseOrderDetailID)**、 **Sum(OrderQty)**、 **Sum(ReceivedQty)**、 **Sum(RejectedQty)**、および**Sum(StockedQty)** をオフにし、**合計**選択します。  
  
7.  をクリックして **[次へ]** 2 回クリックして**完了**を閉じる、**レポート ウィザード**します。  
  
     これで .rdlc ファイルが作成されました。 このファイルはレポート デザイナーで開くことができます。 設計した Tablix がデザイン画面に表示されます。  
  
8.  .rdlc ファイルが開かれた状態で、次の手順を実行してパラメーターを追加します。  
  
    1.  をクリックして**パラメーター**で、**レポート データ**ペイン、およびクリック**パラメーターを追加して**。  
  
    2.  **[名前]** ボックスに **productid** を入力します。  
  
    3.  **[データ型]** リスト ボックスで **[整数]** が選択されていることを確認します。  
  
    4.  **[OK]** をクリックします。  
  
9. .rdlc ファイルを保存します。  
  
## <a name="next-task"></a>次の作業  
 これで、レポート ウィザードを使用して子レポートを設計できました。 次は、Web サイト アプリケーションに ReportViewer コントロールを追加します。  
  
  
