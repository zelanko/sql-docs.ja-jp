---
title: "マイニング モデルの処理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "処理のマイニング モデル [Analysis Services]"
ms.assetid: c2204472-c500-47a5-9afa-7ce2ca78b233
caps.latest.revision: 32
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 32
---
# マイニング モデルの処理
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のデータ マイニング デザイナーにある [マイニング モデル] タブを使用すると、特定のマイニング モデル構造に関連するマイニング モデルを処理したり、その構造に関連するすべてのモデルを処理したりできます。  
  
 マイニング モデルは、次のツールを使用して処理できます。  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
 XMLA 処理コマンドを使用することもできます。 詳細については、「[処理するためのツールと方法 (Analysis Services)](../../analysis-services/multidimensional-models/tools-and-approaches-for-processing-analysis-services.md)」を参照してください。  
  
### SQL Server データ ツールを使用した単一のマイニング モデルの処理  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブで、グリッドにある 1 つまたは複数のモデル列からマイニング モデルを 1 つ選択します。  
  
2.  **[マイニング モデル]** メニューの **[モデルの処理]** をクリックします。  
  
     マイニング構造に変更を加えた場合は、モデルを処理する前に構造を再配置するように求められます。 **[はい]**をクリックします。  
  
3.  **[マイニング モデルの処理 - \<model>]** ダイアログ ボックスで **[実行]** をクリックします。  
  
     **[処理の進行状況]** ダイアログ ボックスが開き、モデル処理の詳細が表示されます。  
  
4.  モデルの処理が問題なく終了したら、**[処理の進行状況]** ダイアログ ボックスで **[閉じる]** をクリックします。  
  
5.  **[マイニング モデルの処理 - \<model>]** ダイアログ ボックスで **[閉じる]** をクリックします。  
  
 そのマイニング構造と選択したマイニング モデルのみが処理されます。  
  
### マイニング構造に関連するすべてのマイニング モデルの処理  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブにある **[マイニング モデル]** メニューで **[マイニング構造および全モデルの処理]** をクリックします。  
  
2.  マイニング構造に変更を加えた場合は、モデルを処理する前に構造を再配置するように求められます。 **[はい]**をクリックします。  
  
3.  **[マイニング構造の処理 - \<structure>]** ダイアログ ボックスで **[実行]** をクリックします。  
  
4.  **[処理の進行状況]** ダイアログ ボックスが開き、モデル処理の詳細が表示されます。  
  
5.  モデルの処理が問題なく終了したら、**[処理の進行状況]** ダイアログ ボックスで **[閉じる]** をクリックします。  
  
6.  **[\<model> を処理しています]** ダイアログ ボックスで **[閉じる]** をクリックします。  
  
 マイニング構造および関連するすべてのマイニング モデルが処理されます。  
  
## 参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  