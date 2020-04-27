---
title: 'レッスン 3: レポート ウィザードを使用して親レポートを設計する | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 282c5753b0e1e966d1041944e936d341ed46a30f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108480"
---
# <a name="lesson-3-design-the-parent-report-using-the-report-wizard"></a>レッスン 3: レポート ウィザードを使用して親レポートを設計する
  親レポートのデータ接続とデータ テーブルを作成した後は、レポート デザイナーのレポート ウィザードを使用して親レポートを設計します。 レポート デザイナーの詳細については、「[レポート デザイナーを使用してレポートをデザインする &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)」を参照してください。  
  
### <a name="to-design-the-parent-report-using-the-report-wizard"></a>レポート ウィザードを使用して親レポートを設計するには  
  
1.  **ソリューション エクスプローラー**でトップレベル Web サイトが選択されていることを確認します。  
  
2.  Web サイトを右クリックし、 **[新しい項目の追加]** を選択します。  
  
3.  [**新しい項目の追加**] ダイアログボックスで [**レポートウィザード**] を選択し、レポートファイルの名前を入力して、[**追加**] をクリックします。  
  
     これにより、レポート ウィザードが起動します。  
  
4.  **[データセットのプロパティ]** ページの **[データ ソース]** ボックスで、「 **レッスン 2: 親レポートのデータ接続とデータ テーブルを定義する** 」で作成した [DataSet1](lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)を選択します。  
    上の手順で作成した **DataTable** で **[使用できるデータセット]** ボックスが自動的に更新されます。  
  
5.  **[次へ]** をクリックします。  
  
6.  **[フィールドの配置]** ページで、次の操作を行います。  
  
    1.  **[ProductID]** 、 **[Name]** 、 **[ProductNumber]** 、 **[SafetyStockLevel]** 、および **[ReorderLevel]** を、 **[使用できるフィールド]** から **&gt;[値]** ボックスにドラッグします。  
  
    2.  **Sum (ProductID)**、 **sum (saf**)、sum **(ReorderLevel)** の横にある矢印をクリックし、**合計**の選択を解除します。  
  
7.  [**次へ**] を2回クリックし、[**完了**] をクリックして**レポートウィザード**を閉じます。  
  
     これで .rdlc ファイルが作成されました。 このファイルはレポート デザイナーで開くことができます。 設計した Tablix がデザイン画面に表示されます。  
  
8.  .rdlc ファイルを保存します。  
  
## <a name="next-task"></a>次の作業  
 これで、レポート ウィザードを使用して親レポートを設計できました。 次は、子レポートのデータ接続とデータ テーブルを作成します。  
  
  
