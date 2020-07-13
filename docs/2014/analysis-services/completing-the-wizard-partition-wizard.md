---
title: '[ウィザードの完了] (パーティションウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.finish.f1
ms.assetid: 68a4dd5d-94d9-4a02-be31-949a6da0ef51
author: minewiskan
ms.author: owend
ms.openlocfilehash: 02de9a6840bfc4994eeb55f74905cc3eaec66bc5
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527348"
---
# <a name="completing-the-wizard-partition-wizard"></a>[ウィザードの完了] (パーティション ウィザード)
  **[ウィザードの完了]** ページを使用すると、パーティションの名前の設定とパーティションの集計のデザインを定義できます。必要であれば、パーティション ウィザードの完了後にパーティションを配置し、処理することもできます。  
  
## <a name="options"></a>Options  
 **名前**  
 新しいパーティションの名前を入力します。 複数のテーブルを使用する場合、プレフィックスを入力します。このプレフィックスとテーブル名を組み合わせて、各パーティションの名前が作成されます。  
  
 **[集計オプション]**  
 パーティションの集計オプションを指定します。  
  
 次の表に、選択できる集計オプションを示します。  
  
|オプション|説明|  
|------------|-----------------|  
|**[ここでパーティションの集計をデザインする]**|パーティション ウィザードで新しいパーティションを作成した後で、そのパーティションの集計をデザインします。 このオプションを選択した場合、パーティション ウィザードで **[完了]** をクリックすると集計のデザイン ウィザードが起動します。 集計のデザイン ウィザードの詳細については、「 [集計のデザイン ウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md)」を参照してください。|  
|**[後で集計をデザインする]**|ここでは集計をデザインせずに、パーティションを作成します。|  
|**[既存のパーティションから集計のデザインをコピーする]**|メジャー グループの既存のパーティションから新しいパーティションに、集計のデザインをコピーします。 このオプションをクリックすると、 **[コピー元]** オプションが有効になります。 **[コピー元]** オプションを使用して、集計のデザインのコピー元パーティションを選択します。<br /><br /> 将来マージされる可能性があるパーティションは、テーブル構造と集計デザインが同じであることに注意してください。 新しいパーティションをメジャー グループの既存のパーティションとマージする可能性がある場合、既存のパーティションから新しいパーティションに、集計のデザインをコピーしておきます。|  
  
 **[今すぐ配置して処理する]**  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]**** インスタンスにパーティションを配置し、処理します。 このページの **[完了]** をクリックすると、パーティションが配置されて処理されます。  
  
## <a name="see-also"></a>参照  
 [パーティション (Analysis Services - 多次元データ)](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
