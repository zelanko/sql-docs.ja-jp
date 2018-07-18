---
title: 'レッスン 13: Excel で分析 |Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a59a91b86da12dc9df4b9d3ce2b65ef456439627
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37971674"
---
# <a name="lesson-12-analyze-in-excel"></a>レッスン 12: Excel で分析します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは SSDT での Excel 機能で分析を使用して、Microsoft Excel を開き、モデル ワークスペースへのデータ ソース接続を自動的に作成し、ワークシートにピボット テーブルを自動的に追加します。 "Excel で分析" 機能を使用すると、モデルを配置する前に、モデル デザインの有効性をすばやく簡単にテストできます。 このレッスンでは、データの分析は行いません。 このレッスンの目的は、モデル作成者が、モデル デザインのテストに使用できるツールに慣れることです。 In Excel 機能は、モデル作成者向けのものが、分析を使用するとは異なりエンドユーザーはクライアント アプリケーションをデプロイされたモデル データを Excel または Power BI に接続し、参照するようにレポートを使用します。  
  
このレッスンを完了するには ､ SSDT と同じコンピューターに Excel をインストールする必要があります。 詳細については、「 [[Excel で分析]](../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)と同じコンピューター上に Excel がインストールされている必要があります。  
  
このレッスンの推定所要時間: **20 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 11: ロールの作成](../analysis-services/lesson-11-create-roles.md)です。  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>既定のパースペクティブと Internet Sales パースペクティブを使用した参照  
これらの最初のタスクの両方、既定のパースペクティブを含むすべてのモデル オブジェクトを使用して、Internet Sales パースペクティブを使用しても、モデルを参照は前述しました。 Internet Sales パースペクティブでは、Customer テーブル オブジェクトが除外されます。  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>既定のパースペクティブを使用して参照するには  
  
1.  をクリックして、**モデル**メニュー > **Excel で分析**します。  
  
2.  **[Excel で分析]** ダイアログ ボックスで、 **[OK]** をクリックします。  
  
    Excel で新しいブックが開きます。 現在のユーザー アカウントを使用してデータ ソース接続が作成され、既定のパースペクティブを使用して表示可能なフィールドが定義されます。 ピボット テーブルがワークシートに自動的に追加されます。  
  
3.  Excel で、**ピボット テーブル フィールド リスト**に注意してください、 **DimDate**と**FactInternetSales**メジャー グループが表示されるだけでなく**DimCustomer**、 **DimDate**、 **DimGeography**、 **DimProduct**、 **DimProductCategory**、 **DimProductSubcategory**、および**FactInternetSales**それぞれの列のすべてのテーブルが表示されます。  
  
4.  ブックを保存せずに Excel を閉じます。  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>Internet Sales パースペクティブを使用して参照するには  
  
1.  をクリックして、**モデル** メニューをクリック**Excel で分析**します。  
  
2.  **[Excel で分析]** ダイアログ ボックスの **[現在の Windows ユーザー]** を選択したままにして、 **[パースペクティブ]** ドロップダウン リストで **[Internet Sales]** を選択し、 **[OK]** をクリックします。 
    
    ![として-テーブル-lesson12-パースペクティブ](../analysis-services/media/as-tabular-lesson12-perspective.png)
    
3.  Excel で**ピボット テーブル フィールド**フィールドの一覧から DimCustomer テーブルが除外されます。  
    
    ![として表形式の lesson12-フィールド](../analysis-services/media/as-tabular-lesson12-fields.png)
    
4.  ブックを保存せずに Excel を閉じます。  
  
## <a name="browse-by-using-roles"></a>ロールを使用して参照します。  
ロールはテーブル モデルに欠かせない要素です。 少なくとも 1 つのロールにメンバーとしてユーザーを追加することがなくユーザーはアクセスして、モデルを使用してデータを分析することができません。 "Excel で分析" 機能を利用して、定義したロールをテストすることができます。  
  
#### <a name="to-browse-by-using-the-sales-manager-user-role"></a>Sales Manager ユーザー ロールを使用して参照するには  
  
1.  SSDT で、**モデル** メニューをクリック**Excel で分析**します。  
  
2.  **Excel で分析** ダイアログ ボックスで**ユーザー名またはモデルへの接続に使用するロールを指定**を選択します**ロール**、し、ドロップダウン リスト ボックスに、 **営業マネージャー**、 をクリックし、 **OK**します。  
  
    Excel で新しいブックが開きます。 ピボット テーブルが自動的に作成されます。 [ピボット テーブル フィールド リスト] には、新しいモデルで使用できるすべてのデータ フィールドが表示されます。  
      
3.  ブックを保存せずに Excel を閉じます。  
  
## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 13: デプロイ](../analysis-services/lesson-13-deploy.md)します。

  
  
  
