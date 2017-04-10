---
title: "レッスン 13: Excel での分析 | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
caps.latest.revision: 22
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# レッスン 13: Excel での分析
このレッスンでは、[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で "Excel で分析" 機能を使用して Microsoft Excel を開き、モデル ワークスペースへのデータ ソース接続を自動的に作成して、ワークシートにピボットテーブルを自動的に追加します。 "Excel で分析" 機能を使用すると、モデルを配置する前に、モデル デザインの有効性をすばやく簡単にテストできます。 このレッスンでは、データの分析は行いません。 このレッスンの目的は、モデル作成者が、モデル デザインのテストに使用できるツールに慣れることです。 モデル作成者向けの "Excel で分析" 機能を使用する場合とは異なり、エンド ユーザーは Excel や [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] などのクライアント レポート アプリケーションを使用して、配置済みのモデル データへの接続と参照を行います。  
  
このレッスンを完了するには、[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] と同じコンピューター上に Excel がインストールされている必要があります。 詳細については、「[Excel で分析 (SSAS テーブル)](../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)」を参照してください。  
  
このレッスンの推定所要時間: **20 分**  
  
## 前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン「[レッスン 11: パーティションの作成](../analysis-services/lesson-11-create-partitions.md)」を完了している必要があります。  
  
## 既定のパースペクティブと Internet Sales パースペクティブを使用した参照  
ここでは、すべてのモデル オブジェクトを含む既定のパースペクティブと「レッスン 8: パースペクティブの作成」で作成した Internet Sales パースペクティブの両方を使用してモデルを参照します。 Internet Sales パースペクティブでは、Customer テーブル オブジェクトが除外されます。  
  
#### 既定のパースペクティブを使用して参照するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で、**[モデル]** メニューの **[Excel で分析]** をクリックします。  
  
2.  **[Excel で分析]** ダイアログ ボックスで、**[OK]** をクリックします。  
  
    Excel で新しいブックが開きます。 現在のユーザー アカウントを使用してデータ ソース接続が作成され、既定のパースペクティブを使用して表示可能なフィールドが定義されます。 ピボットテーブルがワークシートに自動的に追加されます。  
  
3.  Excel の **[ピボットテーブルのフィールドリスト]** に、**Date** メジャーと **Internet Sales** メジャー グループが表示され、**Customer**、**Date**、**Geography**、**Product**、**Product Category**、**Product Subcategory**、および **Internet Sales** の各テーブルとそれぞれの列もすべて表示されます。  
  
4.  ブックを保存せずに Excel を閉じます。  
  
#### Internet Sales パースペクティブを使用して参照するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で、**[モデル]** メニューの **[Excel で分析]** をクリックします。  
  
2.  **[Excel で分析]** ダイアログ ボックスの **[現在の Windows ユーザー]** を選択したままにして、**[パースペクティブ]** ドロップダウン リストで **[Internet Sales]** を選択し、**[OK]** をクリックします。 Excel が開きます。  
  
3.  Excel の **[ピボットテーブルのフィールドリスト]** で、フィールドリストから Customer テーブルが除外されます。  
  
4.  ブックを保存せずに Excel を閉じます。  
  
## ロールを使用した参照  
ロールはテーブル モデルに欠かせない要素です。 ユーザーがメンバーとして追加されているロールが少なくとも 1 つなければ、ユーザーはモデルを使用してデータにアクセスし、分析することができません。 "Excel で分析" 機能を利用して、定義したロールをテストすることができます。  
  
#### Internet Sales Manager ユーザー ロールを使用して参照するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で、**[モデル]** メニューの **[Excel で分析]** をクリックします。  
  
2.  **[Excel で分析]** ダイアログ ボックスの **[モデルへの接続に使用するユーザー名またはロールの指定]** で、**[ロール]** を選択します。次にドロップダウン リストで **[Internet Sales Manager]** を選択し、**[OK]** をクリックします。  
  
    Excel で新しいブックが開きます。 ピボット テーブルが自動的に作成されます。 [ピボット テーブル フィールド リスト] には、新しいモデルで使用できるすべてのデータ フィールドが表示されます。  
      
3.  ブックを保存せずに Excel を閉じます。  
  
## 次の手順  
このチュートリアルを続行するには、次のレッスン「[レッスン 14: 配置](../analysis-services/lesson-14-deploy.md)」に進んでください。  
  
  
  
