---
title: Analysis Services ワークスペース データベースでパーティションの処理 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6f81d61411ef8815d23407b9aee1df4cf56e70de
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072149"
---
# <a name="process-partitions-in-the-workspace-databse"></a>ワークスペース データベースでパーティションの処理 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  パーティションは、テーブルを論理的な部分に分割します。 各パーティションは、他のパーティションとは個別に処理 (更新) できます。 このトピックのタスクでは、 **で** [パーティションの処理] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ダイアログ ボックスを使用して、モデル ワークスペース データベースでパーティションを処理する方法について説明します。  
  
 別の Analysis Services インスタンスにモデルが配置された後、データベース管理者は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用するか、スクリプトによって、または IS パッケージを使用して (配置済みの) モデルでパーティションを作成し管理できます。 詳細については、次を参照してください。[の作成とテーブル モデル パーティションの管理](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)します。  
  
###  <a name="bkmk_create_new"></a> パーティションを処理するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[モデル]** メニューをクリックし、 **[処理]** ([更新])、 **[パーティションの処理]** の順にクリックします。  
  
2.  **[モード]** ボックスの一覧で、次のプロセス モードのいずれかを選択します。  
  
    |モード|説明|  
    |----------|-----------------|  
    |**既定の処理**|パーティション オブジェクトの処理状態を検出して、未処理または部分的に処理されたパーティション オブジェクトを完全に処理された状態にするために必要な処理を実行します。 空のテーブルとパーティションのデータが読み込まれ、階層、計算列、およびリレーションシップが構築または再構築されます。|  
    |**完全処理**|パーティション オブジェクトとそこに含まれているすべてのオブジェクトを処理します。 既に処理されたオブジェクトに対して完全処理を実行すると、そのオブジェクト内のすべてのデータが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって削除されてから、オブジェクトが処理されます。 この種の処理は、構造上の変更をオブジェクトに加えた場合に必要となります。|  
    |**データの処理**|階層またはリレーションシップを再構築したり、計算列とメジャーを再計算したりせずに、パーティションまたはテーブルにデータを読み込みます。|  
    |**消去の処理**|パーティションからすべてのデータを削除します。|  
    |**追加の処理**|パーティションを新しいデータで増分更新します。|  
  
3.  **[処理]** チェックボックス列で、選択したモードで処理するパーティションを選択し、 **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [パーティション](../../analysis-services/tabular-models/partitions-ssas-tabular.md)   
 [ワークスペース データベースのパーティションの作成と管理](../../analysis-services/tabular-models/create-and-manage-partitions-in-the-workspace-database-ssas-tabular.md)  
  
  
