---
title: 'Analysis Services チュートリアル-レッスン 12: Excel で分析 |Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d215045f87ed780a4adc97f9ae4fed9ac7e6991a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38015997"
---
# <a name="analyze-in-excel"></a>[Excel で分析]

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは Microsoft Excel を開き、モデル ワークスペースへの接続を自動的に作成して、ワークシートにピボット テーブルを自動的に追加する Excel 機能で分析を使用します。 "Excel で分析" 機能を使用すると、モデルを配置する前に、モデル デザインの有効性をすばやく簡単にテストできます。 このレッスンでは、データの分析を実行しません。 このレッスンの目的は、モデル作成者が、モデル デザインのテストに使用できるツールに慣れることです。   
  
このレッスンを完了するには、Visual Studio と同じコンピューターに Excel をインストールする必要があります。
  
このレッスンの推定所要時間: **5 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事では、順序で完了する必要があります、表形式モデルのチュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 11: ロールを作成](../tutorial-tabular-1400/as-lesson-11-create-roles.md)です。  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>既定のパースペクティブと Internet Sales パースペクティブを使用した参照  

これらの最初のタスクでモデルを参照するとも両方既定のパースペクティブを含むすべてのモデル オブジェクトを使用して、Internet Sales パースペクティブを使用して、前にします。 Internet Sales パースペクティブでは、Customer テーブル オブジェクトが除外されます。  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>既定のパースペクティブを使用して参照するには  
  
1.  をクリックして、**モデル**メニュー > **Excel で分析**します。  
  
2.  **[Excel で分析]** ダイアログ ボックスで、 **[OK]** をクリックします。  
  
    Excel は、新しいブックを開きます。 現在のユーザー アカウントを使用してデータ ソース接続が作成され、既定のパースペクティブを使用して表示可能なフィールドが定義されます。 ピボット テーブルがワークシートに自動的に追加されます。  
  
3.  Excel で、**ピボット テーブル フィールド リスト**に注意してください、 **DimDate**と**FactInternetSales**メジャー グループに表示されます。 **DimCustomer**、 **DimDate**、 **DimGeography**、 **DimProduct**、 **DimProductCategory**、**DimProductSubcategory**、および**FactInternetSales**も、それぞれの列のテーブルが表示されます。  
  
4.  ブックを保存せずに Excel を閉じます。  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>Internet Sales パースペクティブを使用して参照するには  
  
1.  をクリックして、**モデル** メニューをクリック**Excel で分析**します。  
  
2.  **[Excel で分析]** ダイアログ ボックスの **[現在の Windows ユーザー]** を選択したままにして、 **[パースペクティブ]** ドロップダウン リストで **[Internet Sales]** を選択し、 **[OK]** をクリックします。 
    
    ![as-lesson12-perspective](../tutorial-tabular-1400/media/as-lesson12-perspective.png)
    
3.  Excel で**ピボット テーブル フィールド**フィールドの一覧から DimCustomer テーブルが除外されます。  
    
    ![lesson12-フィールドとして](../tutorial-tabular-1400/media/as-lesson12-fields.png)
    
4.  ブックを保存せずに Excel を閉じます。  
  
## <a name="browse-by-using-roles"></a>ロールを使用して参照します。  

ロールは、任意の表形式モデルの重要な部分です。 少なくとも 1 つのロールにメンバーとしてユーザーを追加することがなくユーザーがアクセスし、モデルを使用してデータを分析することはできません。 "Excel で分析" 機能を利用して、定義したロールをテストすることができます。  
  
#### <a name="to-browse-by-using-the-sales-manager-user-role"></a>Sales Manager ユーザー ロールを使用して参照するには  
  
1.  SSDT で、**モデル** メニューをクリック**Excel で分析**します。  
  
2.  **ユーザー名またはモデルへの接続に使用するロールを指定**を選択します**ロール**、し、ドロップダウン リスト ボックスに、次のように選択します**営業マネージャー**、をクリックして **。OK**します。  
  
    Excel は、新しいブックを開きます。 ピボット テーブルが自動的に作成されます。 ピボット テーブル フィールド リストには、新しいモデルで使用できるすべてのデータ フィールドが含まれています。  
      
3.  ブックを保存せずに Excel を閉じます。  
  
## <a name="whats-next"></a>次の操作

次のレッスンに移動:[レッスン 13: デプロイ](../tutorial-tabular-1400/as-lesson-13-deploy.md)します。

  
  
  
