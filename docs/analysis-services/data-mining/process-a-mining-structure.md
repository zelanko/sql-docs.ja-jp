---
title: "マイニング構造の処理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マイニング構造 [Analysis Services], 処理"
ms.assetid: 4162f33e-c23f-4293-8905-271781e45fa4
caps.latest.revision: 31
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 31
---
# マイニング構造の処理
  マイニング構造に関連付けられているマイニング モデルを参照したり使用したりする前に、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置してマイニング構造とマイニング モデルを処理する必要があります。 また、マイニング構造またはマイニング モデルに変更を加えると、それらを再配置し、処理するように求められます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のデータ マイニング デザイナーの **[マイニング構造]** タブで構造を処理すると、関連するモデルもすべて処理されます。  
  
 マイニング構造は、次のツールを使用して処理できます。  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   XMLA: Process コマンド  
  
 個々のモデルを処理する方法の詳細については、「[マイニング モデルの処理](../../analysis-services/data-mining/process-a-mining-model.md)」を参照してください。  
  
### SQL Server データ ツールを使用してマイニング構造および関連するすべてのマイニング モデルを処理するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] の **[マイニング モデル]** メニュー項目から **[マイニング構造および全モデルの処理]** を選択します。  
  
     マイニング構造に変更を加えた場合は、マイニング モデルを処理する前にマイニング構造を再配置するよう求められます。 **[はい]**をクリックします。  
  
2.  **[マイニング構造の処理 - \<structure>]** ダイアログ ボックスで **[実行]** をクリックします。  
  
     **[処理の進行状況]** ダイアログ ボックスが開き、モデル処理の詳細が表示されます。  
  
3.  モデルの処理が完了したら、**[処理の進行状況]** ダイアログ ボックスの **[閉じる]** をクリックします。  
  
4.  **[マイニング構造の処理 - \<structure>]** ダイアログ ボックスで **[閉じる]** をクリックします。  
  
## 参照  
 [マイニング構造のタスクと操作方法](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  