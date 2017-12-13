---
title: "マイニング構造からマイニング モデルの削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 470e1d74434261b08c47f93c060c4ac4da143cb2
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>マイニング構造からのマイニング モデルの削除
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]使用してデータ マイニング デザイナーを使用してマイニング モデルを削除することができます[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または DMX ステートメントを使用します。  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a>SQL Server データ ツールを使用したマイニング モデルの削除  
  
1.  **の** [マイニング モデル] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブをクリックします。  
  
2.  削除するモデルを右クリックして、 **[削除]**をクリックします。  
  
     **[オブジェクトの削除]** ダイアログ ボックスが開きます。  
  
3.  **[OK]**をクリックします。  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a>SQL Server Management Studio を使用したマイニング モデルの削除  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、モデルが含まれる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを開きます。  
  
2.  **[マイニング構造]**を展開し、 **[マイニング モデル]**を展開します。  
  
3.  削除するモデルを右クリックして、 **[削除]**をクリックします。  
  
     モデルを削除してもトレーニング データは削除されず、モデルのトレーニング時に作成したメタデータとパターンのみ削除されます。  
  
### <a name="delete-a-mining-model-using-dmx"></a>DMX を使用したマイニング モデルの削除  
  
-   [DROP MINING MODEL &#40;DMX&#41;](../../dmx/drop-mining-model-dmx.md)  
  
## <a name="see-also"></a>参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
