---
title: マイニング モデルの処理 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2bfc8d22ff87f467fa89d178d46b422918aa4dd6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="process-a-mining-model"></a>マイニング モデルの処理
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のデータ マイニング デザイナーにある [マイニング モデル] タブを使用すると、特定のマイニング モデル構造に関連するマイニング モデルを処理したり、その構造に関連するすべてのモデルを処理したりできます。  
  
 マイニング モデルは、次のツールを使用して処理できます。  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
 XMLA 処理コマンドを使用することもできます。 詳細については、「[処理するためのツールと方法 (Analysis Services)](../../analysis-services/multidimensional-models/tools-and-approaches-for-processing-analysis-services.md)」を参照してください。  
  
### <a name="process-a-single-mining-model-using-sql-server-data-tools"></a>SQL Server データ ツールを使用した単一のマイニング モデルの処理  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブで、グリッドにある 1 つまたは複数のモデル列からマイニング モデルを 1 つ選択します。  
  
2.  **[マイニング モデル]** メニューの **[モデルの処理]** をクリックします。  
  
     マイニング構造に変更を加えた場合は、モデルを処理する前に構造を再配置するように求められます。 **[はい]** をクリックします。  
  
3.  **マイニング モデルの処理 -\<モデル >** ダイアログ ボックスで、をクリックして**実行**です。  
  
     **[処理の進行状況]** ダイアログ ボックスが開き、モデル処理の詳細が表示されます。  
  
4.  モデルの処理が問題なく終了したら、**[処理の進行状況]** ダイアログ ボックスで **[閉じる]** をクリックします。  
  
5.  をクリックして**閉じる**で、**マイニング モデルの処理 -\<モデル >**  ダイアログ ボックス。  
  
 そのマイニング構造と選択したマイニング モデルのみが処理されます。  
  
### <a name="process-all-mining-models-that-are-associated-with-a-mining-structure"></a>マイニング構造に関連するすべてのマイニング モデルの処理  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブにある **[マイニング モデル]** メニューで **[マイニング構造および全モデルの処理]** をクリックします。  
  
2.  マイニング構造に変更を加えた場合は、モデルを処理する前に構造を再配置するように求められます。 **[はい]** をクリックします。  
  
3.  **マイニング構造の処理 -\<構造 >** ダイアログ ボックスで、をクリックして**実行**です。  
  
4.  **[処理の進行状況]** ダイアログ ボックスが開き、モデル処理の詳細が表示されます。  
  
5.  モデルの処理が問題なく終了したら、**[処理の進行状況]** ダイアログ ボックスで **[閉じる]** をクリックします。  
  
6.  をクリックして**閉じる**で、**処理\<モデル >**  ダイアログ ボックス。  
  
 マイニング構造および関連するすべてのマイニング モデルが処理されます。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
