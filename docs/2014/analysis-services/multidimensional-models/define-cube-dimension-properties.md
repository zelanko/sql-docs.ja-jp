---
title: キューブ ディメンションのプロパティの定義 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 9314e749-0918-4862-abaf-a21692188122
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bc40ef64b7b5e9b92d0e170d89ed388a90ff01c4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164677"
---
# <a name="define-cube-dimension-properties"></a>キューブ ディメンションのプロパティの定義
  キューブ ディメンションは、キューブ内のデータベース ディメンションのインスタンスです。 1 つのデータベース ディメンションは複数のキューブで使用でき、複数のキューブ ディメンションが 1 つのデータベース ディメンションに基づくことができます。 次の表では、キューブ ディメンションのプロパティについて説明します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`AllMemberAggregationUsage`|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の集計デザイナーによって集計をデザインする方法を制御します。 このプロパティは、以下の値をとります。<br /><br /> **Full**: キューブの各集計に All メンバーが含まれている必要があります。<br /><br /> **None**: キューブの集計に All メンバーを含めることはできません。 これが既定値です。<br /><br /> **Unrestricted**: 集計デザイナーに制限が適用されません。<br /><br /> **Default**: Unrestricted と同じ機能です。|  
|`Description`|わかりやすいレベル名を指定します。|  
|`DimensionID`|データベース ディメンションの一意識別子 (ID) が格納されます。|  
|`HierarchyUniqueNameStyle`|キューブ ディメンションに含まれる階層に使用する一意の名前の生成方法を指定します。 このプロパティは、以下の値をとります。<br /><br /> `IncludeDimensionName`: ディメンションの名前は、階層の名前の一部として含めるです。 これが既定値です。<br /><br /> `ExcludeDimensionName`: ディメンションの名前は、階層の名前の一部として含めるは。|  
|`ID`|キューブ ディメンションの一意識別子が格納されます。|  
|`MemberUniqueNameStyle`|キューブ ディメンションに含まれる階層のメンバーに使用する一意の名前の生成方法を指定します。 このプロパティは、以下の値をとります。<br /><br /> `Native`:[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]メンバーの一意の名前を自動的に決定します。 これが既定値です。<br /><br /> `NamePath`:[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の各レベルの名前とメンバーのキャプションで構成される複合名が生成されます。|  
|`Name`|キューブ ディメンションの表示名が格納されます。 既定では、キューブ ディメンションの名前は、同じ名前の別のキューブ ディメンションがまだ定義されていない場合、データベース ディメンションの名前と同じです。|  
|`Visible`|キューブ ディメンションを表示するかどうかを指定します。 既定値は `True` です。|  
  
## <a name="see-also"></a>参照  
 [ディメンション&#40;Analysis Services - 多次元データ&#41;](../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  