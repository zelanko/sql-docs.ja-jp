---
title: キューブ ディメンションのプロパティの定義 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4401055a15afe73a1f33ee43354f7ee45f887a96
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022529"
---
# <a name="define-cube-dimension-properties"></a>キューブ ディメンションのプロパティの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  キューブ ディメンションは、キューブ内のデータベース ディメンションのインスタンスです。 1 つのデータベース ディメンションは複数のキューブで使用でき、複数のキューブ ディメンションが 1 つのデータベース ディメンションに基づくことができます。 次の表では、キューブ ディメンションのプロパティについて説明します。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**AllMemberAggregationUsage**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の集計デザイナーによって集計をデザインする方法を制御します。 このプロパティは、以下の値をとります。<br /><br /> **Full**: キューブの各集計に All メンバーが含まれている必要があります。<br /><br /> **None**: キューブの集計に All メンバーを含めることはできません。 これが既定値です。<br /><br /> **Unrestricted**: 集計デザイナーに制限が適用されません。<br /><br /> **Default**: Unrestricted と同じ機能です。|  
|**Description**|わかりやすいレベル名を指定します。|  
|**DimensionID**|データベース ディメンションの一意識別子 (ID) が格納されます。|  
|**HierarchyUniqueNameStyle**|キューブ ディメンションに含まれる階層に使用する一意の名前の生成方法を指定します。 このプロパティは、以下の値をとります。<br /><br /> **IncludeDimensionName**:<br />                    ディメンションの名前が、階層の名前の一部として含まれます。 これが既定値です。<br /><br /> **ExcludeDimensionName**:<br />                    ディメンションの名前が、階層の名前の一部として含まれません。|  
|**ID**|キューブ ディメンションの一意識別子が格納されます。|  
|**MemberUniqueNameStyle**|キューブ ディメンションに含まれる階層のメンバーに使用する一意の名前の生成方法を指定します。 このプロパティは、以下の値をとります。<br /><br /> **Native**:<br />                      [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって、メンバーの一意の名前が自動的に決定されます。 これが既定値です。<br /><br /> **NamePath**: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって、メンバーの各レベル名およびキャプションで構成される複合名が生成されます。|  
|**名前**|キューブ ディメンションの表示名が格納されます。 既定では、キューブ ディメンションの名前は、同じ名前の別のキューブ ディメンションがまだ定義されていない場合、データベース ディメンションの名前と同じです。|  
|**[表示]**|キューブ ディメンションを表示するかどうかを指定します。 既定値は **True**です。|  
  
## <a name="see-also"></a>参照  
 [ディメンションと #40 です。Analysis Services - 多次元データ & #41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
