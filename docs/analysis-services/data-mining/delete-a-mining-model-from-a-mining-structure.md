---
title: マイニング構造からマイニング モデルの削除 |Microsoft ドキュメント
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 38d544972849b8de847467f5fa964f34fed3cd57
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>マイニング構造からのマイニング モデルの削除
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ マイニング デザイナー、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または DMX ステートメントを使用すると、マイニング モデルを削除することができます。  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a>SQL Server データ ツールを使用したマイニング モデルの削除  
  
1.  **の** [マイニング モデル] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブをクリックします。  
  
2.  削除するモデルを右クリックして、 **[削除]** をクリックします。  
  
     **[オブジェクトの削除]** ダイアログ ボックスが開きます。  
  
3.  **[OK]** をクリックします。  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a>SQL Server Management Studio を使用したマイニング モデルの削除  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、モデルが含まれる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを開きます。  
  
2.  **[マイニング構造]** を展開し、 **[マイニング モデル]** を展開します。  
  
3.  削除するモデルを右クリックして、 **[削除]** をクリックします。  
  
     モデルを削除してもトレーニング データは削除されず、モデルのトレーニング時に作成したメタデータとパターンのみ削除されます。  
  
### <a name="delete-a-mining-model-using-dmx"></a>DMX を使用したマイニング モデルの削除  
  
-   [マイニング モデルの削除 (&) #40";"DMX"&"#41;](../../dmx/drop-mining-model-dmx.md)  
  
## <a name="see-also"></a>参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
