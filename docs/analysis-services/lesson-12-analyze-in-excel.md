---
title: "レッスン 13: Excel で分析 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4c3fa27228e03c076eeb3800b21c34397b4c9834
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-12-analyze-in-excel"></a>レッスン 12: Excel で分析
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは SSDT での Excel 機能で、分析を使用して、Microsoft Excel を開き、モデル ワークスペースを開き、データ ソース接続を自動的に作成し、ワークシートにピボット テーブルを自動的に追加します。 "Excel で分析" 機能を使用すると、モデルを配置する前に、モデル デザインの有効性をすばやく簡単にテストできます。 このレッスンでは、データの分析は行いません。 このレッスンの目的は、モデル作成者が、モデル デザインのテストに使用できるツールに慣れることです。 Excel の機能は、モデル作成者向けでの分析の使用とは異なりエンドユーザーがクライアント レポート アプリケーションの配置済みモデル データの Excel または Power BI に接続しを参照するように使用されます。  
  
このレッスンを完了するのには、SSDT と同じコンピューターに Excel をインストールする必要があります。 詳細については、「 [[Excel で分析]](../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)と同じコンピューター上に Excel がインストールされている必要があります。  
  
このレッスンの推定所要時間: **20 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 11: ロールの作成](../analysis-services/lesson-11-create-roles.md)です。  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>既定のパースペクティブと Internet Sales パースペクティブを使用した参照  
これらの最初のタスクは、参照、モデル パースペクティブを使用して両方の既定値、すべてのモデル オブジェクトが含まれており、および Internet Sales パースペクティブを使用しても前にします。 Internet Sales パースペクティブでは、Customer テーブル オブジェクトが除外されます。  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>既定のパースペクティブを使用して参照するには  
  
1.  クリックして、**モデル**メニュー > **Excel で分析**です。  
  
2.  **[Excel で分析]** ダイアログ ボックスで、 **[OK]**をクリックします。  
  
    Excel で新しいブックが開きます。 現在のユーザー アカウントを使用してデータ ソース接続が作成され、既定のパースペクティブを使用して表示可能なフィールドが定義されます。 ピボット テーブルがワークシートに自動的に追加されます。  
  
3.  Excel で、**ピボット テーブル フィールド リスト**に注意してください、 **DimDate**と**FactInternetSales**メジャー グループが表示されるだけでなく**DimCustomer**、 **DimDate**、 **DimGeography**、 **DimProduct**、 **DimProductCategory**、 **DimProductSubcategory**、および**FactInternetSales**すべて、それぞれの列のテーブルが表示されます。  
  
4.  ブックを保存せずに Excel を閉じます。  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>Internet Sales パースペクティブを使用して参照するには  
  
1.  クリックして、**モデル** メニューをクリックして**Excel で分析**です。  
  
2.  **[Excel で分析]** ダイアログ ボックスの **[現在の Windows ユーザー]** を選択したままにして、 **[パースペクティブ]** ドロップダウン リストで **[Internet Sales]**を選択し、 **[OK]**をクリックします。 
    
    ![としてのテーブルの lesson12 の観点から見た](../analysis-services/media/as-tabular-lesson12-perspective.png)
    
3.  Excel で**ピボット テーブル フィールド**、DimCustomer テーブルがフィールドの一覧から除外されることを確認します。  
    
    ![として表形式の lesson12-フィールド](../analysis-services/media/as-tabular-lesson12-fields.png)
    
4.  ブックを保存せずに Excel を閉じます。  
  
## <a name="browse-by-using-roles"></a>ロールを使用して参照します。  
ロールはテーブル モデルに欠かせない要素です。 ユーザーがメンバーとして追加するには、少なくとも 1 つのロール、なしと、ユーザーはアクセスして、モデルを使用してデータを分析することができません。 "Excel で分析" 機能を利用して、定義したロールをテストすることができます。  
  
#### <a name="to-browse-by-using-the-sales-manager-user-role"></a>Sales Manager ユーザー ロールを使用して、参照  
  
1.  SSDT をクリックして、**モデル** メニューをクリックして**Excel で分析**です。  
  
2.  **Excel で分析**ダイアログ ボックスで、**ユーザー名またはモデルへの接続に使用するロールを指定****ロール**、し、ドロップダウン リスト ボックスで  **営業マネージャー**、クリックして**OK**です。  
  
    Excel で新しいブックが開きます。 ピボット テーブルが自動的に作成します。 [ピボット テーブル フィールド リスト] には、新しいモデルで使用できるすべてのデータ フィールドが表示されます。  
      
3.  ブックを保存せずに Excel を閉じます。  
  
## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 13: 展開](../analysis-services/lesson-13-deploy.md)です。

  
  
  

