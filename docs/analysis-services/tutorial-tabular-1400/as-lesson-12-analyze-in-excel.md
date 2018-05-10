---
title: 'Analysis Services のチュートリアル レッスン 12: Excel で分析 |Microsoft ドキュメント'
description: Analysis Services tutorial プロジェクトで、Excel で分析を使用する方法について説明します。
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: ''
author: Minewiskan
manager: kfile
editor: ''
tags: ''
ms.assetid: ''
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 6e6c4ed1eb92a629a8916bd1eae455b82914ae0c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="analyze-in-excel"></a>[Excel で分析]

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでを Microsoft Excel を開き、モデル ワークスペースへの接続を自動的に作成し、ワークシートにピボット テーブルを自動的に追加 excel で分析を使用します。 "Excel で分析" 機能を使用すると、モデルを配置する前に、モデル デザインの有効性をすばやく簡単にテストできます。 このレッスンでは、データの分析を実行しません。 このレッスンの目的は、モデル作成者が、モデル デザインのテストに使用できるツールに慣れることです。   
  
このレッスンを完了するには、Visual Studio と同じコンピューターに Excel をインストールする必要があります。
  
このレッスンの推定所要時間: **5 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事は、順番に従って実行する必要がありますが、テーブル モデリング チュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 11: ロールの作成](../tutorial-tabular-1400/as-lesson-11-create-roles.md)です。  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>既定のパースペクティブと Internet Sales パースペクティブを使用した参照  

これらの最初のタスクでモデルを参照する、パースペクティブを使用して両方の既定値、すべてのモデル オブジェクトが含まれており、および Internet Sales パースペクティブを使用しても前にします。 Internet Sales パースペクティブでは、Customer テーブル オブジェクトが除外されます。  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>既定のパースペクティブを使用して参照するには  
  
1.  クリックして、**モデル**メニュー > **Excel で分析**です。  
  
2.  **[Excel で分析]** ダイアログ ボックスで、 **[OK]** をクリックします。  
  
    Excel は、新しいブックが開きます。 現在のユーザー アカウントを使用してデータ ソース接続が作成され、既定のパースペクティブを使用して表示可能なフィールドが定義されます。 ピボット テーブルがワークシートに自動的に追加されます。  
  
3.  Excel で、**ピボット テーブル フィールド リスト**に注意してください、 **DimDate**と**FactInternetSales**メジャー グループが表示されます。 **DimCustomer**、 **DimDate**、 **DimGeography**、 **DimProduct**、 **DimProductCategory**、 **DimProductSubcategory**、および**FactInternetSales**も、それぞれの列を持つテーブルが表示されます。  
  
4.  ブックを保存せずに Excel を閉じます。  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>Internet Sales パースペクティブを使用して参照するには  
  
1.  クリックして、**モデル** メニューをクリックして**Excel で分析**です。  
  
2.  **[Excel で分析]** ダイアログ ボックスの **[現在の Windows ユーザー]** を選択したままにして、 **[パースペクティブ]** ドロップダウン リストで **[Internet Sales]** を選択し、 **[OK]** をクリックします。 
    
    ![as-lesson12-perspective](../tutorial-tabular-1400/media/as-lesson12-perspective.png)
    
3.  Excel で**ピボット テーブル フィールド**、DimCustomer テーブルがフィールドの一覧から除外されることを確認します。  
    
    ![lesson12-フィールドとして](../tutorial-tabular-1400/media/as-lesson12-fields.png)
    
4.  ブックを保存せずに Excel を閉じます。  
  
## <a name="browse-by-using-roles"></a>ロールを使用して参照します。  

ロールは、表形式モデルの重要な部分です。 メンバーとしてユーザーを追加するには、少なくとも 1 つのロール、なしユーザーがアクセスし、モデルを使用してデータを分析できません。 "Excel で分析" 機能を利用して、定義したロールをテストすることができます。  
  
#### <a name="to-browse-by-using-the-sales-manager-user-role"></a>Sales Manager ユーザー ロールを使用して、参照  
  
1.  SSDT をクリックして、**モデル** メニューをクリックして**Excel で分析**です。  
  
2.  **ユーザー名またはモデルへの接続に使用するロールを指定**を選択**ロール**、ドロップダウン リスト ボックスで、次のように選択します。**営業マネージャー**、順にクリック**OK**です。  
  
    Excel は、新しいブックが開きます。 ピボット テーブルが自動的に作成します。 ピボット テーブル フィールド リストには、新しいモデルで使用可能なすべてのデータ フィールドが含まれています。  
      
3.  ブックを保存せずに Excel を閉じます。  
  
## <a name="whats-next"></a>次の操作

次のレッスンに移動:[レッスン 13: 展開](../tutorial-tabular-1400/as-lesson-13-deploy.md)です。

  
  
  
