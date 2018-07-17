---
title: グリッド (キューブ デザイナーのディメンションの使用法 タブ) (Analysis Services - 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ed63b1da-0fce-4f24-a722-5cff378831e8
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8e112b3cd1a732b403c7e2da2dde185e5e4c7df5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295832"
---
# <a name="grid-dimension-usage-tab-cube-designer-analysis-services---multidimensional-data"></a>[グリッド] (キューブ デザイナーの [ディメンションの使用法] タブ) (Analysis Services - 多次元データ)
  キューブ デザイナーの **[ディメンションの使用法]** タブの **[グリッド]** ペインを使用すると、キューブのディメンションとメジャー グループ間のディメンション リレーションシップを表示したり編集したりできます。 各ディメンションのリレーションシップは、グリッドにセルとして表されます。グリッドでは、メジャー グループは列として表示され、ディメンションは行として表示されます。  
  
## <a name="options"></a>および  
  
|オプション|定義|  
|------------|----------------|  
|**メジャー グループ**|メジャー グループを選択して、 **[グリッド]** ペインに列として表示します。 **[(すべて表示)]** を選択すると、利用可能なメジャー グループがすべて表示されます。<br /><br /> メジャー グループの名前を変更するには、メジャー グループの列ヘッダーを選択してクリックします。|  
|**Dimensions**|キューブ ディメンションを選択して、 **[グリッド]** ペインに行として表示します。 **[(すべて表示)]** を選択すると、利用可能なキューブ ディメンションがすべて表示されます。<br /><br /> キューブ ディメンションの名前を変更するには、ディメンションの行ヘッダーを選択してクリックします。|  
|**(セル)**|セルを選択して参照ボタン (**[...]**) をクリックし、 **[リレーションシップの定義]** ダイアログ ボックスを表示して、キューブ ディメンションとメジャー グループ間のディメンション リレーションシップを定義します。 **[リレーションシップの定義]** ダイアログ ボックスの詳細については、「[[リレーションシップの定義] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。|  
  
## <a name="context-menu"></a>コンテキスト メニュー  
 次に、 **[グリッド]** ペインを右クリックして表示されるショートカット メニューで、使用可能なオプションを示します。  
  
|オプション|定義|  
|------------|----------------|  
|**キューブ ディメンションを追加します。**|**[キューブ ディメンションの追加]** ダイアログ ボックスを表示し、既存または新しいデータベース ディメンションへの参照をキューブに追加します。 **[キューブ ディメンションの追加]** ダイアログ ボックスの詳細については、「[[キューブ ディメンションの追加] ダイアログ ボックス (Analysis Services - 多次元データ)](add-cube-dimension-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。|  
|**新しいリンク オブジェクト**|**リンク オブジェクト ウィザード** を表示して、メジャー グループやディメンションを他のキューブからリンクし、アクション、KPI、および計算を選択したキューブにインポートします。 **リンク オブジェクト ウィザード**の詳細については、「 [リンク オブジェクト ウィザードの F1 ヘルプ](linked-object-wizard-f1-help.md)」を参照してください。|  
|**切り取り**|注: このオプションは無効です。|  
|**[コピー]**|注: このオプションは無効です。|  
|**[貼り付け]**|注: このオプションは無効です。|  
|**削除**|選択したキューブ ディメンション、メジャー グループ、またはディメンションのリレーションシップをキューブから削除します。|  
|**Rename**|選択したキューブ ディメンション、メジャー グループ、またはディメンションのリレーションシップの名前を変更します。|  
|**Properties**|選択したキューブ ディメンション、メジャー グループ、またはディメンションのリレーションシップのプロパティを、 **の** [プロパティ] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ウィンドウに表示します。|  
  
## <a name="see-also"></a>参照  
 [キューブ オブジェクト&#40;Analysis Services - 多次元データ&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)   
 [多次元モデルのキューブ](multidimensional-models/cubes-in-multidimensional-models.md)   
 [ディメンションの使用法&#40;キューブ デザイナー&#41; &#40;Analysis Services - 多次元データ&#41;](dimension-usage-cube-designer-analysis-services-multidimensional-data.md)   
 [ツールバー&#40;ディメンションの使用法 タブ、キューブ デザイナー&#41; &#40;Analysis Services - 多次元データ&#41;](toolbar-dimension-usage-cube-designer-analysis-services-multidimensional-data.md)   
 [ディメンションの使用法&#40;キューブ デザイナー&#41; &#40;Analysis Services - 多次元データ&#41;](dimension-usage-cube-designer-analysis-services-multidimensional-data.md)  
  
  
