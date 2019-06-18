---
title: 属性リレーションシップの定義 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e49207e99887e13cdd5321821e7325b4a2dac7dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62717849"
---
# <a name="attribute-relationships---define"></a>属性リレーションシップ - 定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、属性はディメンションの基本的な要素です。 ディメンションには、属性リレーションシップに基づいて構成される一連の属性が含まれます。  
  
 ディメンションに含まれるテーブルごとに、テーブルのキー属性をそのテーブルの別の属性に関連付ける属性リレーションシップがあります。 このリレーションシップは、ディメンションの作成時に作成します。  
  
 属性リレーションシップには、次の利点があります。  
  
-   ディメンション処理に必要なメモリの量が減少します。 これにより、ディメンション、パーティション、およびクエリの処理速度が上がります。  
  
-   ストレージへのアクセスが高速になり、実行プランがより適切に最適化されるため、クエリ パフォーマンスが向上します。  
  
-   ユーザー定義階層がリレーションシップのパスに沿って定義されている場合、集計デザイン アルゴリズムによってより効果的な集計が選択されます。  
  
  
## <a name="attribute-relationship-considerations"></a>属性リレーションシップに関する注意点  
 基になるデータで属性リレーションシップがサポートされる場合、属性間で一意の属性リレーションシップを定義することも必要です。 一意の属性リレーションシップを定義するには、ディメンション デザイナーの **[属性リレーションシップ]** タブを使用します。  
  
 基になるリレーションシップがある属性には、その関連属性を基準とした一意なキーが必要です。 つまり、基になる属性のメンバーによって、関連属性のメンバーが 1 つだけ識別される必要があります。 たとえば、市区町村 -> 都道府県のリレーションシップを考えてみます。 このリレーションシップでは、基になる属性が市区町村、関連属性が都道府県です。 基になる属性は、「多」側と多対一リレーションシップの「一」側が関連します。 基になる属性のキーは、市区町村 + 都道府県です。 詳細については、「 [属性リレーションシップの作成、変更、または削除](../../analysis-services/multidimensional-models/attribute-relationships-create-modify-or-delete-relationship.md)」を参照してください。  
  
 属性リレーションシップのプロパティの詳細については、「 [属性リレーションシップのプロパティの構成](../../analysis-services/multidimensional-models/attribute-relationships-configure-attribute-properties.md)」を参照してください。  
  
> [!NOTE]  
>  属性リレーションシップを正しく定義しないと、クエリ結果が無効になる場合があります。  
  
## <a name="see-also"></a>参照  
 [のディメンション デザイナーの](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
