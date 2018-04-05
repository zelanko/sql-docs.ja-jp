---
title: マイニング モデルの処理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mining models [Analysis Services], processing
ms.assetid: c2204472-c500-47a5-9afa-7ce2ca78b233
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3152bfff58d0e5163c3ef3635ebee59a9258bd07
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="process-a-mining-model"></a>マイニング モデルの処理
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]データ マイニング デザイナーでのマイニング モデル タブで[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、マイニング構造に関連付けられている特定のマイニング モデルを処理することができますか、または構造に関連付けられているすべてのモデルを処理することができます。  
  
 マイニング モデルは、次のツールを使用して処理できます。  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
 XMLA 処理コマンドを使用することもできます。 詳細については、「[処理するためのツールと方法 (Analysis Services)](../../analysis-services/multidimensional-models/tools-and-approaches-for-processing-analysis-services.md)」を参照してください。  
  
### <a name="process-a-single-mining-model-using-sql-server-data-tools"></a>SQL Server データ ツールを使用した単一のマイニング モデルの処理  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブで、グリッドにある 1 つまたは複数のモデル列からマイニング モデルを 1 つ選択します。  
  
2.  **[マイニング モデル]** メニューの **[モデルの処理]**をクリックします。  
  
     マイニング構造に変更を加えた場合は、モデルを処理する前に構造を再配置するように求められます。 **[はい]**をクリックします。  
  
3.  **マイニング モデルの処理 -\<モデル >**ダイアログ ボックスで、をクリックして**実行**です。  
  
     **[処理の進行状況]** ダイアログ ボックスが開き、モデル処理の詳細が表示されます。  
  
4.  モデルの処理が問題なく終了したら、 **[処理の進行状況]** ダイアログ ボックスで **[閉じる]** をクリックします。  
  
5.  をクリックして**閉じる**で、**マイニング モデルの処理 -\<モデル >**  ダイアログ ボックス。  
  
 そのマイニング構造と選択したマイニング モデルのみが処理されます。  
  
### <a name="process-all-mining-models-that-are-associated-with-a-mining-structure"></a>マイニング構造に関連するすべてのマイニング モデルの処理  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブにある **[マイニング モデル]** メニューで **[マイニング構造および全モデルの処理]** をクリックします。  
  
2.  マイニング構造に変更を加えた場合は、モデルを処理する前に構造を再配置するように求められます。 **[はい]**をクリックします。  
  
3.  **マイニング構造の処理 -\<構造 >**ダイアログ ボックスで、をクリックして**実行**です。  
  
4.  **[処理の進行状況]** ダイアログ ボックスが開き、モデル処理の詳細が表示されます。  
  
5.  モデルの処理が問題なく終了したら、 **[処理の進行状況]** ダイアログ ボックスで **[閉じる]** をクリックします。  
  
6.  をクリックして**閉じる**で、**処理\<モデル >**  ダイアログ ボックス。  
  
 マイニング構造および関連するすべてのマイニング モデルが処理されます。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
