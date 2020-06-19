---
title: ワークスペースデータベースのパーティションの処理 (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3a369705-43fa-4961-9045-32e06fbdde33
author: minewiskan
ms.author: owend
ms.openlocfilehash: 947f4bdbb6dae0e371c9df50b202986c62f0644e
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938753"
---
# <a name="process-partitions-in-the-workspace-database-ssas-tabular"></a>ワークスペースデータベースのパーティションの処理 (SSAS テーブル)
  パーティションは、テーブルを論理的な部分に分割します。 各パーティションは、他のパーティションとは個別に処理 (更新) できます。 このトピックのタスクでは、 **で** [パーティションの処理] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ダイアログ ボックスを使用して、モデル ワークスペース データベースでパーティションを処理する方法について説明します。  
  
 別の Analysis Services インスタンスにモデルが配置された後、データベース管理者は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用するか、スクリプトによって、または IS パッケージを使用して (配置済みの) モデルでパーティションを作成し管理できます。 詳細については、「[テーブル モデル パーティションの作成および管理 (SSAS テーブル)](partitions-ssas-tabular.md)」を参照してください。  
  
###  <a name="to-process-a-partition"></a><a name="bkmk_create_new"></a> パーティションを処理するには  
  
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
 [SSAS 表形式のパーティション &#40;&#41;](partitions-ssas-tabular.md)   
 [ワークスペース データベースのパーティションの作成と管理 (SSAS テーブル)](workspace-database-ssas-tabular.md)  
  
  
